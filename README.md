# 🔐 xsukax AES-256 File Encryptor/Decryptor

![](https://raw.githubusercontent.com/xsukax/xsukax-AES-256-File-Encryptor-Decryptor-Frontend/refs/heads/main/ScreenShot.jpg)

A **military-grade**, browser-based file encryption tool that provides **unbreakable AES-256-GCM encryption** with complete privacy. All operations happen directly in your browser - your files and passwords never leave your device.

## 🛡️ Why xsukax AES-256 File Encryptor/Decryptor?

### **Absolute Privacy**
- ✅ **100% Client-Side Processing** - No server uploads, ever
- ✅ **Zero-Knowledge Architecture** - Your data never touches our servers
- ✅ **No Registration Required** - Complete anonymity
- ✅ **No Tracking or Analytics** - What you encrypt stays your business
- ✅ **No File Size Limits** - Encrypt files of any size locally
- ✅ **Offline Capable** - Works without internet connection

### **Unbreakable Security**
- 🔒 **AES-256-GCM Encryption** - The gold standard used by governments and military
- 🔑 **PBKDF2 Key Derivation** - 200,000 iterations for maximum password security
- 🎲 **Cryptographically Secure Random** - Unique salt and IV for every encryption
- 🔐 **Web Crypto API** - Native browser cryptography for maximum performance
- 🛡️ **Authenticated Encryption** - GCM mode ensures data integrity and authenticity

## ✨ Features

### **Core Functionality**
- 📁 **Universal File Support** - Encrypt ANY file type (documents, images, videos, archives)
- ⚡ **Lightning Fast** - Hardware-accelerated encryption via Web Crypto API
- 🎨 **Modern Luxurious UI** - Dark theme with elegant animations
- 📊 **Real-time Progress Bar** - Visual feedback with percentage display
- 💾 **Automatic Downloads** - Encrypted files download instantly
- 🔄 **Seamless Decryption** - One-click decryption with password

### **Technical Excellence**
- **No Dependencies** - Pure vanilla JavaScript, no external libraries
- **Cross-Platform** - Works on any modern browser (Chrome, Firefox, Safari, Edge)
- **Mobile Responsive** - Perfect experience on phones and tablets
- **Lightweight** - Single HTML file under 15KB
- **Open Source** - Fully auditable code for transparency

## 🏗️ System Architecture

```mermaid
graph TB
    subgraph "Browser Environment"
        UI[User Interface]
        FC[File Controller]
        WC[Web Crypto API]
        FS[File System API]
    end
    
    subgraph "Security Layer"
        PBKDF[PBKDF2 Key Derivation]
        AES[AES-256-GCM]
        RNG[Secure Random Generator]
    end
    
    subgraph "Data Flow"
        IF[Input File]
        EF[Encrypted File .enc]
        DF[Decrypted File]
    end
    
    UI --> FC
    FC --> WC
    WC --> PBKDF
    WC --> AES
    WC --> RNG
    
    IF --> FC
    FC --> EF
    EF --> FC
    FC --> DF
    
    FS --> IF
    EF --> FS
    DF --> FS
    
    style UI fill:#007AFF,stroke:#0051D5,stroke-width:2px,color:#fff
    style WC fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
    style AES fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
```

## 🚀 Getting Started

### **Option 1: Direct Usage**
1. Download the `index.html` file
2. Open it in any modern web browser
3. Start encrypting - no installation needed!

### **Option 2: Host It Yourself**
```bash
# Clone the repository
git clone https://github.com/xsukax/xsukax-AES-256-File-Encryptor-Decryptor-Frontend.git

# Navigate to directory
cd xsukax-AES-256-File-Encryptor-Decryptor-Frontend

# Open in browser
open index.html
# or serve it locally
python -m http.server 8000
```

### **Option 3: GitHub Pages**
Host it free on GitHub Pages for easy access from anywhere!

## 📖 How to Use

### **Encrypting Files**

```mermaid
flowchart LR
    A[Select File] --> B[Enter Password]
    B --> C{Password Valid?}
    C -->|Yes| D[Generate Salt]
    D --> E[Generate IV]
    E --> F[Derive Key via PBKDF2]
    F --> G[Encrypt with AES-256-GCM]
    G --> H[Combine Salt + IV + Ciphertext]
    H --> I[Download .enc File]
    C -->|No| J[Show Error]
    J --> B
    
    style A fill:#5AC8FA,stroke:#4BA7D8,stroke-width:2px
    style I fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
    style J fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
```

1. **Select File** - Click "Choose file" and select any file
2. **Enter Password** - Create a strong password (remember it!)
3. **Click Encrypt** - File processes locally with progress indicator
4. **Save .enc File** - Encrypted file downloads automatically

### **Decrypting Files**

```mermaid
flowchart LR
    A[Select .enc File] --> B[Enter Password]
    B --> C[Extract Salt from File]
    C --> D[Extract IV from File]
    D --> E[Derive Key via PBKDF2]
    E --> F[Decrypt with AES-256-GCM]
    F --> G{Authentication Valid?}
    G -->|Yes| H[Download Original File]
    G -->|No| I[Show Error: Wrong Password]
    I --> B
    
    style A fill:#5AC8FA,stroke:#4BA7D8,stroke-width:2px
    style H fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
    style I fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
```

1. **Select .enc File** - Choose your encrypted file
2. **Enter Password** - Use the same password from encryption
3. **Click Decrypt** - Original file restored perfectly
4. **Save Original** - Decrypted file downloads with original name

## 🔬 Technical Specifications

### **Encryption Details**
```
Algorithm:        AES-256-GCM
Key Size:         256 bits
Key Derivation:   PBKDF2-SHA256
Iterations:       200,000
Salt Size:        128 bits (16 bytes)
IV Size:          96 bits (12 bytes)
Tag Size:         128 bits (16 bytes)
```

### **Key Derivation Process**

```mermaid
sequenceDiagram
    participant U as User
    participant B as Browser
    participant WC as Web Crypto API
    participant PBKDF as PBKDF2
    
    U->>B: Enter Password
    B->>WC: Generate Random Salt (16 bytes)
    WC-->>B: Salt
    B->>WC: Import Password as Key Material
    WC-->>B: Key Material
    B->>PBKDF: Derive Key (200,000 iterations)
    Note over PBKDF: SHA-256 Hash Function
    PBKDF->>PBKDF: Iteration 1
    PBKDF->>PBKDF: Iteration 2
    PBKDF->>PBKDF: ...
    PBKDF->>PBKDF: Iteration 200,000
    PBKDF-->>B: AES-256 Key (256 bits)
    B->>WC: Use Key for Encryption
```

### **Security Architecture**
- **Salt**: Random 16-byte value unique per file prevents rainbow table attacks
- **IV**: Random 12-byte initialization vector ensures identical files encrypt differently
- **PBKDF2**: Transforms passwords into cryptographic keys, resistant to brute force
- **GCM Mode**: Provides both confidentiality and authenticity verification

### **File Structure**

```mermaid
graph LR
    subgraph "Encrypted File Format (.enc)"
        A[Salt<br/>16 bytes] --> B[IV<br/>12 bytes]
        B --> C[Ciphertext + Auth Tag<br/>Variable length]
    end
    
    style A fill:#FF9500,stroke:#E68600,stroke-width:2px
    style B fill:#5AC8FA,stroke:#4BA7D8,stroke-width:2px
    style C fill:#007AFF,stroke:#0051D5,stroke-width:2px
```

```
Encrypted File Format (.enc):
[Salt (16 bytes)][IV (12 bytes)][Encrypted Data + Auth Tag]
```

## 🛡️ Security Guarantees

### **Security Model**

```mermaid
graph TD
    subgraph "Threats Protected Against"
        BF[Brute Force Attacks]
        DA[Dictionary Attacks]
        PA[Pattern Analysis]
        TD[Data Tampering]
        SC[Side-Channel Attacks]
    end
    
    subgraph "Protection Mechanisms"
        PBKDF2[200,000 PBKDF2 Iterations]
        SALT[Unique Salt per File]
        IV[Random IV]
        GCM[GCM Auth Tag]
        CT[Constant-Time Ops]
    end
    
    BF --> PBKDF2
    DA --> SALT
    PA --> IV
    TD --> GCM
    SC --> CT
    
    style BF fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
    style DA fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
    style PA fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
    style TD fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
    style SC fill:#d70015,stroke:#b8000f,stroke-width:2px,color:#fff
    
    style PBKDF2 fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
    style SALT fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
    style IV fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
    style GCM fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
    style CT fill:#32a852,stroke:#2d9749,stroke-width:2px,color:#fff
```

### **What We Protect**
- ✅ **File Contents** - Encrypted with military-grade AES-256
- ✅ **File Names** - Original names only visible after decryption
- ✅ **Metadata Privacy** - No timestamps or user data stored
- ✅ **Password Security** - Never stored, logged, or transmitted
- ✅ **Memory Safety** - Automatic cleanup after processing

### **Attack Resistance**
- **Brute Force Protection** - 200,000 PBKDF2 iterations slow down attacks
- **Dictionary Attack Prevention** - Unique salt per file
- **Pattern Analysis Immunity** - Random IV ensures no patterns
- **Tampering Detection** - GCM authentication tag verifies integrity
- **Side-Channel Resistance** - Constant-time operations where possible

## 🔍 Privacy Features

### **Zero-Knowledge Architecture**

```mermaid
graph TB
    subgraph "Your Device"
        F[Your Files]
        P[Your Password]
        E[Encryption Process]
        D[Decryption Process]
    end
    
    subgraph "What Leaves Your Device"
        N[NOTHING]
    end
    
    subgraph "External Servers"
        NS[No Server Contact]
        NC[No Cloud Storage]
        NA[No Analytics]
        NT[No Tracking]
    end
    
    F --> E
    P --> E
    E --> F
    
    F --> D
    P --> D
    D --> F
    
    N -.->|❌| NS
    N -.->|❌| NC
    N -.->|❌| NA
    N -.->|❌| NT
    
    style N fill:#32a852,stroke:#2d9749,stroke-width:3px,color:#fff
    style NS fill:#f5f5f7,stroke:#d2d2d7,stroke-width:2px
    style NC fill:#f5f5f7,stroke:#d2d2d7,stroke-width:2px
    style NA fill:#f5f5f7,stroke:#d2d2d7,stroke-width:2px
    style NT fill:#f5f5f7,stroke:#d2d2d7,stroke-width:2px
```

### **Complete Transparency**
- 100% open source code
- Single HTML file - easy to audit
- No minification - readable source
- No obfuscation - full transparency
- Standard Web Crypto API - trusted implementation

## 💡 Use Cases

### **Personal**
- 🏥 **Medical Records** - Protect sensitive health information
- 💰 **Financial Documents** - Secure tax returns, statements
- 📸 **Private Photos** - Keep personal memories private
- 🔑 **Password Backups** - Encrypt password manager exports
- 📝 **Personal Journals** - Protect private thoughts

### **Professional**
- 💼 **Business Documents** - Secure contracts and proposals
- 🏗️ **Source Code** - Protect proprietary algorithms
- 📊 **Client Data** - GDPR/HIPAA compliant storage
- 🎨 **Creative Work** - Protect designs before release
- 📧 **Sensitive Communications** - Encrypted email attachments

## 🚨 Security Best Practices

### **Password Guidelines**
- Use **minimum 12 characters** (longer is better)
- Mix uppercase, lowercase, numbers, symbols
- Avoid dictionary words or personal info
- Use unique passwords for different files
- Consider using a password manager

### **Operational Security**
- **Never share passwords** over insecure channels
- **Verify file integrity** after decryption
- **Delete original files** after encryption if needed
- **Store .enc files safely** - they're your only copy
- **Test decryption** before deleting originals

## ⚠️ Important Warnings

> **⚠️ Password Loss = Data Loss**  
> There is NO password recovery. If you forget your password, your data is permanently inaccessible. This is a security feature, not a limitation.

> **⚠️ Not a Backup Solution**  
> Encryption is not backup. Always maintain separate backups of important data.

> **⚠️ Browser Compatibility**  
> Requires modern browser with Web Crypto API support (Chrome 37+, Firefox 34+, Safari 11+)

## 🔧 Browser Requirements

| Browser | Minimum Version | Recommended |
|---------|----------------|-------------|
| Chrome | 37+ | Latest |
| Firefox | 34+ | Latest |
| Safari | 11+ | Latest |
| Edge | 79+ | Latest |
| Opera | 24+ | Latest |

## 📊 Performance

- **Encryption Speed**: ~50-100 MB/s (varies by device)
- **Memory Usage**: Minimal (streams large files)
- **File Size Limit**: None (browser memory dependent)
- **Processing**: Utilizes hardware acceleration when available

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### **Areas for Contribution**
- Additional encryption algorithms
- Performance optimizations
- UI/UX improvements
- Localization/translations
- Security audits

## 📜 License

This project is licensed under the **GNU General Public License v3.0** - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Web Crypto API developers for providing native cryptography
- The cryptography community for AES and PBKDF2 standards
- Open source contributors worldwide

---

**🔐 Your Privacy is Not For Sale**

Built with ❤️ for the privacy-conscious community

[Live Demo](https://xsukax.github.io/xsukax-AES-256-File-Encryptor-Decryptor-Frontend/xsukax-AES-256-File-Encryptor-Decryptor.html) | [Report Bug](https://github.com/xsukax/xsukax-AES-256-File-Encryptor-Decryptor-Frontend/issues)
