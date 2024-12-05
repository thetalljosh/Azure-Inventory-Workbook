# The Ultimate Azure Inventory Dashboard

# Azure Inventory Workbook

This workbook provides a comprehensive dashboard for managing and analyzing your Azure environment. It builds upon the excellent foundation of [scautomation/Azure-Inventory-Workbook](https://github.com/scautomation/Azure-Inventory-Workbook) with added features, customizations, and enhancements.

## Features

* **Inventory:**  Discover and explore your Azure resources with detailed information on their properties, configurations, and relationships.
* **Cost Analysis:** Track and analyze your Azure spending with breakdowns by resource group, subscription, service type, and time period. Identify cost optimization opportunities.
* **Security:** Assess your security posture by identifying vulnerabilities, misconfigurations, and compliance violations. Get recommendations for improving security.
* **Compliance:** Evaluate your resources against industry standards and regulatory requirements (e.g., PCI DSS, HIPAA, SOC 2).
* **User-Friendly Interface:**  Navigate easily through a well-organized and visually appealing dashboard.

## Key Differences from the Original

This fork introduces several enhancements compared to the original workbook:

* **Expanded Scope:** Includes new sections for Cost Analysis, Security, and Compliance.
* **Enhanced Inventory:** Provides more detailed information about resources, including tags and relationships.
* **Improved Organization:**  Uses a more granular and hierarchical structure for better navigation.
* **Optimized Queries:**  Leverages more efficient Azure Resource Graph queries for faster performance.
* **Enhanced User Experience:** Offers a more visually appealing and user-friendly design.

## Getting Started

1. **Deploy the Workbook:** Click the "Deploy to Azure" button below.
   [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fthetalljosh%2FAzure-Inventory-Workbook%2Fmain%2Fgallerytemplate%2Ftemplate.json)

2. **Customize (Optional):** Adjust parameters and filters to tailor the workbook to your specific needs.

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

## Acknowledgments

* This workbook is based on the excellent work by [scautomation](https://github.com/scautomation).
* Thanks to the Azure community for their valuable contributions and feedback.








## Original README from source below:


## related blog post
https://www.cloudsma.com/2020/10/ultimate-azure-inventory-dashboard/

## related video
https://www.youtube.com/watch?v=Kglnm_jDoQ4&feature=youtu.be

### Contribute
Version 2 of this workbook is much more accurate, but I still welcome contributions, ideas etc. Please contribute with pull requests of your own.

### Deployment
How to import Gallery template https://www.cloudsma.com/2020/11/import-azure-monitor-workbooks/


#### Deployment through the PowerShell
------------

```ps

# Variables
$AzureRmSubscriptionName = "Your-Subscription-Name"
$RgName = "Workbook-Rg-Name"
$workbookDisplayName = "Azure Inventory"
$workbookSourceId = "Azure Monitor"
$workbookType = "workbook"
$templateUri = "https://raw.githubusercontent.com/scautomation/Azure-Inventory-Workbook/master/armTemplate/template.json"
$workbookSerializedData = Invoke-RestMethod -Uri "https://raw.githubusercontent.com/scautomation/Azure-Inventory-Workbook/master/galleryTemplate/template.json"

## Connectivity
# Login first with Connect-AzAccount if not using Cloud Shell
$AzureRmContext = Get-AzSubscription -SubscriptionName $AzureRmSubscriptionName | Set-AzContext -ErrorAction Stop
Select-AzSubscription -Name $AzureRmSubscriptionName -Context $AzureRmContext -Force -ErrorAction Stop

## Action
Write-Host "Deploying : $workbookType-$workbookDisplayName in the resource group : $RgName" -ForegroundColor Cyan
New-AzResourceGroupDeployment -Name $(("$workbookType-$workbookDisplayName").replace(' ', '')) -ResourceGroupName $RgName `
  -TemplateUri $TemplateUri `
  -workbookDisplayName $workbookDisplayName `
  -workbookType $workbookType `
  -workbookSourceId $workbookSourceId `
  -Confirm -ErrorAction Stop

```
