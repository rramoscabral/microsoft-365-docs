---
title: "Identity and device access prerequisites for pass-through authentication in your Microsoft 365 test environment"
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 04/23/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection: 
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
description: Create a Microsoft 365 environment to test identity and device access with the prerequisites for pass-through authentication.
---

# Identity and device access prerequisites for pass-through authentication in your Microsoft 365 test environment

*This Test Lab Guide can only be used for Microsoft 365 Enterprise test environments.*

[Identity and device access configurations](microsoft-365-policies-configurations.md) are a set of configurations and conditional access policies to protect access to all services that are integrated with Azure Active Directory (Azure AD), including Office 365 and Enterprise Mobility + Security (EMS) in Microsoft 365 Enterprise.

This article describes how you can configure a Microsoft 365 test environment that meets the requirements of the [Pass-through authentication prerequisite configuration](identity-access-prerequisites.md#prerequisites) for identity and device access.

There are eight phases to setting up this test environment:

1.	Build out your simulated enterprise with pass-through authentication Microsoft 365 test environment
2.	Configure Azure AD seamless single sign-on
3.	Configure named locations
4.	Configure password writeback
5.	Configure self-service password reset
6.	Configure multifactor authentication
7.	Enable Azure AD Identity Protection
8.	Enable modern authentication for Exchange Online and Skype for Business Online

## Phase 1: Build out your simulated enterprise with pass-through authentication Microsoft 365 test environment

Follow the instructions in [Pass-through authentication](pass-through-auth-m365-ent-test-environment.md).

Here is the resulting configuration.

![The simulated enterprise with pass-through authentication test environment](media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
## Phase 2: Configure Azure AD seamless single sign-on

Follow the instructions in [Phase 2 of the Azure AD Seamless Single Sign-on Test Lab Guide](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## Phase 3: Configure named locations

First, determine the public IP addresses or address ranges used by your organization.

Next, follow the instructions in [Configure named locations in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) to add the addresses or address ranges as named locations. 

## Phase 4: Configure password writeback

Follow the instructions in [Phase 2 of the password writeback Test Lab Guide](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## Phase 5: Configure self-service password reset

Follow the instructions in [Phase 3 of the password reset Test Lab Guide](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

When enabling password reset for the accounts in a specific Azure AD group, add these accounts to the **Password reset** group:

- User 2
- User 3
- User 4
- User 5

Test password reset only for the User 2 account.

## Phase 6: Configure multi-factor authentication

Follow the instructions in [Phase 2 of the multi-factor authentication Test Lab Guide](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) for the following user accounts:

- User 2
- User 3
- User 4
- User 5

Test multi-factor authentication only for the User 2 account.

## Phase 7: Enable Azure AD Identity Protection

Follow the instructions in [Phase 2 of the Azure AD Identity Protection Test Lab Guide](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-enable-and-use-azure-ad-identity-protection). 

## Phase 8: Enable modern authentication for Exchange Online and Skype for Business Online

For Exchange Online, follow [these instructions](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

For Skype for Business Online:

1. Connect to [Skype for Business Online](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Run this command.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Verify that the change was successful with this command.

  ```powershell
  Get-CsOAuthConfiguration
  ```

The result is a test environment that meets the requirements of the [Pass-through authentication prerequisite configuration](identity-access-prerequisites.md#prerequisites) for identity and device access. 

## Next step

Use [Common identity and device access policies](identity-access-policies.md) to configure the policies that build on the prerequisites and protect identities and devices.

## See also

[Additional identity Test Lab Guides](m365-enterprise-test-lab-guides.md#identity)

[Phase 2: Identity](identity-infrastructure.md)

[Microsoft 365 Enterprise Test Lab Guides](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Enterprise deployment](deploy-microsoft-365-enterprise.md)

[Microsoft 365 Enterprise documentation](https://docs.microsoft.com/microsoft-365-enterprise/)

