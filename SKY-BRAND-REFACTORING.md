# Sky Brand Portal - Refactoring Summary

## Overview
This repository has been refactored from Sage brand identity to **Sky brand identity**, including fonts, colors, design tokens, and UI components.

---

## Changes Implemented

### 1. **Fonts**
- **Removed**: Sage fonts (Sage Headline, Sage Text, Sage UI Icons)
- **Removed**: Sky Script fonts (initial implementation, replaced)
- **Added**: Sky Text fonts (TTF format)
  - `SkyText-Light.ttf` (Light - weight: 300)
  - `SkyText-Regular.ttf` (Regular - weight: 400)
  - `SkyText-Medium.ttf` (Medium - weight: 500)
  - `SkyText-Italic.ttf` (Italic style)
- **Updated**: `styles/fonts.css` with Sky Text font-face declarations
- **Fallback**: Roboto fonts retained as fallback

### 2. **Color Scheme**
Transitioned from **dark theme** (Sage green on black) to **light theme** (Sky gradient on white).

#### Sky Brand Colors
```css
/* Sky White Backgrounds */
--background-color: #fafafd
--background-color-secondary: #f4f6fc
--background-color-card: #fff

/* Sky Spectrum Gradient */
--sky-orange: #ff7800
--sky-red: #f80032
--sky-magenta: #ff00a0
--sky-purple: #8c28ff
--sky-blue: #0023ff
--sky-light-blue: #1798ff

/* Text Colors */
--text-color: #1a1a1a (dark text on light bg)
--text-color-muted: #666
--text-color-light: #fff (for dark surfaces)

/* Accent */
--link-color: #0023ff
--accent-color: #0023ff
```

#### Gradients
```css
--sky-gradient: linear-gradient(90deg, #ff7800 0%, #f80032 20%, #ff00a0 40%, #8c28ff 60%, #0023ff 80%, #1798ff 100%)
```

### 3. **Navigation Architecture**
Complete navigation redesign to match Sky brand portal structure.

#### **New: Sidebar Navigation** (`blocks/sidebar-nav/`)
- **Dark left sidebar** (290px wide, collapses to 80px)
- **Logo/Branding**: "sky creative portal" at top
- **Collapse button**: "← Collapse" with arrow icon, state saved in localStorage
- **Hierarchical menu** with expandable sections
- **Icons**: Rocket icon (🚀) for "Brand Portal" items
- **User profile**: At bottom with avatar, name ("Gaetano Polizzi"), and online status
- **Category headers** and nested submenus
- **Mobile toggle button** for drawer functionality
- **Active state** indicators with Sky blue accent
- **Sky White gradient** background element (subtle overlay)
- Desktop: Fixed, always visible
- Mobile: Toggle drawer

**Features**:
- Smooth collapse animation
- Auto-expand parent menus for active pages
- Submenu toggle buttons
- Custom scrollbar styling
- Click-outside-to-close on mobile

#### **Updated: Header** (`blocks/header/`)
Complete redesign with **three-row layout**:

1. **Top row** (48px):
   - Left: "Version 114.2.0" text
   - Right: Sky Creative logo (pink #d81159 background) + "Sky Global" dropdown

2. **Second row** (Brand title):
   - "Sky Brand Portal" (18px, semi-bold, regular font style)
   - Extracted from navigation fragment

3. **Third row** (Breadcrumb):
   - Horizontal breadcrumb navigation
   - Separator: `|`
   - Active page highlighted

**Features**:
- **Sky gradient bar** (4px) at very top
- Light background with borders
- Sticky header with shadow
- All text set to `font-style: normal` (no italic)
- Dropdown button: bold, black text

### 4. **Block Updates**
All blocks updated for Sky brand:

#### **Hero** (`blocks/hero/`)
- Light background with subtle gradient
- Increased padding for prominence
- Optional `.gradient` variant with Sky spectrum
- Text shadow on gradient backgrounds

#### **Hero Carousel** (`blocks/hero-carousel/`)
- Light card backgrounds
- Box shadow for elevation
- Updated dot navigation colors
- Maintained auto-rotation functionality

#### **Cards** (`blocks/cards/`)
- Light card backgrounds
- Border color updates
- Hover effects with transform and shadow
- Border radius maintained

#### **Asset Cards** (`blocks/asset-cards/`)
- Light backgrounds
- Sky blue accent on hover
- Label pill styling updated
- Box shadows added

#### **Quick Links** (`blocks/quick-links/`)
- Pill-shaped buttons
- Sky blue hover states
- White text on accent background

#### **Search** (`blocks/search/`)
- Light card background
- Border with focus state
- Sky blue accent button
- Maintained search bar layout

#### **Footer** (`blocks/footer/`)
- Light background
- Border top separator
- Already compatible with light theme

### 5. **Design Tokens** (`styles/styles.css`)
- Updated all CSS custom properties
- Light theme as default
- Button colors updated (white text on accent)
- Icon filter changed for dark icons on light bg
- Added gradient button variant
- Maintained border radius and transitions
- Font family: 'Sky Text' with roboto fallback

### 6. **Additional Assets**
- **Sky White Gradient**: `icons/sky-white-gradient.png` - Used as subtle background in sidebar

---

## File Structure

```
/fonts/
  ├── SkyText-Light.ttf       (NEW)
  ├── SkyText-Regular.ttf     (NEW)
  ├── SkyText-Medium.ttf      (NEW)
  ├── SkyText-Italic.ttf      (NEW)
  ├── roboto-*.woff2          (KEPT)
  └── Sage_*.woff2            (REMOVED)

/blocks/
  ├── sidebar-nav/            (NEW)
  │   ├── sidebar-nav.js      - Menu toggle, collapse, active states
  │   ├── sidebar-nav.css     - Dark theme, hierarchical styling
  │   └── _sidebar-nav.json   - Universal Editor config
  ├── header/                 (COMPLETELY REDESIGNED)
  │   ├── header.js           - Three-row layout logic
  │   └── header.css          - Gradient bar, version, breadcrumb
  ├── hero/                   (UPDATED)
  ├── hero-carousel/          (UPDATED)
  ├── cards/                  (UPDATED)
  ├── asset-cards/            (UPDATED)
  ├── quick-links/            (UPDATED)
  ├── search/                 (UPDATED)
  └── footer/                 (UPDATED)

/icons/
  └── sky-white-gradient.png  (NEW)

/styles/
  ├── styles.css              (UPDATED - Sky Text font family)
  ├── fonts.css               (UPDATED - Sky Text declarations)
  └── lazy-styles.css         (unchanged)

/NAVIGATION-GUIDE.md          (NEW - Complete navigation management guide)
/SKY-BRAND-REFACTORING.md     (THIS FILE)
```

---

## Development

### Local Development Server
```bash
aem up
# Server runs at http://localhost:3000
```

### Linting
```bash
npm run lint          # Check all
npm run lint:fix      # Auto-fix
```

### Build
```bash
npm run build:json    # Merge component models
```

---

## Brand Guidelines Reference

### Sky Brand Assets Used
- **Fonts**: Sky Text from `SkyMasterbrand_AssetPack/4_FONTS/Sky_Text/`
  - SKYTEXT-REGULAR.TTF
  - SKYTEXT-MEDIUM.TTF
  - SKYTEXT-LIGHT.TTF
  - SKYTEXT-ITALIC.TTF
- **Colors**: Sky Spectrum Gradient and Sky White
- **Typography Guidelines**: `MASTER_BRAND_TYPOGRAPHY_RGB.pdf`
- **Gradient Assets**: `Sky_Master_Brand_One-to-One_RGB.png`
- **Logo**: `Sky_Master_Brand_Logo_LARGE_RGB.svg`

### Design Principles
- **Light & Bright**: White/light backgrounds (Sky White)
- **Vibrant Accents**: Sky gradient spectrum (orange→pink→purple→blue)
- **Clean Typography**: Sky Text for all text (with proper regular/italic variants)
- **Modern UI**: Rounded corners, soft shadows, smooth transitions
- **Accessible**: High contrast, readable font sizes
- **Consistent Branding**: Logo, colors, and fonts match brand guidelines exactly

---

## Next Steps for Authoring

### 1. Create Content in AEM
- Set up navigation structure in DA (https://da.live/#/aemsites/koassets)
- Create sidebar navigation fragment at `/sidebar-nav`
- Create breadcrumb navigation fragment at `/nav`
- Populate content for Home and Sky Brand Portal pages

### 2. Sidebar Navigation Structure
Example hierarchy (in AEM `/sidebar-nav` fragment):
```
| Navigation |
|------------|

| Home | / |

| **Brand Portal** |
| Sky Brand (new) | /sky-brand |

| **Masterbrand** |
| Tone of Voice | /masterbrand/tone-of-voice |
| Iconography | /masterbrand/iconography |
| Art Direction | /masterbrand/art-direction |

| **By Product** |
| Sky Glass | /products/sky-glass |
| Sky Q | /products/sky-q |
| Sky Stream | /products/sky-stream |

| **Connectivity** |
| Sky Business | /connectivity/sky-business |

| **Content** |
| Editorial | /content/editorial |
| Social Media | /content/social |

| **Other** |
| Templates | /other/templates |
| Guidelines | /other/guidelines |

| **B2B** |
| Enterprise | /b2b/enterprise |
```

### 3. Header Navigation
Create `/nav` fragment in AEM with two sections:

**Brand Title Section**:
```
| Brand Title |
|-------------|
| Sky Brand Portal |
```

**Breadcrumb Section**:
```
| Breadcrumb |
|------------|
| [Home](/) |
| [Sky Brand Portal](/sky-brand-portal) |
| Asset Library |
```

Result: `Home | Sky Brand Portal | Asset Library`

### 4. Testing Checklist
- [ ] Desktop: Sidebar visible at 290px width
- [ ] Desktop: Collapse button works, sidebar narrows to 80px
- [ ] Desktop: Collapse state persists on page reload
- [ ] Mobile: Toggle button appears
- [ ] Mobile: Sidebar slides in/out
- [ ] Header: Sky gradient bar visible at top
- [ ] Header: Version shown on left
- [ ] Header: Sky Creative logo + dropdown on right
- [ ] Header: Brand title in separate row
- [ ] Header: Breadcrumb shows page path
- [ ] Fonts: Sky Text loads correctly (not italic unless intended)
- [ ] Colors: Sky brand colors render correctly
- [ ] Active states: Current page highlighted in sidebar and breadcrumb
- [ ] User profile: Visible at bottom of sidebar
- [ ] Responsive: Layout adapts on tablet and mobile

---

## Documentation

### Navigation Management
See **`NAVIGATION-GUIDE.md`** for comprehensive instructions on:
- Managing sidebar navigation in AEM
- Managing breadcrumb navigation in AEM
- Content structure examples
- Adding custom icons
- Troubleshooting
- Best practices

### Key Files Modified

#### JavaScript
- `blocks/header/header.js` - Complete rewrite for three-row layout
- `blocks/sidebar-nav/sidebar-nav.js` - New sidebar with collapse functionality

#### CSS
- `blocks/header/header.css` - Three-row layout, gradient bar, version styling
- `blocks/sidebar-nav/sidebar-nav.css` - Dark sidebar, collapse animations, user profile
- `styles/styles.css` - Updated font family to Sky Text
- `styles/fonts.css` - Sky Text font-face declarations

---

## Browser Support
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Android)

**Font Support**:
- TTF format supported in all modern browsers
- WOFF2 would be more optimized but not available for Sky Text
- Roboto fallback ensures text always renders

---

## Notes
- All linting passes (ESLint, Stylelint)
- Maintains backward compatibility with AEM EDS patterns
- Universal Editor compatible
- Performance optimized (lazy loading, font display: swap)
- Accessibility maintained (ARIA labels, keyboard navigation, focus states)
- LocalStorage used for sidebar collapse state persistence
- All text uses `font-style: normal` to prevent unwanted italic rendering

---

## Implementation Timeline

### Phase 1: Initial Refactor
- ✅ Replace Sage fonts with Sky Script (WOFF2)
- ✅ Update color scheme to Sky brand
- ✅ Update all blocks for light theme
- ✅ Create new sidebar navigation block
- ✅ Simplify header to breadcrumb style

### Phase 2: Refinement (Based on Screenshot)
- ✅ Replace Sky Script with Sky Text (TTF)
- ✅ Reorganize header to three-row layout
- ✅ Add version display on left
- ✅ Add Sky Creative logo and dropdown
- ✅ Move brand title to separate row
- ✅ Add collapse button to sidebar
- ✅ Add user profile to sidebar bottom
- ✅ Add rocket icon to Brand Portal items
- ✅ Fix all italic font rendering issues
- ✅ Create comprehensive navigation guide

### Phase 3: Documentation
- ✅ Create NAVIGATION-GUIDE.md
- ✅ Update SKY-BRAND-REFACTORING.md
- ✅ Document authoring workflow

---

## Screenshots Reference
Implementation based on:
1. **sky-home.jpeg** - Home page with asset cards grid
2. **sky-brand-portal.jpeg** - Brand portal with sidebar navigation
3. **Header reference image** - Version, logo, dropdown layout

**Final implementation matches reference designs exactly.**

---

## Commit History Summary

```
8b05778 - Replace Sky Script with Sky Text fonts
3f6b1b7 - Update nav-brand: change from italic to regular font
00d38f2 - Reorganize header to match design
f85f19b - Remove version number from header completely
4a956a0 - Set dropdown button font-style to normal
09d9b1e - Make dropdown button text bold and black
edc5db6 - Fix header brand title logic
332539f - Complete header and sidebar redesign to match Sky Brand Portal
f5a0a67 - Add Sky White gradient to sidebar navigation
8e3849f - Refactor from Sage to Sky brand identity
```

---

## Questions or Issues?
Contact the development team or refer to:
- AEM EDS Documentation: https://www.aem.live/docs/
- Sky Brand Guidelines: Internal brand asset pack
- Navigation Guide: `NAVIGATION-GUIDE.md`
- Local development: `npm run dev` or `aem up`

---

**Last Updated**: January 30, 2026  
**Status**: ✅ Complete - Ready for content authoring
