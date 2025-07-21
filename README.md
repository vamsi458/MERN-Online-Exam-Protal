# MERN Online Exam Portal

A comprehensive online examination platform built with the MERN stack, designed to facilitate seamless exam creation, management, and administration for educational institutions. The platform supports multiple user roles including administrators, teachers, and students, providing a complete end-to-end examination solution.

## 🚀 Features

### Admin Features
- **User Management**: Register teachers, manage user accounts, block/unblock users
- **Subject Management**: Add, remove, and manage examination subjects
- **Dashboard Analytics**: View comprehensive statistics and counts
- **System Administration**: Full control over the examination ecosystem

### Teacher Features
- **Question Bank Management**: Create, update, and manage questions with multiple-choice options
- **Test Creation**: Design comprehensive tests with customizable parameters
- **Subject-wise Organization**: Organize questions by subjects
- **Question Search**: Advanced search functionality for existing questions
- **Test Configuration**: Set test duration, start/end times, and registration periods

### Student Features
- **Test Registration**: Register for available examinations
- **Online Examination**: Take tests with real-time timer functionality
- **Answer Management**: Save and modify answers during the test
- **Result Viewing**: Access detailed test results and performance analytics
- **Test History**: View completed tests and historical performance

### System Features
- **JWT Authentication**: Secure token-based authentication system
- **Role-based Access Control**: Different permissions for admin, teacher, and student roles
- **Real-time Test Management**: Automatic test state transitions
- **Answer Sheet Processing**: Automated scoring and result generation
- **Email Integration**: Nodemailer integration for notifications
- **File Upload Support**: Excel file processing for bulk operations
- **Security**: Helmet.js for security headers and CORS configuration

## 🛠️ Tech Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database with Mongoose ODM
- **JWT** - JSON Web Tokens for authentication
- **Passport.js** - Authentication middleware with local and JWT strategies
- **bcrypt** - Password hashing
- **Nodemailer** - Email service integration
- **Multer** - File upload handling
- **ExcelJS** - Excel file processing

### Frontend - User Portal
- **React 18** - User interface library
- **Material-UI** - React component library
- **Redux** - State management with Redux Thunk middleware
- **React Router DOM** - Client-side routing
- **Axios** - HTTP client for API requests

### Frontend - Admin Portal
- **React 17** - User interface library
- **Material-UI** - React component library
- **Ant Design** - Additional UI components
- **Redux** - State management
- **React Router DOM** - Client-side routing
- **Axios** - HTTP client for API requests

## 📁 Project Structure

```
MERN-Online-Exam-Portal/
├── Server/                 # Backend Node.js application
│   ├── models/            # MongoDB data models
│   ├── schemas/           # Mongoose schemas
│   ├── routes/            # Express route handlers
│   ├── services/          # Business logic and utilities
│   └── app.js            # Express application setup
├── admin/                 # Admin React application
└── user/                  # User React application (Students & Teachers)
```

## 🚀 Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- MongoDB
- npm or yarn

### Backend Setup

1. Navigate to the server directory:
```bash
cd Server
```

2. Install dependencies:
```bash
npm install
```

3. Create a configuration file:
```bash
# Create config/default.json with your MongoDB connection string and JWT secret
{
  "mongodb": {
    "connectionString": "your_mongodb_connection_string"
  },
  "jwt": {
    "secret": "your_jwt_secret"
  }
}
```

4. Start the server:
```bash
npm start
```

The server will start on port 5000 (or PORT environment variable).

### Admin Portal Setup

1. Navigate to the admin directory:
```bash
cd admin
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm start
```

### User Portal Setup

1. Navigate to the user directory:
```bash
cd user
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm start
```

## 🔗 API Endpoints

### Public Routes
- `POST /api/v1/public/register` - Student registration

### Authentication Routes
- `POST /api/v1/login` - User login (teachers and students)
- `POST /api/v1/adminlogin` - Admin login

### Admin Routes (Protected)
- `GET /api/v1/admin/details` - Get admin details
- `POST /api/v1/admin/register` - Register new teacher
- `POST /api/v1/admin/removeUser` - Remove/block user
- `POST /api/v1/admin/unblockUser` - Unblock user
- `POST /api/v1/admin/addSubject` - Add new subject
- `GET /api/v1/admin/getDashboardCount` - Get dashboard statistics
- `GET /api/v1/admin/getAllSubjects` - Get all subjects
- `GET /api/v1/admin/getAllTeachers` - Get all teachers
- `GET /api/v1/admin/getAllStudent` - Get all students

### User Routes (Protected)

#### Common User Routes
- `GET /api/v1/user/details` - Get user details
- `GET /api/v1/user/getAllTest` - Get all tests
- `POST /api/v1/user/getTestById` - Get test details by ID

#### Teacher-specific Routes
- `POST /api/v1/user/addQuestion` - Add new question
- `GET /api/v1/user/getAllSubjects` - Get active subjects
- `POST /api/v1/user/searchQuestion` - Search questions
- `POST /api/v1/user/updateQuestion` - Update question
- `POST /api/v1/user/createTest` - Create new test

#### Student-specific Routes
- `POST /api/v1/user/testRegistration` - Register for test
- `GET /api/v1/user/getAllTestStudent` - Get tests with registration status
- `GET /api/v1/user/getUpcomingTests` - Get upcoming tests
- `POST /api/v1/user/startTest` - Start test attempt
- `POST /api/v1/user/saveAnswer` - Save answer during test
- `POST /api/v1/user/endTest` - Submit and end test
- `GET /api/v1/user/getAllCompletedTest` - Get completed tests
- `POST /api/v1/user/getResultMainDetailsByTestId` - Get test results

## 🗄️ Database Schema

### User Schema
- Username, email, usertype (TEACHER/STUDENT), password, status, createdBy

### Question Schema
- Body, explanation, options, subject, answer, marks, status, createdBy

### Test Schema
- Title, subjects, questions, maxmarks, startTime, endTime, duration, registration times, status

### Answer Sheet Schema
- Test reference, student reference, score, answers array, startTime, completion status

### Subject Schema
- Name, status, createdBy

### Test Registration Schema
- User reference, test reference

## 🔐 Authentication & Authorization

The application uses JWT-based authentication with different strategies:
- **Local Strategy**: Username/password authentication
- **JWT Strategy**: Token-based authentication for protected routes
- **Role-based Access**: Different permissions for admin, teacher, and student roles

## 🚦 Test Flow

1. **Admin** creates subjects and registers teachers
2. **Teachers** create questions and design tests
3. **Students** register for available tests
4. **System** manages test states automatically
5. **Students** take tests within specified time windows
6. **System** processes answers and generates results
7. **Results** are made available after the designated result time

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📝 License

This project is licensed under the MIT License.

## 🐛 Known Issues

- Some service functions may be incomplete (truncated in source)
- Default admin credentials are hardcoded (should be configurable)
- Password validation could be enhanced

## 🔮 Future Enhancements

- Real-time notifications
- Advanced analytics and reporting
- Mobile application support
- Integration with Learning Management Systems
- Automated question generation
- Proctoring capabilities
