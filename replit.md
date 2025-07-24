# HMC Accounting + Inventory System

## Overview

This is a full-stack web application built for accounting and inventory management. The system provides comprehensive features for managing vouchers, accounts, customers, products, stock transactions, and sales invoices. It's designed as a single-page application with a modern React frontend and Express.js backend.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **UI Components**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom HMC branding colors
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for client-side routing
- **Form Handling**: React Hook Form with Zod validation
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon Database (serverless PostgreSQL)
- **API Pattern**: RESTful API with conventional HTTP methods
- **Middleware**: Custom logging middleware for API requests
- **Session Management**: Built-in session handling capabilities

### Database Design
The system uses a comprehensive accounting and inventory schema with the following main entities:
- **Users**: Authentication and user management
- **Accounts**: Chart of accounts for double-entry bookkeeping
- **Vouchers & Voucher Entries**: Journal entries and accounting transactions
- **Customers**: Customer information and balances
- **Product Categories**: Product organization and categorization
- **Products**: Inventory items with stock tracking
- **Stock Transactions**: Inventory movement tracking
- **Sales Invoices & Items**: Sales transaction management

## Key Components

### Authentication System
- Basic username/password authentication
- Session-based user management
- User context throughout the application

### Accounting Module
- **Voucher Entry**: Create and manage accounting journal entries
- **Account Ledger**: View individual account transaction histories
- **Voucher Posting**: Post vouchers to update account balances
- **Double-entry bookkeeping**: Maintains accounting equation balance

### Inventory Management
- **Stock Management**: Track inventory in/out transactions
- **Product Categories**: Organize products by category
- **Low Stock Alerts**: Monitor inventory levels and alert on low stock
- **Cost and sale price tracking**: Maintain product pricing information

### Sales System
- **Sales Invoice Creation**: Generate customer invoices
- **Customer Management**: Maintain customer database with balances
- **Invoice Item Management**: Line-item details for sales transactions
- **PDF Generation**: Print-ready invoice generation

### Dashboard & Reporting
- **Summary Cards**: Key performance indicators and metrics
- **Recent Transactions**: Latest voucher and transaction activity
- **Top Products**: Best-selling product analytics
- **Quick Actions**: Shortcuts to common tasks

## Data Flow

### Transaction Processing
1. **User Input**: Forms collect transaction data with validation
2. **API Request**: TanStack Query handles HTTP requests to Express backend
3. **Database Update**: Drizzle ORM processes database operations
4. **State Sync**: Query invalidation updates UI with fresh data
5. **User Feedback**: Toast notifications confirm successful operations

### Inventory Updates
1. **Stock Transactions**: Record inventory movements (in/out)
2. **Product Stock Updates**: Automatic stock level adjustments
3. **Low Stock Monitoring**: Real-time stock level checking
4. **Sales Integration**: Stock reduction on invoice creation

### Accounting Flow
1. **Voucher Creation**: Users create journal entries
2. **Posting Process**: Vouchers update account balances when posted
3. **Ledger Updates**: Individual account histories are maintained
4. **Balance Calculations**: Account balances reflect all posted transactions

## External Dependencies

### Core Libraries
- **Database**: `drizzle-orm`, `@neondatabase/serverless`
- **UI Framework**: `@radix-ui/*` components, `tailwindcss`
- **State Management**: `@tanstack/react-query`
- **Forms**: `react-hook-form`, `@hookform/resolvers`
- **Validation**: `zod`, `drizzle-zod`
- **Styling**: `tailwindcss`, `class-variance-authority`, `clsx`
- **Date Handling**: `date-fns`
- **PDF Generation**: `jspdf` (for invoice printing)

### Development Tools
- **Build System**: `vite`, `esbuild`
- **Type Checking**: `typescript`
- **Development Server**: Custom Vite integration with Express
- **Database Migrations**: `drizzle-kit`

## Deployment Strategy

### Build Process
1. **Frontend Build**: Vite compiles React app to static assets
2. **Backend Build**: esbuild bundles Express server for Node.js
3. **Output Structure**: 
   - Frontend assets → `dist/public/`
   - Backend bundle → `dist/index.js`

### Production Setup
- **Server**: Node.js Express server serves both API and static files
- **Database**: PostgreSQL connection via environment variable
- **Environment**: Production/development modes with appropriate configurations
- **Static Assets**: Express serves built frontend from public directory

### Development Environment
- **Hot Reload**: Vite provides instant frontend updates
- **API Development**: Express server with automatic restart on changes
- **Database**: Drizzle migrations handle schema updates
- **Development Tools**: Built-in error overlay and debugging tools

The system is designed for easy deployment on platforms like Replit, Vercel, or traditional VPS hosting with minimal configuration requirements.