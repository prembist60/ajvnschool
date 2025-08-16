# AJVN School Website — Comprehensive Documentation

## Overview
A simple static website for Amar Jyoti Vidhya Niketan (AJVN) School, built with HTML and CSS. There is no build step or backend. Open the pages directly in a browser.

- Entry point: `index.html`
- Shared stylesheet: `styles.css`
- Additional pages: `about.html`, `contact.html`, `course.html`

## File Structure
- `index.html`: Home page with hero image, features, and shared header/nav/footer
- `about.html`: About page with `.about-content`
- `contact.html`: Contact page with a styled form in `.contact-form`
- `course.html`: Courses page (uses `sty.css` and `script.js` placeholders; see Known Issues)
- `styles.css`: Global styles for layout, navigation, hero image, features, form, and buttons
- `45.jpg`: Image used by the home page hero
- `12.JPG`: Large image asset (currently unused)

## Public Components and Markup Contracts
The site exposes a small set of reusable structural components via HTML markup patterns and CSS class names. Treat these as your “public API”.

### Layout
- Header (`<header>`)
  - Contains the page title and optional tagline.
  - Styles: background color, centered white text, padding.
  - Usage:
```html
<header>
	<h1>Welcome to Amar Jyoti Vidhya Niketan School</h1>
	<p>Igniting Minds, Empowering Futures</p>
</header>
```

- Navigation (`<nav>` with links)
  - Horizontal top navigation bar with white links.
  - Usage:
```html
<nav>
	<a href="index.html">Home</a>
	<a href="about.html">About Us</a>
	<a href="contact.html">Contact</a>
	<a href="course.html">Course</a>
</nav>
```

- Footer (`<footer>`)
  - Full-width footer with centered white text.
  - Usage:
```html
<footer>
	<p>&copy; 2023 AJVN School. All rights reserved.</p>
</footer>
```

### Content Sections
- Hero (`<section class="hero">`)
  - Displays a full-width responsive image.
  - Styles: `.hero img { width: 100%; height: auto; }`
  - Usage:
```html
<section class="hero">
	<img src="45.jpg" alt="School Image">
</section>
```

- Features (`<section class="features">`)
  - A content block with padding for listing school strengths.
  - Usage:
```html
<section class="features">
	<h2>Our Features</h2>
	<ul>
		<li>PG to 10 class</li>
		<li>Experienced teacher's team</li>
		<li>Rich Extracurricular Activities</li>
		<li>Focus on Holistic Development</li>
	</ul>
</section>
```

- About Content (`<section class="about-content">`)
  - Free-form text container used on `about.html`.
  - Usage:
```html
<section class="about-content">
	<p>Welcome to Amar Jyoti Vidhya Niketan...</p>
</section>
```

- Contact Form (`<section class="contact-form">` containing `<form>`)  
  - A centered, max-width form with grid layout; labels and fields are full-width.
  - Usage:
```html
<section class="contact-form">
	<h2>Get in Touch</h2>
	<form>
		<label for="name">Name:</label>
		<input type="text" id="name" name="name" required>

		<label for="email">Email:</label>
		<input type="email" id="email" name="email" required>

		<label for="message">Message:</label>
		<textarea id="message" name="message" required></textarea>

		<button type="submit">Submit</button>
	</form>
</section>
```

- Courses Page Sections (in `course.html`)
  - Home/Hero: `<section id="home" class="hero"> ... <button onclick="learnMore()">Learn More</button>`
  - About: `<section id="about">`
  - Courses List: `<section id="courses">`
  - Contact: `<section id="contact">` with a simple form
  - Note: This page references `sty.css` and `script.js` which are not present (see Known Issues). The `onclick="learnMore()"` hook expects a function in `script.js`.

## Style API Reference (CSS)
Below are the key selectors you can rely on across pages.

- `body`: Base font family (`Arial`), line-height, text color, margin/padding reset
- `header`: Teal background, white text, padding, centered text
- `nav`: Pink background, white text, padding, centered; anchors are white with spacing
- `nav a`: White links with no underline and 15px horizontal margin
- `.hero img`: Full-width responsive image
- `.features`: Padded section
- `footer`: Blue background, white text, centered, full width
- `.contact-form`: Max width 600px and centered with top/bottom margin
- `form`: CSS grid with gap between rows
- `label`: Block display with small bottom margin
- `input, textarea`: Full-width controls with padding
- `button`: Blue background, white text, padding, no border, pointer cursor

## Usage Examples

- Add a new hero image to any page:
```html
<section class="hero">
	<img src="path/to/your-image.jpg" alt="Descriptive alternate text">
</section>
```

- Create a new feature list:
```html
<section class="features">
	<h2>Why Choose Us</h2>
	<ul>
		<li>Student-centered learning</li>
		<li>Modern facilities</li>
		<li>Community engagement</li>
	</ul>
</section>
```

- Reuse the contact form on another page:
```html
<section class="contact-form">
	<h2>Contact Admissions</h2>
	<form>
		<label for="fullName">Full Name:</label>
		<input type="text" id="fullName" name="fullName" required>

		<label for="email">Email:</label>
		<input type="email" id="email" name="email" required>

		<label for="message">Message:</label>
		<textarea id="message" name="message" required></textarea>

		<button type="submit">Send</button>
	</form>
</section>
```

- Implement the missing `learnMore()` (for use in `course.html` only):
```html
<!-- Add this near the end of course.html just before </body> if you create script.js later -->
<script>
	function learnMore() {
		alert('Thank you for your interest! Please explore the Courses and About sections.');
	}
</script>
```

## How to Add a New Page
1. Duplicate `about.html` or `index.html` as a starting point.
2. Keep the `<header>`, `<nav>`, and `<footer>` for consistency.
3. Link the shared stylesheet:
```html
<link rel="stylesheet" href="styles.css">
```
4. Add your page-specific content inside appropriate sections.
5. Update the navigation (`<nav>`) links on all pages to include your new page.

## Running Locally
No server is required. Double-click any `.html` file to open it in your browser, or serve the folder with a simple static server (e.g., `python -m http.server 8000`).

## Accessibility Notes
- Always include descriptive `alt` text for images.
- Ensure `label` elements’ `for` attributes match input `id`s (already followed in `contact.html`).
- Verify color contrast meets WCAG AA, as some current color combinations may be low contrast.

## Known Issues and Recommendations
- `course.html` links to `sty.css` which is not in the repository. To use the shared styles, change to `styles.css`.
- `course.html` references `script.js` and uses `onclick="learnMore()"`, but `script.js` does not exist. Either add the function inline or create a `script.js` file and include it.
- `12.JPG` is present but unused; consider removing it if unnecessary to reduce repository size.

## Changelog
- Initial documentation generated to cover components, CSS API, usage examples, and guidance for extending the site.