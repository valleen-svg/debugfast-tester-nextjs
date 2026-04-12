# DebugFast Next.js Test App

A Next.js application designed to test and demonstrate the capabilities of DebugFast-JS, a comprehensive error tracking and debugging tool for JavaScript applications.

## Features

This test app showcases various DebugFast features including:

- **Error Boundary Integration**: React error boundaries that catch and report component errors
- **Global Error Handling**: Automatic capture of unhandled errors and promise rejections
- **Manual Error Reporting**: Programmatic error capture with custom context and tags
- **Console Logging**: Capture of console.log, console.warn, and console.error messages
- **Network Request Monitoring**: Tracking of HTTP requests and responses
- **User Action Recording**: Monitoring of user interactions and input
- **Screenshot Capture**: Automatic screenshot capture on errors
- **DOM State Capture**: Recording of DOM state at the time of errors

## Setup

### Prerequisites

- Node.js 18+
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd debugfast-nextjs-tester
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
   - Copy `.env.example` to `.env.locale` and update the `NEXT_PUBLIC_DEBUGFAST_API_KEY` with your DebugFast API key
   - The API key should be in the format: `project-id:api-key`

4. Start the development server:
```bash
npm run dev
```

5. Open [http://localhost:3000](http://localhost:3000) in your browser

## Usage

The app provides several interactive buttons to test different error scenarios:

### Error Testing
- **Trigger React Error Boundary**: Causes a React component to throw an error, testing the error boundary
- **Trigger Global Error**: Simulates an unhandled JavaScript error
- **Trigger Unhandled Rejection**: Creates an unhandled promise rejection
- **Trigger Manual Capture**: Demonstrates programmatic error reporting with custom context

### Feature Testing
- **Trigger Console Logs**: Generates various console messages (error, warn, log)
- **Trigger Network Requests**: Makes HTTP requests to test network monitoring

### User Interaction Testing
- **Input Fields**: Type in the text and password fields to test user action recording
- Password fields are automatically masked in the captured data

## Configuration

DebugFast is configured in `src/app/providers.tsx` with the following options:

```typescript
DebugFast.init({
  apiKey: process.env.NEXT_PUBLIC_DEBUGFAST_API_KEY!,
  captureScreenshot: true,
  captureConsole: true,
  captureNetwork: true,
  captureDom: true,
  captureUserActions: true,
  debug: true,
  beforeSend: (report) => {
    console.log('DebugFast Report:', report);
    return report;
  },
});
```

### Environment Variables

- `NEXT_PUBLIC_DEBUGFAST_API_KEY`: Your DebugFast API key (required)

## Project Structure

```
src/
├── app/
│   ├── app.tsx          # Main test application component
│   ├── layout.tsx       # Root layout with providers
│   ├── page.tsx         # Next.js page component
│   ├── providers.tsx    # DebugFast initialization and error boundary
│   └── globals.css      # Global styles
```

## Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server

### Adding New Tests

To add new test scenarios:

1. Add new button/functionality in `app.tsx`
2. Implement the test logic
3. Ensure proper error handling or intentional error triggering

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License.