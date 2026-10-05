# Blockendance

## Blockchain-Based Attendance Management System

Blockendance is a Python and Flask-based attendance management system that uses a blockchain-inspired data structure to securely record attendance information.

The project demonstrates how blockchain concepts such as **SHA-256 hashing, block linking, data integrity, tamper detection, persistence, and record verification** can be applied to a practical attendance management system.

---

## 🚀 Project Overview

Traditional attendance systems generally store attendance data in centralized databases where records can potentially be modified.

Blockendance uses a chain of cryptographically linked blocks to maintain attendance records.

Each attendance record contains information such as:

- Teacher name
- Date
- Course
- Enrollment year
- Present students
- Block index
- Previous block hash
- Current block hash

When a new attendance record is added, it becomes a new block connected to the previous block through its hash.

This allows the system to verify whether the blockchain has been modified.

---

## 🎯 Key Features

### 🔗 Blockchain-Based Attendance

Attendance records are stored as blocks in a blockchain structure.

Each block contains:

- Index
- Timestamp
- Attendance data
- Previous block hash
- Current SHA-256 hash

### 🔐 Cryptographic Security

The project uses **SHA-256 hashing** to generate block hashes.

Every block references the hash of the previous block, creating a chain:

```text
Genesis Block
     ↓
Block 1
     ↓
Block 2
     ↓
Block 3
     ↓
Block 4
```

If the contents of a block are modified, its hash changes and the chain integrity check can detect the modification.

### 👨‍🏫 Teacher-Based Attendance

The application starts by collecting the teacher's name.

The teacher can then specify:

- Total number of students
- Course
- Enrollment year
- Attendance date

### 📚 Multiple Courses

The system currently supports courses including:

- Computer Science
- Information Technology
- Electronics
- Mechanical
- Civil

### 🎓 Enrollment Year

The attendance system supports enrollment years from:

```text
2020
2021
2022
2023
2024
2025
2026
```

The selected enrollment year is also used when generating student roll numbers.

For example:

```text
Computer Science-2025-01
Computer Science-2025-02
Computer Science-2025-03
```

### ✅ Attendance Management

Students can be marked:

- Present
- Absent

The interface also provides an option to mark all students as present.

Only students marked present are stored in the attendance record.

### 🔎 Attendance Record Search

Previously stored attendance records can be searched using information such as:

- Teacher
- Course
- Enrollment year
- Date

### 📊 Analytics

The project includes blockchain analytics functionality.

The analytics module can provide information such as:

- Total blocks
- Attendance records
- Total students recorded
- Unique teachers
- Unique courses
- Date ranges
- Teacher statistics
- Course statistics
- Student attendance statistics

### 💾 Data Persistence

The project includes persistence functionality for saving and loading blockchain data.

Blockchain data can be stored in JSON format and loaded when the application starts.

The project also provides export functionality for blockchain and analytics data.

### 📄 Reporting

Attendance reports can be generated from the blockchain data.

The application also provides API endpoints for retrieving statistics, attendance records, analytics, and reports.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core application and blockchain implementation |
| Flask | Web application framework |
| HTML | User interface |
| CSS | Styling |
| Materialize CSS | UI components |
| JavaScript | Client-side interaction |
| SHA-256 | Cryptographic hashing |
| JSON | Data persistence |
| CSV | Data export |

---

## 🏗️ Project Architecture

```text
Blockendance/
│
├── block.py
├── blockchain.py
├── genesis.py
├── newBlock.py
├── getBlock.py
├── checkChain.py
├── persistence.py
├── analytics.py
├── demo.py
│
├── templates/
│   ├── index.html
│   ├── class.html
│   ├── attendance.html
│   ├── view.html
│   └── result.html
│
├── static/
│   ├── css/
│   │   ├── main.css
│   │   └── materialize.css
│   │
│   └── js/
│       └── materialize.js
│
└── blockchain_backups/
```

---

## 🔗 Blockchain Architecture

### 1. Genesis Block

The blockchain begins with a genesis block.

```text
Block 0
├── Index: 0
├── Type: Genesis
├── Previous Hash: 0
└── Hash: SHA-256
```

### 2. Attendance Block

When attendance is submitted, a new block is created.

Example:

```json
{
    "type": "attendance",
    "teacher_name": "Teacher Name",
    "date": "2026-10-06",
    "course": "Computer Science",
    "year": "2025",
    "present_students": [
        "Computer Science-2025-01",
        "Computer Science-2025-03"
    ]
}
```

The block is linked to the previous block using its hash.

### 3. Block Linking

Each block stores the hash of the previous block:

```text
Block 0
   │
   │ prev_hash
   ▼
Block 1
   │
   │ prev_hash
   ▼
Block 2
   │
   │ prev_hash
   ▼
Block 3
```

This provides a mechanism for detecting changes to the chain.

---

## 🔍 Blockchain Integrity Verification

The project includes a blockchain integrity verification system.

The system checks:

1. Whether each block has a valid hash.
2. Whether each block correctly references the previous block.
3. Whether the blockchain remains properly linked.

If a block is modified, the integrity check can report that the blockchain has been compromised.

Example:

```text
Blockchain integrity verified
```

or:

```text
Error: Block #X has invalid hash
```

---

## 🌐 Web Application

The Flask application provides a web interface for interacting with the blockchain.

### Main Flow

```text
Enter Teacher Name
        ↓
Enter Class Details
        ↓
Select Course
        ↓
Select Enrollment Year
        ↓
Enter Number of Students
        ↓
Select Date
        ↓
Mark Attendance
        ↓
Create Blockchain Block
        ↓
Save Blockchain Data
```

---

## 🚀 Installation

### Prerequisites

- Python 3.6 or higher
- pip

### 1. Clone the repository

```bash
git clone https://github.com/sujal9991/blockendance.git
cd blockendance
```

### 2. Install Flask

```bash
pip install Flask
```

### 3. Run the application

```bash
python blockchain.py
```

### 4. Open the application

Open your browser and visit:

```text
http://localhost:5001
```

---

## 🧪 Running the Blockchain Demo

The project also includes a comprehensive demonstration script.

Run:

```bash
python demo.py
```

The demo demonstrates:

- Blockchain creation
- Block creation
- Cryptographic linking
- Integrity verification
- Tamper detection
- Analytics
- Data persistence
- Data export
- Report generation

---

## 📡 API Endpoints

### Blockchain Statistics

```text
GET /api/stats
```

Returns blockchain statistics.

### Attendance Records

```text
GET /api/records
```

Returns attendance records stored in the blockchain.

### Analytics

```text
GET /api/analytics
```

Returns attendance analytics.

### Export

```text
GET /api/export/<format>
```

Supported formats include:

```text
json
csv
analytics
```

### Attendance Report

```text
GET /api/report
```

Reports can also be requested in text format:

```text
GET /api/report?format=text
```

---

## 🎓 Educational Value

This project demonstrates practical implementation of:

- Blockchain fundamentals
- SHA-256 cryptographic hashing
- Linked data structures
- Block creation
- Genesis blocks
- Hash-based block linking
- Blockchain integrity verification
- Tamper detection
- Data persistence
- Data analytics
- Flask web development
- REST-style API endpoints

---

## 🔍 Use Cases

Blockendance can be used as a:

- Blockchain learning project
- College academic project
- Attendance management proof of concept
- Demonstration of cryptographic hashing
- Demonstration of blockchain data integrity
- Starting point for further blockchain-based applications

---

## ⚠️ Project Limitations

This project is intended primarily for educational and demonstration purposes.

### Single-Node Blockchain

The current implementation runs on a single Flask server.

### No Distributed Consensus

The system does not implement a distributed consensus mechanism such as Proof of Work or Proof of Stake.

### Centralized Application

Although attendance records are organized using blockchain concepts, the application itself is hosted and controlled by a single server.

### Simplified Blockchain

This implementation is designed to demonstrate blockchain fundamentals rather than function as a production-grade decentralized blockchain network.

---

## 🔮 Future Improvements

Possible future improvements include:

- User authentication
- Role-based access control
- Student login
- Teacher accounts
- QR-code based attendance
- Mobile application
- Distributed blockchain nodes
- Digital signatures
- Advanced dashboards
- Database integration
- Cloud deployment
- Smart-contract integration
- Decentralized storage

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

You can:

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Commit your changes
5. Submit a Pull Request

---

## 📄 License

This project is licensed under the MIT License.

See the `LICENSE` file for more information.

---

## 👨‍💻 Author

**Sujal Bhandarge**

Computer Engineering Student

GitHub:  
https://github.com/sujal9991

---

## 🙏 Acknowledgement

This project is based on an existing Blockendance implementation and has been customized, modified, and extended for educational and project purposes.

Original project attribution:

**Adeen Shukla**

GitHub:  
https://github.com/adeen-s

---

## ⭐ Project

If you find this project useful for learning about blockchain and Python development, consider giving the repository a star.

**Built with Python, Flask, SHA-256, and blockchain concepts.**
