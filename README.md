# bold-kettle-grid

![CI](https://img.shields.io/github/actions/workflow/status/retachiyomiidk/bold-kettle-grid/ci.yml?branch=main&label=CI) ![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-3178C6) ![License](https://img.shields.io/github/license/retachiyomiidk/bold-kettle-grid?color=blue) ![Version](https://img.shields.io/badge/version-3.6.7-green)

A minimal, tree-shakeable TypeScript client library with full type definitions. bold-kettle-grid provides a Client class with HTTP method wrappers (get, post, put, delete), configurable retry with exponential backoff, typed ApiResponse and PaginatedResponse interfaces, and request/response interceptors. Built with tsup for CJS+ESM dual output.

## Features

- Automatic retry with exponential backoff (configurable maxRetries, default 3)
- Full TypeScript type definitions: ApiResponse<T> and PaginatedResponse<T>
- Built with tsup for CJS + ESM dual output with .d.ts files
- Tree-shakeable and side-effect free for bundlers
- Client class with get/post/put/delete method wrappers

## Prerequisites

- Node.js 16 or higher
- TypeScript 5.0 or higher
- npm, yarn, or pnpm

## Installation

```bash
npm install bold-kettle-grid
# or
yarn add bold-kettle-grid
# or
pnpm add bold-kettle-grid
```

## Usage

```typescript
import { Client } from 'bold-kettle-grid';
import type { ApiResponse } from 'bold-kettle-grid';

const client = new Client({
  apiKey: process.env.API_KEY!,
  baseUrl: 'https://api.example.com',
  maxRetries: 3,
});

// GET request with typed response
const data = await client.get<ApiResponse<{ id: string; name: string }>>('/items/1');
console.log(data.data.name);

// POST request
const created = await client.post('/items', { name: 'New Item', value: 42 });

// Automatic retry with exponential backoff on failure
// The client retries up to maxRetries times with 2^attempt * 1000ms delay
```

## Project Structure

```
bold-kettle-grid/
├── src/
│   ├── client.ts
│   └── index.ts
├── tests/client.test.ts
├── package.json  tsconfig.json  tsup.config.ts
├── README.md  LICENSE  CHANGELOG.md  CONTRIBUTING.md  CODE_OF_CONDUCT.md
├── .github/
│   ├── workflows/ci.yml
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
└── .gitignore
```

## Running Tests

```bash
npm test
# watch mode
npm test -- --watch
```

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

Quick start:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make your changes and run tests (see [Running Tests](#running-tests) above)
4. Commit with a clear message: `git commit -am 'Add: my feature'`
5. Push to your fork: `git push origin feature/my-feature`
6. Open a Pull Request

Please ensure all tests pass before submitting a pull request.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for a list of changes and version history.

## License

This project is licensed under the Apache-2.0 -- see the [LICENSE](LICENSE) file for details.

Copyright (c) 2026 chen kumar.
