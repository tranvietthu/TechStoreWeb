# TechStore — Phone E-Commerce Website

**Software Engineering Project | ASP.NET Core MVC · .NET 10 · SQL Server**

[English](#english) | [Tiếng Việt](#tiếng-việt)

---

<a id="english"></a>
## 🇬🇧 English

### Overview

**TechStore** is a phone e-commerce web application developed as a software engineering project. It provides a foundation for an online electronics storefront, customer account management, and data-driven store operations.

The repository uses **ASP.NET Core MVC (.NET 10)**, **Entity Framework Core**, and **Microsoft SQL Server**. It also contains configurations for **Google and Facebook sign-in**, an **AI chatbot service**, and **Docker-based deployment**. Some modules may still be under development.

### Technology stack

| Layer | Technology |
| --- | --- |
| Language | C# |
| Web framework | ASP.NET Core MVC, .NET 10 |
| Data access | Entity Framework Core |
| Database | Microsoft SQL Server 2022 |
| Authentication | ASP.NET Core Cookie Authentication; Google and Facebook OAuth integration |
| AI assistance | Configurable chatbot services and LLM client |
| Containerization | Docker and Docker Compose |
| Development | Visual Studio / .NET CLI |
| Version control | Git and GitHub |

### Application architecture

The application follows the **Model–View–Controller (MVC)** pattern:

```text
Browser
   |
   v
ASP.NET Core MVC
   |-- Controllers: HTTP requests and application flow
   |-- Views: rendered user interface
   |-- Models: domain and view data
   |-- Services: application and chatbot logic
   `-- Data / EF Core: database access and initialization
                         |
                         v
                    SQL Server
```

In `Program.cs`, the application registers MVC, database services, authentication, sessions, and chatbot services. It also attempts to create and initialize the database on startup.

### Repository structure

```text
ProjectCongNghePhanMem/
|-- .agents/skills/        # Repository support files
|-- Database/              # Database-related resources
|-- Web_ban_đt/            # Main ASP.NET Core application (TechStoreWeb)
|   |-- TechStoreWeb.csproj
|   |-- Program.cs
|   |-- appsettings.json
|   `-- Dockerfile
|-- web/                   # Additional web resources
|-- Web_ban_đt.slnx        # Visual Studio solution
|-- docker-compose.yml     # Container configuration
|-- .dockerignore
|-- .gitattributes
|-- .gitignore
`-- README.md
```

*The structure above lists verified top-level paths and selected application files; it is not an exhaustive file tree.*

### Getting started (Windows)

**Prerequisites**

- Windows with **Visual Studio** (ASP.NET and web development workload), or the **.NET 10 SDK**.
- SQL Server 2022 (or a compatible SQL Server instance).
- Git.
- Optional: Docker Desktop for container-based workflows.

**1. Clone the repository**

```powershell
git clone https://github.com/tranvietthu/ProjectCongNghePhanMem.git
cd ProjectCongNghePhanMem
```

**2. Configure database access**

Create a local connection string using a development configuration mechanism such as .NET user secrets. From the repository root:

```powershell
cd Web_ban_đt
dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=localhost;Database=TechStoreDb;Trusted_Connection=True;TrustServerCertificate=True;"
```

Replace `localhost` and the authentication method with those used by your SQL Server instance. The connection string shown is an **example**, not a verified default configuration.

**3. Restore and run**

```powershell
dotnet restore TechStoreWeb.csproj
dotnet run --project TechStoreWeb.csproj
```

Open the local URL printed in the terminal. Alternatively, open `Web_ban_đt.slnx` in Visual Studio and run the `TechStoreWeb` project.

**4. Optional integrations**

The project contains settings for Google OAuth, Facebook OAuth, and an AI chatbot. Configure only the integrations you intend to use, using local secrets or environment variables. Examples:

```powershell
dotnet user-secrets set "Authentication:Google:ClientId" "YOUR_CLIENT_ID"
dotnet user-secrets set "Authentication:Google:ClientSecret" "YOUR_CLIENT_SECRET"
dotnet user-secrets set "Authentication:Facebook:AppId" "YOUR_APP_ID"
dotnet user-secrets set "Authentication:Facebook:AppSecret" "YOUR_APP_SECRET"
dotnet user-secrets set "Chatbot:ApiKey" "YOUR_API_KEY"
```

These values are placeholders. Third-party integrations may require additional provider-side setup. Never commit actual credentials, API keys, or production connection strings.

### Docker

The repository includes a multi-stage .NET 10 Dockerfile and a `docker-compose.yml` defining an application service and a SQL Server 2022 service. The current Compose configuration should be reviewed before use: confirm the database volume path, web application port mapping, database connection settings, and container readiness/initialization. **Docker deployment has not been verified by this README.**

### Development notes

- `Program.cs` configures **cookie authentication**, Google/Facebook OAuth, session state, MVC routes, EF Core, and chatbot services.
- On startup, the application invokes database creation and initialization routines. Check the database configuration and initialization behavior before starting against an existing database.
- Features, routes, and integration readiness should be validated against the current controllers, views, and services before a production release.

### Roadmap

Potential next steps for the project:

- [ ] Document all implemented customer and administrator features.
- [ ] Add screenshots of the main storefront and administrative interfaces.
- [ ] Add automated tests for key shopping and authentication flows.
- [ ] Validate database initialization and migrations.
- [ ] Test and refine Docker Compose configuration.
- [ ] Add deployment, security, and monitoring documentation.


---

<a id="tiếng-việt"></a>
## 🇻🇳 Tiếng Việt

### Giới thiệu

**TechStore** là dự án website thương mại điện tử bán điện thoại, được xây dựng phục vụ học tập và thực hành quy trình phát triển phần mềm. Ứng dụng hướng tới việc cung cấp nền tảng cửa hàng trực tuyến, quản lý tài khoản người dùng và dữ liệu phục vụ hoạt động kinh doanh.

Dự án sử dụng **ASP.NET Core MVC (.NET 10)**, **Entity Framework Core** và **Microsoft SQL Server**. Mã nguồn cũng có phần cấu hình **đăng nhập Google/Facebook**, **chatbot AI** và **Docker**. Một số chức năng có thể đang được tiếp tục phát triển.

### Công nghệ sử dụng

| Thành phần | Công nghệ |
| --- | --- |
| Ngôn ngữ | C# |
| Framework | ASP.NET Core MVC, .NET 10 |
| Truy cập dữ liệu | Entity Framework Core |
| Cơ sở dữ liệu | Microsoft SQL Server 2022 |
| Xác thực | Cookie Authentication; tích hợp OAuth Google/Facebook |
| Trợ lý AI | Các dịch vụ chatbot và LLM client có thể cấu hình |
| Đóng gói ứng dụng | Docker, Docker Compose |
| Môi trường phát triển | Visual Studio / .NET CLI |
| Quản lý mã nguồn | Git, GitHub |

### Kiến trúc hệ thống

Ứng dụng được tổ chức theo mô hình **MVC (Model–View–Controller)**:

```text
Người dùng / Trình duyệt
          |
          v
     ASP.NET Core MVC
          |-- Controllers: nhận và xử lý request
          |-- Views: giao diện hiển thị
          |-- Models: mô hình dữ liệu
          |-- Services: nghiệp vụ và chatbot
          `-- Data / EF Core: làm việc với cơ sở dữ liệu
                                  |
                                  v
                              SQL Server
```

Trong `Program.cs`, ứng dụng đăng ký dịch vụ MVC, Entity Framework Core, xác thực, session và chatbot. Khi khởi động, ứng dụng cũng thực hiện các thao tác tạo/khởi tạo dữ liệu.

### Cấu trúc thư mục

```text
ProjectCongNghePhanMem/
|-- .agents/skills/        # Tài nguyên hỗ trợ repository
|-- Database/              # Tài nguyên liên quan đến cơ sở dữ liệu
|-- Web_ban_đt/            # Ứng dụng ASP.NET Core chính (TechStoreWeb)
|   |-- TechStoreWeb.csproj
|   |-- Program.cs
|   |-- appsettings.json
|   `-- Dockerfile
|-- web/                   # Tài nguyên web bổ sung
|-- Web_ban_đt.slnx        # Solution dành cho Visual Studio
|-- docker-compose.yml     # Cấu hình container
|-- .dockerignore
|-- .gitattributes
|-- .gitignore
`-- README.md
```

*Cây thư mục trên thể hiện các mục đã kiểm tra được, không phải danh sách đầy đủ mọi tệp.*

### Hướng dẫn cài đặt và chạy (Windows)

**Yêu cầu môi trường**

- Windows, **Visual Studio** với workload **ASP.NET and web development**, hoặc **.NET 10 SDK**.
- SQL Server 2022 (hoặc phiên bản tương thích).
- Git.
- Docker Desktop (không bắt buộc).

**Bước 1 — Clone repository**

```powershell
git clone https://github.com/tranvietthu/ProjectCongNghePhanMem.git
cd ProjectCongNghePhanMem
```

**Bước 2 — Cấu hình SQL Server**

Từ thư mục gốc của dự án, chạy:

```powershell
cd Web_ban_đt
dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=localhost;Database=TechStoreDb;Trusted_Connection=True;TrustServerCertificate=True;"
```

Đây chỉ là **chuỗi kết nối ví dụ**. Hãy đổi tên máy chủ, cơ sở dữ liệu và phương thức xác thực theo SQL Server đang sử dụng.

**Bước 3 — Khôi phục thư viện và chạy ứng dụng**

```powershell
dotnet restore TechStoreWeb.csproj
dotnet run --project TechStoreWeb.csproj
```

Truy cập địa chỉ localhost được in trong terminal. Ngoài ra, có thể mở `Web_ban_đt.slnx` bằng Visual Studio, chọn project `TechStoreWeb` và chạy.

**Bước 4 — Cấu hình tích hợp (tùy chọn)**

Dự án có phần khai báo cho Google OAuth, Facebook OAuth và chatbot AI. Có thể cấu hình bằng .NET User Secrets:

```powershell
dotnet user-secrets set "Authentication:Google:ClientId" "YOUR_CLIENT_ID"
dotnet user-secrets set "Authentication:Google:ClientSecret" "YOUR_CLIENT_SECRET"
dotnet user-secrets set "Authentication:Facebook:AppId" "YOUR_APP_ID"
dotnet user-secrets set "Authentication:Facebook:AppSecret" "YOUR_APP_SECRET"
dotnet user-secrets set "Chatbot:ApiKey" "YOUR_API_KEY"
```

Các giá trị trên chỉ mang tính minh họa. Việc tích hợp OAuth/AI có thể cần cấu hình bổ sung trên dịch vụ tương ứng. **Không commit mật khẩu, API key hoặc chuỗi kết nối thật lên GitHub.**

### Docker

Repository có Dockerfile build ứng dụng .NET 10 và `docker-compose.yml` khai báo hai service: ứng dụng web và SQL Server 2022. Trước khi chạy bằng Docker Compose, cần kiểm tra lại đường dẫn mount dữ liệu, cổng web, cấu hình kết nối và cơ chế chờ SQL Server sẵn sàng. **Tài liệu này chưa xác nhận quá trình triển khai Docker hoạt động thành công.**

### Ghi chú phát triển

- `Program.cs` cấu hình MVC routing, session, cookie authentication, OAuth Google/Facebook, EF Core và các dịch vụ chatbot.
- Khi khởi động, chương trình có gọi các hàm tạo và khởi tạo database. Nên kiểm tra kỹ trước khi kết nối tới cơ sở dữ liệu đã có dữ liệu quan trọng.
- Cần đối chiếu các controller, view và service hiện tại để xác nhận mức độ hoàn thành từng chức năng trước khi triển khai thực tế.

### Định hướng phát triển

- [ ] Bổ sung danh sách các chức năng người dùng và quản trị đã hoàn thiện.
- [ ] Thêm ảnh minh họa trang chủ, danh sách sản phẩm và giao diện quản trị.
- [ ] Bổ sung kiểm thử tự động cho các luồng mua hàng và xác thực.
- [ ] Hoàn thiện quy trình khởi tạo và quản lý phiên bản cơ sở dữ liệu.
- [ ] Kiểm thử và chuẩn hóa cấu hình Docker Compose.
- [ ] Viết tài liệu triển khai, bảo mật và giám sát ứng dụng.


