# BillingOS Documentation Plan

## Context

BillingOS needs developer documentation so users can integrate billing into their apps. The docs will be hosted via Mintlify (repo at `/Users/ankushkumar/Code/docs/`, currently has default starter kit content). The goal: a developer should go from zero to accepting payments in under 5 minutes. Written for both non-technical and technical audiences, SDK-focused with API reference as secondary.

---

## Navigation Structure (4 Tabs)

```
GUIDES                          REACT SDK                    NODE SDK               API REFERENCE
├─ Get Started                  ├─ Overview                  ├─ Server SDK          ├─ Overview
│  ├─ Introduction              │  ├─ overview               │  ├─ overview          │  ├─ introduction
│  ├─ Quickstart (5 min)        │  ├─ installation           │  ├─ session-tokens    │  ├─ authentication
│  ├─ How It Works              │  └─ provider               │  ├─ customers         │  └─ errors
│  └─ Session Tokens            ├─ Components                │  ├─ subscriptions     ├─ Checkout
├─ Accept Payments              │  ├─ pricing-table          │  ├─ entitlements      │  ├─ create
│  ├─ Show a Pricing Page       │  ├─ checkout-modal         │  └─ usage             │  ├─ status
│  └─ Accept a Payment          │  ├─ customer-portal        │                       │  └─ confirm
├─ Manage Billing               │  ├─ feature-gate           │                       ├─ Products
│  ├─ Manage Subscriptions      │  ├─ usage-display          │                       │  └─ list
│  ├─ Gate Features             │  ├─ upgrade-nudge          │                       ├─ Features
│  ├─ Track Usage               │  └─ upgrade-prompt         │                       │  ├─ check
│  └─ Upgrade Nudges            ├─ Hooks                     │                       │  ├─ entitlements
└─ Production                   │  ├─ use-subscription       │                       │  ├─ track-usage
   ├─ Handle Webhooks           │  ├─ use-checkout           │                       │  └─ usage-metrics
   └─ Go Live Checklist         │  ├─ use-feature            │                       ├─ Portal
                                │  ├─ use-entitlements       │                       │  ├─ create/status/data
                                │  ├─ use-track-usage        │                       └─ Subscriptions
                                │  └─ use-products           │                          ├─ cancel
                                └─ Client                    │                          └─ reactivate
                                   └─ client (class ref)     │
```

---

## File Structure

```
/Users/ankushkumar/Code/docs/
├── docs.json                          # Rewrite: BillingOS branding + 4-tab nav
├── index.mdx                          # Rewrite: BillingOS landing page
├── quickstart.mdx                     # Rewrite: 5-step zero-to-checkout
├── guides/
│   ├── how-it-works.mdx               # Architecture overview (non-technical friendly)
│   ├── session-tokens.mdx             # Auth explained
│   ├── show-a-pricing-page.mdx        # PricingTable guide
│   ├── accept-a-payment.mdx           # Checkout walkthrough
│   ├── manage-subscriptions.mdx       # CustomerPortal guide
│   ├── gate-features.mdx              # FeatureGate + entitlements
│   ├── track-usage.mdx                # Usage metering
│   ├── upgrade-nudges.mdx             # UpgradeNudge guide
│   ├── handle-webhooks.mdx            # Webhook handling
│   └── go-live-checklist.mdx          # Sandbox → production
├── sdk/
│   ├── overview.mdx                   # React SDK overview
│   ├── installation.mdx               # Install + peer deps
│   ├── provider.mdx                   # BillingOSProvider reference
│   ├── components/
│   │   ├── pricing-table.mdx
│   │   ├── checkout-modal.mdx
│   │   ├── customer-portal.mdx
│   │   ├── feature-gate.mdx
│   │   ├── usage-display.mdx
│   │   ├── upgrade-nudge.mdx
│   │   └── upgrade-prompt.mdx
│   ├── hooks/
│   │   ├── use-subscription.mdx
│   │   ├── use-checkout.mdx
│   │   ├── use-feature.mdx
│   │   ├── use-entitlements.mdx
│   │   ├── use-track-usage.mdx
│   │   └── use-products.mdx
│   └── client.mdx                     # BillingOSClient class reference
├── server-sdk/
│   ├── overview.mdx
│   ├── session-tokens.mdx
│   ├── customers.mdx
│   ├── subscriptions.mdx
│   ├── entitlements.mdx
│   └── usage.mdx
├── api-reference/
│   ├── introduction.mdx
│   ├── authentication.mdx
│   ├── errors.mdx
│   ├── checkout/  (create, status, confirm)
│   ├── products/  (list)
│   ├── features/  (check, entitlements, track-usage, usage-metrics)
│   ├── portal/    (create, status, data)
│   └── subscriptions/ (cancel, reactivate)
├── snippets/
│   ├── session-token-endpoint.mdx     # Reusable: Next.js API route code
│   └── provider-setup.mdx             # Reusable: Provider wrapper code
└── images/                            # Screenshots (add as available)
```

**Files to delete** (default Mintlify starter content):
- `essentials/` directory (all files)
- `api-reference/endpoint/` directory + `openapi.json`
- `ai-tools/` directory
- `development.mdx`

---

## Implementation Phases

### Phase 1: Core Flow (8 pages) — Ship first
The minimum viable docs to let someone accept payments.

1. **`docs.json`** — Rewrite with BillingOS branding, 4-tab nav structure
2. **`index.mdx`** — Landing: "Add billing to your app in 5 minutes"
3. **`quickstart.mdx`** — 5 steps: install SDK → create session endpoint → wrap with Provider → add PricingTable → run and test
4. **`guides/how-it-works.mdx`** — Non-technical architecture overview
5. **`guides/session-tokens.mdx`** — Session token auth explained
6. **`guides/show-a-pricing-page.mdx`** — PricingTable guide
7. **`guides/accept-a-payment.mdx`** — Checkout walkthrough
8. **`sdk/installation.mdx`** — Install instructions
9. **`sdk/provider.mdx`** — BillingOSProvider setup

### Phase 2: SDK Component References (7 pages)
10-16. All component pages under `sdk/components/`

### Phase 3: Hooks + Client Reference (7 pages)
17-23. All hook pages under `sdk/hooks/` + `sdk/client.mdx`

### Phase 4: Remaining Guides (5 pages)
24-28. manage-subscriptions, gate-features, track-usage, upgrade-nudges, go-live-checklist

### Phase 5: Server SDK (6 pages)
29-34. All pages under `server-sdk/`

### Phase 6: API Reference (14 pages)
35-48. Introduction, auth, errors + all endpoint pages

---

## Key Content Decisions

- **Quickstart is self-contained**: All 5 steps on one page, no external links needed, includes test card number `4242 4242 4242 4242`
- **Session tokens explained early**: Biggest friction point — server must create tokens, so this needs dedicated explanation right after quickstart
- **Goal-oriented guide titles**: "Accept a Payment" not "Checkout API", "Gate Features" not "Entitlements Reference"
- **Sandbox noted as "coming soon"**: Go-live checklist explains using Stripe test keys, notes sandbox environment is on roadmap
- **Reusable snippets**: Session token endpoint code and Provider setup appear in multiple pages via Mintlify's snippet import system
- **No dashboard docs**: SDK/API focus only per requirement

## Source Files to Reference

| Doc Page | Source of Truth |
|----------|----------------|
| Provider props | `/Users/ankushkumar/Code/billingos-sdk/src/providers/BillingOSProvider.tsx` |
| Client methods | `/Users/ankushkumar/Code/billingos-sdk/src/client/index.ts` |
| Component props | `/Users/ankushkumar/Code/billingos-sdk/src/components/` |
| Hook signatures | `/Users/ankushkumar/Code/billingos-sdk/src/hooks/` |
| Node SDK methods | `/Users/ankushkumar/Code/billingos-sdk/packages/node/src/client/billingos.ts` |
| Session token example | `/Users/ankushkumar/Code/billingos-testprojects/my-app/src/app/api/billingos-session/route.ts` |
| API endpoints | `/Users/ankushkumar/Code/billingos-bare/billingos-docs/apps/api/src/v1/` |
| Sandbox plan | `/Users/ankushkumar/Code/billingos-bare/billingos-docs/docs/sandbox/plan.md` |

## Verification

1. Run `npx mintlify dev` in `/Users/ankushkumar/Code/docs/` — all pages should render without errors
2. Click through every sidebar link — no broken pages
3. Code examples should be copy-pasteable (verify imports, package names match actual SDK)
4. Quickstart flow should be completable by reading only that one page
5. Run `npx mintlify broken-links` to check for dead links
