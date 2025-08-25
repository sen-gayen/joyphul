# Joyphul - Gratitude-Sharing Social Platform

## Overview

Joyphul is a gratitude-sharing social platform that enables users to "plant seeds of joy" by sharing meaningful moments, places, things, and ideas with a community. The application features a flower and garden-inspired design with coral, sage green, and golden yellow theming. Users can create posts ("seeds"), view community content in a feed ("the garden"), engage through comments and "blooms" (likes), and maintain personal profiles.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

The application uses a **React-based frontend** built with Vite for fast development and optimized builds. The architecture follows a component-based pattern with:

- **React Router (Wouter)**: Lightweight routing for navigation between home, profile, and other pages
- **TanStack Query**: Server state management for API calls, caching, and synchronization
- **React Hook Form + Zod**: Form handling with client-side validation
- **shadcn/ui + Tailwind CSS**: Modern UI component library with utility-first styling
- **Custom theming**: Garden-inspired color palette (coral, sage green, golden yellow) with CSS variables

### Backend Architecture

The backend implements a **REST API using Express.js** with the following design patterns:

- **Modular routing**: API endpoints organized by resource (seeds, comments, blooms, users)
- **Storage abstraction**: Interface-based storage layer allowing for different implementations (currently in-memory for development)
- **Middleware pattern**: Request logging, JSON parsing, and error handling
- **Development/Production separation**: Vite integration for development, static serving for production

### Data Storage Solutions

The application uses **Drizzle ORM** with **PostgreSQL** for data persistence:

- **Schema definition**: Type-safe database schema with relations between users, seeds, comments, and blooms
- **Connection management**: Neon serverless PostgreSQL with connection pooling
- **Migration support**: Drizzle Kit for schema migrations and database management
- **Type safety**: Generated TypeScript types from database schema

### Database Schema Design

- **Users**: Profile information with optional avatar support
- **Seeds**: Main content posts with text, optional images, categorization tags, and bloom counts
- **Comments**: Threaded discussion on seeds
- **Blooms**: Like/reaction system with user-seed relationships
- **Relational integrity**: Foreign key constraints and cascade deletes

### API Design Patterns

The REST API follows consistent patterns:

- **Resource-based URLs**: `/api/seeds`, `/api/users/{id}/seeds`, `/api/seeds/{id}/comments`
- **HTTP method semantics**: GET for retrieval, POST for creation
- **Validation**: Zod schemas for request/response validation
- **Error handling**: Centralized error middleware with proper HTTP status codes
- **Response consistency**: Standardized JSON response format

### UI/UX Architecture

The interface implements a **mobile-first responsive design**:

- **Component composition**: Reusable UI components built on Radix primitives
- **Accessibility**: ARIA compliance through Radix UI components
- **Progressive enhancement**: Core functionality works without JavaScript
- **Touch-friendly**: Mobile-optimized interactions and layouts
- **Theme system**: CSS custom properties for consistent design tokens

## External Dependencies

### Database Services

- **Neon Database**: Serverless PostgreSQL hosting with automatic scaling
- **@neondatabase/serverless**: WebSocket-based database client for serverless environments

### UI/Component Libraries

- **Radix UI**: Unstyled, accessible component primitives for complex UI elements
- **Tailwind CSS**: Utility-first CSS framework for styling
- **shadcn/ui**: Pre-built component library combining Radix UI with Tailwind styling
- **Lucide React**: Icon library for consistent iconography

### Development Tools

- **Vite**: Build tool and development server with hot module replacement
- **TypeScript**: Type safety across the entire application
- **Drizzle Kit**: Database schema management and migration tools
- **ESBuild**: Fast JavaScript bundling for production builds

### Form and Validation

- **React Hook Form**: Performance-optimized form state management
- **Zod**: Runtime type validation for forms and API requests
- **@hookform/resolvers**: Integration between React Hook Form and Zod

### State Management

- **TanStack Query**: Server state management with caching, background updates, and optimistic updates
- **React Context**: Client-side state for UI preferences and user session

### File and Asset Management

- **PostCSS**: CSS processing with Tailwind CSS integration
- **Autoprefixer**: Automatic vendor prefixing for CSS properties

The application is designed to be deployed on platforms supporting Node.js with PostgreSQL database connectivity, with specific optimizations for Replit's environment including development banner integration and runtime error overlays.