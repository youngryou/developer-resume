# Developer Resume

A developer-centric resume using Astro and Tailwind CSS. It separates content (Markdown) from UI and is optimised for PDF generation.

## Features

- **Data-UI Separation:** Resume and cover letter content are managed via Markdown files.
- **Print-Optimised (`@media print`):** Generates formatted, A4-sized PDFs directly from the browser without any layout breaks.
- **Privacy First:** Sensitive personal information (like phone numbers and emails) is managed via environment variables and safely masked during public deployment.
- **Cover Letter Management:** Includes a public sample file for deployment fallback and a `.gitignore`-protected folder to manage your actual cover letter locally without exposing it to the public repository.
- **Blazing Fast:** Built with Astro for zero-client-side JavaScript by default.

## Tech Stack

- [Astro](https://astro.build/)
- [Tailwind CSS](https://tailwindcss.com/)
- Markdown

## Project Structure

```text
.
├── .github/
│   └── workflows/
│       └── deploy.yml              # Automated DO deployment configuration
├── infra/
│   └── nginx.conf                  # Nginx configuration
├── public/
├── src/
│   ├── components/                 # Shared UI components (e.g., PrintButton.astro)
│   ├── layouts/                    # Global layout containing @media print rules
│   ├── data/
│   │   ├── resume.md               # Core resume content
│   │   ├── cover-letter-sample.md  # Public fallback sample for deployment
│   │   └── cover-letters/          # Local-only cover letters (ignored by Git)
│   └── pages/
│       ├── index.astro             # Main resume page
│       └── cover.astro             # Cover letter page
├── .env.example                    # Template for environment variables
└── .gitignore
```

## Running Locally

1. Clone the repository:

   ```bash
   git clone git@github.com:youngryou/developer-resume.git
   cd developer-resume
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Set up environment variables:
   - Copy `.env.example` to `.env` and fill in your actual contact details (the `.env` file is excluded from Git).

4. Start the development server:

   ```bash
   npm run dev
   ```

5. Open your browser:
   - **Resume**: `http://localhost:4321`
   - **Cover Letter**: `http://localhost:4321/cover`

6. **To write and print your cover letter:**
   - Create the directory and the target file:
     ```bash
     mkdir -p src/data/cover-letters && touch src/data/cover-letters/current.md
     ```
   - Open `current.md` and add your frontmatter and letter body.
   - The local preview at `/cover` will automatically switch from the sample text to your customised content.

7. Click the **"Save as PDF"** button on the top right to test the print layout and save your application documents.

## License

MIT License
