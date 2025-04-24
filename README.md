# CollabNotes - Git-Based Note Collaboration System

A lightweight backend platform where multiple users can create, edit, and track versions of shared notes, using Git-like commands and version control logic.

![GitHub](https://img.shields.io/github/license/plakshaa/git_notes_collaboration)
![Node.js](https://img.shields.io/badge/Node.js-v14%2B-green)
![MongoDB](https://img.shields.io/badge/MongoDB-4.4%2B-blue)

## 🚀 Features

- Create and edit notes with version control
- View note history and specific versions
- Git-like commit functionality
- Optional GitHub integration for storing notes as markdown files
- MongoDB-based versioning system
- RESTful API endpoints
- Comprehensive error handling

## 📋 Prerequisites

- Node.js (v14 or higher)
- MongoDB (running locally or accessible URL)
- GitHub account (optional, for GitHub integration)
- Git CLI

## 🛠️ Installation

1. Clone the repository:
```bash
git clone https://github.com/plakshaa/git_notes_collaboration.git
cd git_notes_collaboration
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory with the following content:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/collabnotes
GITHUB_TOKEN=your_github_token_here    # Optional
GITHUB_REPO=your_repo_name            # Optional
GITHUB_OWNER=your_github_username     # Optional
```

4. Start the server:
```bash
# For development
npm run dev

# For production
npm start
```

## 📡 API Endpoints

### Create a New Note
```http
POST /api/notes
Content-Type: application/json

{
  "title": "Note Title",
  "content": "Note Content",
  "author": "Author Name"
}
```

### Edit a Note
```http
PUT /api/notes/:id
Content-Type: application/json

{
  "content": "Updated Content",
  "author": "Author Name",
  "commitMessage": "Updated note content"
}
```

### View Note Versions
```http
GET /api/notes/:id/versions
```

### Get Specific Version
```http
GET /api/notes/:id?version=2
```

### Commit Changes
```http
POST /api/notes/:id/commit
Content-Type: application/json

{
  "content": "Updated Content",
  "author": "Author Name",
  "commitMessage": "Commit message"
}
```

## 🔄 GitHub Integration

To enable GitHub integration:

1. Create a GitHub personal access token with repo permissions
2. Add the token to your `.env` file as `GITHUB_TOKEN`
3. Set `GITHUB_REPO` and `GITHUB_OWNER` in your `.env` file

When enabled, notes will be automatically synced to your GitHub repository as markdown files.

## 🧪 Testing

To test the API endpoints, you can use tools like Postman or curl. Here's an example using curl:

```bash
# Create a new note
curl -X POST http://localhost:3000/api/notes \
  -H "Content-Type: application/json" \
  -d '{"title":"Test Note","content":"Hello World","author":"Test User"}'

# Get note versions
curl http://localhost:3000/api/notes/:id/versions
```

## 🛡️ Error Handling

The API includes comprehensive error handling for:
- Invalid requests
- Not found resources
- Server errors
- GitHub API errors

