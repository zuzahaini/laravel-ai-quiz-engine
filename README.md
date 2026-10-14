# AI Quiz & Learning Platform

A full-stack web application for creating exams, taking quizzes, and supporting learning with AI-powered assessment tools.

**Built with Laravel, Livewire, PostgreSQL, and the Laravel AI SDK.**

> **Project status:** In development. This repository contains an existing Laravel AI quiz engine codebase, with further customization and original feature development planned.

## Overview

The AI Quiz & Learning Platform provides a web-based environment for teachers to manage exams and students to complete assessments. It combines exam management, automated evaluation, AI-assisted question generation, and learning recommendations in one application.

The project is being explored and customized as a full-stack development project, with a focus on backend engineering, database integration, AI workflows, and responsive user interfaces.

## Features

### Teacher tools
- Create, edit, and manage exams.
- Organize questions by exam and question type.
- Generate questions with AI.
- Import questions in bulk using CSV files.
- Review student results and exam performance.
- Export results as PDF documents.

### Student experience
- Browse and take published exams.
- Complete timed assessments.
- Navigate questions and flag them for review.
- View scores, feedback, and explanations.
- Receive AI-assisted hints for supported questions.
- Explore recommended practice questions.

### AI and intelligent assessment
- AI-assisted question generation.
- AI-based evaluation of short answers.
- Context-aware grading using semantic similarity search.
- Question and attempt embeddings using PostgreSQL with pgvector.
- Personalized practice recommendations.
- AI usage tracking and configurable usage limits.

### Application infrastructure
- Role-based teacher and student experiences.
- Authentication and account security features.
- Real-time updates using Laravel Reverb.
- Background job processing.
- Responsive interface for desktop and mobile screens.

## Technology Stack

| Layer | Technology |
|---|---|
| Backend | PHP, Laravel 12 |
| Frontend | Livewire, Flux UI, Tailwind CSS |
| Database | PostgreSQL |
| Vector search | pgvector |
| AI integration | Laravel AI SDK |
| Real-time communication | Laravel Reverb, Laravel Echo |
| Authentication | Laravel Fortify |
| Development environment | Docker, Laravel Sail |
| Testing | Pest |
| Code quality | Laravel Pint |

## Architecture Overview

The application follows a full-stack Laravel architecture:

1. **Presentation layer:** Livewire pages provide the teacher and student interfaces.
2. **Application layer:** Laravel manages authentication, exam workflows, validation, and business logic.
3. **Data layer:** PostgreSQL stores users, exams, questions, attempts, and AI usage records.
4. **AI layer:** Agent classes handle question generation, short-answer grading, and hints.
5. **Background processing:** Queued jobs support tasks such as embedding generation and PDF processing.
6. **Real-time layer:** Laravel Reverb and Echo support live updates.

## Getting Started

### Prerequisites

- Git
- Docker Desktop
- Visual Studio Code (recommended)

Docker Desktop is used to run the application and its supporting services.

### 1. Clone the repository

```powershell
git clone https://github.com/zuzahaini/laravel-ai-quiz-engine.git
cd laravel-ai-quiz-engine
```

### 2. Configure environment variables

Create your local environment file:

```powershell
Copy-Item .env.example .env
```

Keep `.env` private. Never commit API keys, passwords, or other secrets.

### 3. Start the Docker services

```powershell
docker compose up -d --build
```

### 4. Generate the application key

```powershell
docker compose exec laravel.test php artisan key:generate
```

### 5. Run database migrations

```powershell
docker compose exec laravel.test php artisan migrate --seed
```

### 6. Install and build frontend assets

```powershell
docker compose exec laravel.test npm install
docker compose exec laravel.test npm run build
```

### 7. Open the application

Open the local application URL configured by your Docker Compose setup. In the current development configuration, this is:

**http://localhost:8040**

If your local configuration uses a different port, use that port instead.

## AI Configuration

AI-powered features require a supported provider and appropriate model configuration.

Configure the provider credentials in your local `.env` file, following the variable names in `.env.example` and `config/ai.php`.

- Keep API keys private.
- Review the provider and model settings before using AI features.
- Local model execution may be possible with Ollama, depending on the application's provider configuration and model compatibility.

AI features may not work until the required provider configuration is completed.

## Testing

The project uses Pest for automated testing.

Run the test suite inside the application container:

```powershell
docker compose exec laravel.test php artisan test
```

## Development Roadmap

The following are planned areas for further development and customization:

- [ ] Complete local AI setup and verify model integration.
- [ ] Test the main teacher and student workflows.
- [ ] Improve error handling and validation.
- [ ] Expand automated test coverage for customized features.
- [ ] Improve documentation and application setup.
- [ ] Develop and document original features.

## Project Structure

```text
app/
├── Ai/             # AI agents
├── Console/        # Artisan commands
├── Events/         # Application events
├── Jobs/           # Background jobs
├── Models/         # Database models
└── Services/       # Application services

config/             # Application configuration
database/           # Migrations and seeders
resources/views/    # Application interfaces
routes/             # Route definitions
tests/              # Automated tests
```

This repository is a work in progress. Further development and project-specific contributions will be documented as they are implemented.
