---
title: "Deployment Options"
category: "General"
---

This document describes the supported deployment scenarios for the Application Test Suite (ATS).

## 1 Introduction

Every customer situation is different. We want to make sure there's a convenient deployment option for ATS in all scenarios. The main determinant is where your app is running — either in the cloud or on-premises. The second determinant is the Selenium component, which either can run in the cloud or be hosted on-premises by the customer. For each scenario, we need to ensure secure and reliable communication between the components.

All in all, there are four different supported deployment scenarios. This document describes and compares them.

Please be aware that not every option supports the full set of features. Take a look at [4 Comparing the Options](#4-comparing-the-options) to understand the differences.

## 2 Components

Every ATS deployment consists of four components: the ATS application, the Mendix Cloud Portal, a Selenium Runner, and your Application Under Test (AUT).

The following diagram illustrates how the components are connected:

![ATS simplified architecture](attachments/deployment/ATS_architecture_simplified.png)

### 2.1 Application Test Suite (ATS) Application

The ATS application provides the GUI to create, manage, and run your tests.

### 2.2 Mendix Cloud Portal

The Mendix Cloud Portal is provided as a cloud service by Mendix. It hosts your projects, user stories, and other related data that is also used by the ATS application.

### 2.3 Selenium Runner

The Selenium Runner is used to execute your tests. Once you trigger a test run from ATS, ATS will connect to your Selenium Service provider to start the test. The Selenium Runner then starts the browser and executes the commands that it receives from ATS.

### 2.4 Application Under Test (AUT)

The AUT is the deployed Mendix application that you want to test.

## 3 Deployment Options

There is one standard deployment option in addition to three alternative options. The standard option is recommended, since it is optimized in terms of setup, ease of use, maintenance, and features.

### 3.1 Standard

![Standard Option](attachments/deployment/deploymentoption_standard.png)

The standard option is highly recommended for all customers. It supports all current and future features, is easy to set up, is maintenance-free, and gets the best support.

### 3.2 Public App On-Premises

![Public app on-premise](attachments/deployment/deploymentoption_alternative1.png)

This option is meant for customers who run their app on premises. Since the app runs on premises, it is protected from external access via a firewall. In order to allow the Selenium Runner to access the app, you have to configure your firewall.

### 3.3 Private App On-Premises

![Private app on-premise](attachments/deployment/deploymentoption_alternative2.png)

This option is meant for customers who run their app on premises and who don't want to open their firewall for the Selenium Runner. In order to enable communication between the Selenium Runner and your local application, you have to deploy a Selenium Saas Agent in your local network. This agent will establish a VPN tunnel to your Selenium Service Provider and route all traffic between the Selenium Runner and your application.

### 3.4 Customer-Hosted Selenium

![Customer hosted Selenium](attachments/deployment/deploymentoption_alternative3.png)

This option is meant for customers who run their app on premises and who also want to run their own Selenium Runner. The challenging part of this option is that the customer needs to set up, maintain, and operate its own Selenium Runner.

{{% alert type="warning" %}}
Selenium is an open-source third-party component and there is no active support from Mendix.
{{% /alert %}}

Since the Selenium Runner offers fewer features compared to Selenium SaaS Providers, it is not possible to make use of the full ATS feature set.

{{% alert type="warning" %}}
The feature set in this option is limited.
{{% /alert %}}

## 4 Comparing the Options

Before you pick your option, you need to be aware of the differences. The following two sections will help you to make your choice.

### 4.1 Features

Feature                       | Standard       | Public App On-Premises        | Private App On-Premises      | Customer-Hosted Selenium
----------------------------- | -------------- | ----------------------------- | ----------------------------- | -----------------------------
Test Automation               | ![][green] Yes | ![][green] Yes                | ![][green] Yes                | ![][green] Yes
Test Recording                | ![][green] Yes | ![][green] Yes                | ![][green] Yes                | ![][green] Yes
OS Selection                  | ![][green] Yes | ![][green] Yes                | ![][green] Yes                | ![][red] No
Responsive Testing            | ![][green] Yes | ![][green] Yes                | ![][green] Yes                | ![][red] No
Multiple Browsers<sup>1</sup> | ![][green] All | ![][green] All                | ![][green] All                | ![][green] Yes<sup>2</sup>
Mobile Testing   | ![][green] Yes | ![][green] Yes                | ![][green] Yes                | ![][red] No
Mendix Platform Integration   | ![][green] All | ![][grey] Limited<sup>3</sup> | ![][grey] Limited<sup>3</sup> | ![][grey] Limited<sup>3</sup>
Recording<sup>4</sup> | ![][green] Yes | ![][green] Yes                | ![][green] Yes                | ![][red] No
Future Proof<sup>5</sup>      | ![][green] Yes | ![][green] Yes                | ![][green] Yes                | ![][red] No

<sup>1</sup> For a list of supported browsers see 
[Browser Compatibility](../refguide/rg-version-2/provider_platform_browser_compatiblitiy_table.md).<br />
<sup>2</sup> Additional setup for every browser required.<br />
<sup>3</sup> ATS will integrate with several APIs from the Mendix Cloud to improve the testing experience. Since some of these APIs are only available for apps that run in the Mendix Cloud, certain features cannot be offered for on-premises apps.<br />
<sup>4</sup> Only available for some providers.<br />
<sup>5</sup> Future features may depend on the functionality offered by the Mendix Cloud or the Selenium service providers. They may not be available if you run your app on-premises or host your own Selenium server.

### 4.2 Setup and Maintenance
The following matrix compares the efforts for setup and maintenance of the different options.

Aspect                                | Standard                   | Public App On-Premises     | Private App On-Premises     | Customer-Hosted Selenium
------------------------------------- | ---------------------------| -------------------------- | --------------------------- | ---------------------------------
Firewall Setup                        | ![][green] None**          | ![][red] Required          | ![][green] None<sup>1</sup> | ![][red] Required
Selenium<sup>2</sup> Runner Setup     | ![][green] No<sup>3</sup>  | ![][green] No<sup>3</sup>  | ![][green] No<sup>3</sup>   | ![][red] Customer responsibility
Selenium<sup>2</sup> SaaS Agent Setup | ![][green] No<sup>4</sup>  | ![][green] No<sup>4</sup>  | ![][red] Yes                | ![][green] No<sup>4</sup>
Selenium<sup>2</sup> Maintenance      | ![][green] Yes<sup>3</sup> | ![][green] Yes<sup>3</sup> | ![][green] Yes<sup>3</sup>  | ![][red] Customer responsibility
Selenium<sup>2</sup> Support          | ![][green] Yes<sup>3</sup> | ![][green] Yes<sup>3</sup> | ![][green] Yes<sup>3</sup>  | ![][red] No

<sup>1</sup> A Selenium SaaS Agent with VPN is used to surpass the company network firewall.<br />
<sup>2</sup> Selenium is an open-source third-party component that is not maintained/supported by Mendix.<br />
<sup>3</sup> Provided by your Selenium SaaS provider.<br />
<sup>4</sup> Not required in this option.

### 4.3 Uploading Files

ATS does not support the uploading of files in every situation. This table presents a summary of the different possibilities:

| Selenium Setup | Uploading Your Own File | Uploading a File | Uploading Possible? |
| :-------------- | :---------------------- | :--------------- | :------------------ |
| Local Selenium Server (Docker) | ![](attachments/deployment/grey.png) Limited<sup>1</sup> | ![](attachments/deployment/green.png) Yes | ![](attachments/deployment/green.png) Yes |
| BrowserStack (SaaS) | ![](attachments/deployment/red.png) No | ![](attachments/deployment/green.png) Yes | ![](attachments/deployment/green.png) Yes |
| SauceLabs (SaaS) | ![](attachments/deployment/red.png) No | ![](attachments/deployment/red.png) No | ![](attachments/deployment/red.png) No |
| Selenium SaaS Agent | ![](attachments/deployment/grey.png) Limited<sup>2</sup> | ![](attachments/deployment/green.png) Yes | ![](attachments/deployment/green.png) Yes |

<sup>1</sup> This is only possible when you prepare your own files on that server.<br />
<sup>2</sup> This depends on where the agent is installed.

For more information, see [How to Upload a File in Your App Using ATS](../howtos/ht-version-2/upload-file-using-ats-2.md).

## 5 Selenium SaaS Subscription

### 5.1 General Solutions

{% alert type="warning" %}}
This is a generic advice on which subscription type you need when using a Selenium SaaS provider. Always look what fits best for your situation!
{{% /alert %}}

Selenium SaaS providers in general provide three different solutions.

1. Live testing: With live testing, you can manually test your website/application using a virtual machine that resembles a chosen device. This option is not needed for ATS since it is an automated testing tool. ATS only supports automated browser testing so this solution is not viable.
2. Automated testing: With automated testing, you use the Selenium SaaS providers servers to execute your test cases. The provider hosts selenium/appium and enables all kind of extras. This is the solution you need when using ATS.
3. Mobile testing: With mobile testing, you use the Selenium SaaS providers servers to execute your mobile test cases. The providers host Appium and enable all kind of extras. ATS is only for browser testing so this solution is not viable.

To test your application for desktops and mobile you need automated browser testing.

ATS has two supported selenium providers, see [Supported Selenium Providers](../refguide/rg-version-2/supported-selenium-hub-provider). The solutions of these providers are discussed in the next sections.

### 5.2 Browserstack Solutions/Products

{{% alert type="warning" %}}
Browserstack is a third party, the information displayed may be out of date! This section is pure to help you understand the different solutions.
{{% /alert %}}

These Browserstack solutions are compatible with ATS.

1. Automate Pro, unlimited automated browser testing for desktop sites.<sup>1</sup> If you only want to test your application on desktops browsers then you should choose Automate Pro.
2. Automate Mobile, unlimited automated browser testing for desktop and mobile sites.<sup>1</sup> If you want to test your application on desktop and mobile browsers then you choose Automate Mobile.
3. Enterprise, personalized pricing.

<sup>1</sup> See [Browserstack Automate](https://www.browserstack.com/automate).<br>

For more information on pricing, see [Browserstack Pricing](https://www.browserstack.com/pricing).

### 5.3 SauceLabs Solutions/Products

{{% alert type="warning" %}}
SauceLabs is a third party, the information displayed may be out of date! This section is pure to help you understand the different solutions.
{{% /alert %}}

These SauceLabs solutions are compatible with ATS.

1. Automated, limited browser testing for desktop and mobile sites.<sup>1</sup> If you want to test your application on desktop and mobile browsers choose this option.
2. Unlimited Automated, unlimited browser testing for desktop and mobile sites.<sup>1</sup> If you want to test your application on desktop and mobile browsers unlimited choose this option.
3. Enterprise, personalized pricing.

<sup>1</sup> See [SauceLabs Automated](https://saucelabs.com/products/web-testing).

{{% alert type="info" %}}
There is also a difference between virtual machines and real devices which do not matter for ATS.
{{% /alert %}}

For more information on pricing, see [SauceLabs Pricing](https://saucelabs.com/pricing).

## 6 Setup Instructions

### 6.1 Standard

There are no additional steps required to set up the standard option.

### 6.2 Public App On-Premises

This option requires configuring your firewall in order to allow Selenium to establish a connection to your AUT.

#### 6.2.1 Firewall Configuration

The firewall should accept connections from the internet either on port 80 (if you use http) or port 443 (if you use https) and forward to the web server of your Mendix application.

### 6.3 Private App On-Premises

This option requires you to deploy an agent component on-premise.

#### 6.3.1 Agent Setup

The setup of the agents depends on your provider.

Selenium Service | Agent Name          | Setup Instructions
---------------- | ------------------- | ------------------
BrowserStack     | BrowserStack Local  | [Here](https://www.browserstack.com/local-testing)
SauceLabs        | Sauce Connect Proxy | [Here](https://wiki.saucelabs.com/display/DOCS/Setting+Up+Sauce+Connect+Proxy)


### 6.4 Customer-Hosted Selenium

This option requires you to set up your own Selenium Server on-premises.

{{% alert type="warning" %}}
Selenium is an open-source third-party component and there is no active support from Mendix.
{{% /alert %}}

{{% alert type="info" %}}
Selenium standalone support has been dropped with ATS 2.0. Only Selenium Grid is supported. By following the instructions below, you will set up a Selenium Grid.
{{% /alert %}}

#### 6.4.1 Selenium Runner Setup

We provide basic installation instructions for the Selenium Runner based on Docker containers. For details, see [Get Started with Docker](https://docs.docker.com/engine/getstarted/), [Selenium Documentation](http://www.seleniumhq.org/docs/), and [Docker-Selenium](https://github.com/SeleniumHQ/docker-selenium).

{{% alert type="info" %}}
The current ATS version requires Selenium version 3.8.1. If ATS upgrades to a newer Selenium version, the customer is obligated to upgrade its Selenium Runner to the new version as well.
{{% /alert %}}

Before you start, make sure that your server has internet access to download the container images.

1. Install Docker on your server, as described in [Install Docker Engine](https://docs.docker.com/engine/installation/).
2. Install Docker Compose, as described in [Install Docker Compose](https://docs.docker.com/compose/install/).
3. Create a folder called **selenium** in the user's home directory.
4. Change to the folder and create a file called **docker-compose.yml** with this content:

    ```yaml
    seleniumhub:
        image: selenium/hub:3.8.1
        ports:
        - 4444:4444

    firefoxnode:
        image: selenium/node-firefox-debug:3.8.1
        ports:
        - 5900
        links:
        - seleniumhub:hub
        environment:
        - SCREEN_HEIGHT=1080
        - SCREEN_WIDTH=1920
        - SCREEN_DEPTH=24

    chromenode:
        image: selenium/node-chrome-debug:3.8.1
        ports:
        - 5900
        links:
        - seleniumhub:hub
        environment:
        - SCREEN_HEIGHT=1080
        - SCREEN_WIDTH=1920
        - SCREEN_DEPTH=24
    ```
5. Start up the Selenium grid with this command:

    ```sh
    docker-compose up -d
    ```
6. You now have a grid running on `http://myserver:4444/wd/hub`. Attached to this grid are two nodes: one for Chrome and one for Firefox. You can easiliy scale by starting new nodes with a simple command. This example will start up a second node for both Firefox and Chrome:

    ```sh
    docker-compose scale firefoxnode=2 chromenode=2
    ```

#### 6.4.2 Firewall Configuration

The firewall should accept TCP connections from the internet on port 4444 (the standard port for Selenium Server). This port should forward to your Selenium Server.

[green]:attachments/deployment/green.png
[grey]:attachments/deployment/grey.png
[red]:attachments/deployment/red.png
