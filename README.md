# 🏗️ FabricForge

**Simplifying Microsoft Fabric Provisioning**

FabricForge is a client-side web application that streamlines the creation and configuration of Microsoft Fabric Workspaces, Lakehouses, and Warehouses through an intuitive interface and automated N8N workflows.

![FabricForge](https://img.shields.io/badge/Microsoft-Fabric-blue?style=flat-square&logo=microsoft)
![N8N](https://img.shields.io/badge/N8N-Automation-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

## 🌟 Features

- **🎨 Intuitive Form Builder**: Visual interface for designing Fabric workspace structures
- **📊 Lakehouse Management**: Create lakehouses with custom tables and schemas
- **🏢 Warehouse Configuration**: Set up warehouses with proper configurations
- **📓 Notebook Integration**: Automatically attach and configure Fabric notebooks
- **🔄 JSON Import/Export**: Save and reuse configurations
- **🔒 Secure by Design**: Client-side only - no data storage
- **🤖 AI-Powered**: Automatic PySpark code generation for table creation
- **✅ Idempotent Operations**: Safe to run multiple times

## 🚀 Quick Start

### Prerequisites

1. **Microsoft Fabric Capacity** (F2 or higher recommended)
2. **Azure AD App Registration** with Fabric API permissions
3. **N8N Instance** for workflow automation
4. **Web Browser** (Chrome, Firefox, Edge, or Safari)

## 📋 Usage Guide - sulaiman013.github.io/fabric-form

### 1. Fill Prerequisites
- **Capacity ID**: Your Microsoft Fabric capacity identifier
- **User ID**: Unique identifier with workspace creation permissions
- **Client ID**: Azure AD application ID
- **Client Secret**: Application secret value
- **Tenant ID**: Azure AD tenant ID
- **N8N Webhook URL**: Your workflow webhook endpoint

### 2. Design Your Workspace
- Enter workspace name
- Add Lakehouses with:
  - Custom names
  - Optional attached notebooks
  - Table structures with columns and data types
- Add Warehouses with custom names

### 3. Submit Configuration
- Preview your configuration in JSON format
- Submit to trigger the N8N workflow
- Monitor progress in your N8N instance

## 🔧 Configuration Example

```json
{
  "Prerequisites": {
    "CapacityId": "12345678-1234-1234-1234-123456789012",
    "UserId": "user-unique-id",
    "ClientId": "87654321-4321-4321-4321-210987654321",
    "ClientSecret": "your-secret",
    "TenantId": "abcdef12-3456-7890-abcd-ef1234567890",
    "WebhookUrl": "http://xxxx/webhook-test/xxxx"
  },
  "WorkspaceName": "DataAnalytics",
  "Lakehouses": [
    {
      "name": "SalesLH",
      "attachedNotebook": "SalesAnalysis",
      "tables": [
        {
          "name": "Orders",
          "columns": [
            {"name": "OrderID", "dataType": "varchar"},
            {"name": "Amount", "dataType": "float"}
          ]
        }
      ]
    }
  ],
  "Warehouses": [
    {"name": "ReportingWH"}
  ]
}
```

## 🏗️ Architecture

```
FabricForge (Browser) → N8N Webhook → Microsoft Fabric APIs
     ↓                      ↓                    ↓
   No Storage          Processes Data      Creates Resources
```

### Workflow Steps
1. **Authentication**: Obtains access token using provided credentials
2. **Workspace Check**: Verifies if workspace exists or creates new
3. **Capacity Assignment**: Links workspace to specified capacity
4. **Resource Creation**: Sequentially creates lakehouses and warehouses
5. **Notebook Setup**: Creates notebooks with AI-generated code
6. **Table Creation**: Executes notebooks to create Delta tables

## 🔒 Security

- **Zero Storage**: No backend servers or databases
- **Direct Transmission**: Data flows directly to your N8N instance
- **Client-Side Only**: All processing happens in your browser
- **Transparent Workflow**: Open-source N8N workflow for full visibility

## 🛠️ Customization

### Modify Supported Data Types
Edit the `fabricDataTypes` array in the JavaScript:
```javascript
const fabricDataTypes = [
    'bigint', 'binary', 'bit', 'char', 'date', 
    // Add more types as needed
];
```

### Adjust UI Theme
Modify CSS variables in the `:root` selector:
```css
:root {
    --primary: #2d5a3d;
    --primary-hover: #1f4d2e;
    // Customize colors
}
```

### Extend N8N Workflow
- Add error notifications
- Implement progress tracking
- Include additional Fabric resources
- Customize AI prompts for code generation

## 📝 Troubleshooting

| Issue | Solution |
|-------|----------|
| Authentication fails | Verify Client ID, Secret, and Tenant ID |
| Webhook not responding | Check N8N workflow is active and URL is correct |
| Resources not created | Ensure user has proper Fabric permissions |
| Rate limiting | Workflow includes delays, but large configs may need adjustment |

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Microsoft Fabric team for the comprehensive APIs
- N8N community for the automation platform
- OpenAI for powering intelligent code generation

---

**Note**: This tool is not officially affiliated with Microsoft. Use at your own discretion and ensure compliance with your organization's policies.
