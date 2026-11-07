# UI craft checklist (20 checks)

Used by the `landing-page-design` skill (build rules while building, scoring before ship). Link here, do not copy the list into other files.

## How to use

- **While building:** treat every check as a build rule. Do not wait for review.
- **While reviewing:** score each check Pass, Fail or N/A. Report Fails only, as a table: Check, Evidence (file, line, screenshot, selector), Fix. Count N/A checks, do not hide them.
- **Severity:** a Fail on 5, 10, 15 or 16 is P0 (it breaks the page). A Fail on 6, 7, 9 or 19 is P1. Everything else is P2. Say so in the table.
- **Static images:** checks 15, 17, 19 and 20 are visual-only from a screenshot. Tag them "verify live".

## The 20

### Content: say less, say it specifically
| # | Check | Pass when | How to test |
| :-- | :-- | :-- | :-- |
| 1 | Delete filler badges | No pill, tag or badge exists only to decorate ("New", "Featured", "Featured" repeated). One badge max per screen, and only if it carries information. | List every badge. Remove it. If nothing is lost, it was filler. |
| 2 | Drop redundant labels | No label restates what the content already says (a "Problem" label above text that opens with the problem, column headers over self-evident columns, figure captions repeating the heading). | Read the label and the content together. If the label adds nothing, cut it. |
| 9 | Make headlines specific | Every headline contains a fact, number, action or named outcome. "Cut onboarding from 4 hours to 15 minutes" passes. "Strategy that delivers" fails. | Swap the headline into a competitor's page. If it still works, it is generic. |
| 13 | Remove embellishments | Every decorative element earns its place (gradients, glows, dividers, ornaments, background art). One signature graphic at most. | Delete each decoration. If the page reads the same or better, leave it deleted. |
| 3 | Unitalicize random words | Italics appear only for titles, terms or true emphasis, never as a styling accent on a random word in a headline. | Search for `<em>`, `<i>`, `font-style: italic`. Justify each hit. |

### Type and system: one rule, applied everywhere
| # | Check | Pass when | How to test |
| :-- | :-- | :-- | :-- |
| 4 | Mono only where needed | Monospace appears only for code, commands, file names or tabular data. Not for labels, eyebrows or decoration. | Search for the mono font family. Every hit must be code-like content. |
| 5 | Use a design system | Colors, type scale, spacing and radii come from named tokens (CSS variables, mapped to your component library). No one-off hex values or magic numbers in components. A short design tokens doc exists. | Grep for raw hex and px outside `:root`. |
| 14 | Inner radius = outer radius minus padding | Any rounded container holding a rounded child follows inner = outer - padding (24 outer, 12 padding, 12 inner). | Inspect each nested pair. Compute it. |
| 16 | Wrap headlines properly | No orphans or widows in headlines, no single-word last lines, no breaks that split a number from its unit. Use `text-wrap: balance`, and check 375, 768 and 1440. | Screenshot all three widths. Read each headline's line breaks. |
| 17 | Align by eye, not pixels | Large type, icons and buttons are optically aligned (side bearing on big type nudged, icons centered on the text's x-height, not the box). | Squint at the left edge of the page. Anything that looks off is off. |
| 18 | Use tabular nums | Stats, prices, tables and counters use `font-variant-numeric: tabular-nums` so digits do not jump. | Search stat and price selectors. |

### Hierarchy: one thing first
| # | Check | Pass when | How to test |
| :-- | :-- | :-- | :-- |
| 6 | Show the actual product | The work is shown as it is (real screenshot, or a faithful native rebuild in the palette). No stock art, no generic AI illustration standing in for the thing. | Ask "what is being sold?" and look for it on screen. |
| 7 | Enlarge the main feature | The main feature is visibly the largest and strongest block on the page. | Blur the page. The main feature must still win. |
| 8 | Group with spacing | Related items sit closer than unrelated items (use the spacing scale). Dividers and borders are the fallback, not the default. | Remove all borders mentally. Groups must still read. |
| 10 | Emphasize the CTA | One filled primary action per view, high contrast, label names the outcome ("Start the free trial"). Everything else is a text link. | Count filled buttons per viewport. More than one is a Fail. |
| 11 | Add an accent colour | One accent, used sparingly for action and one highlight per screen. Never for large fills unless it is the CTA band. | Count accent uses per screen. |

### Craft: consistent and readable
| # | Check | Pass when | How to test |
| :-- | :-- | :-- | :-- |
| 12 | Keep icons consistent | One icon set, one grid, one stroke weight, one corner style. No emoji or text glyphs (arrows, plus signs) mixed in. | Line up every icon. They must look drawn by one hand. |
| 15 | Improve text contrast | Normal text 4.5:1 or better, large text 3:1 or better, on every background it appears on. Compute each pairing. Small text (under 14px) is a Fail on its own. | Compute ratios with the WCAG formula. Never eyeball. |

### States and motion: feedback, not decoration
| # | Check | Pass when | How to test |
| :-- | :-- | :-- | :-- |
| 19 | Add loading states | Anything that loads or processes shows a state: image skeletons, button spinners, step progress. No blank flashes. | Throttle the network. Watch what the page does. |
| 20 | Animate useful feedback | Motion tells the user something happened: press, hover, step complete, content arrived. All of it respects `prefers-reduced-motion`. No ambient animation. | Press, hover and trigger every control. Turn reduced motion on. |

## Accepted exceptions

A Fail can be accepted only with a reason written next to it (for example, "mono labels kept because this is a terminal mock"). Unexplained exceptions count as Fails.
