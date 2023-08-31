# Reportgen

Generate PDF reports for Khulnasoft CSP image and host vulnerabilities.

## Build 

To build the container image, clone this project and run the following command:

```
docker build -t khulnasoft-reports .
```

## Generating Reports

To generate a PDF report, you should have an Khulnasoft CSP console, user and password to this console and an image that you would like to create a report for.

After creating the reportgen image, you should run the following command to generate a PDF report for a specific image:

```
docker run -it -v /tmp:/reports khulnasoft-reports -server <Khulnasoft Server URL> -user <User> -password <Password> -image <Image name> -registry <Registry Name> -output /reports/report.pdf
```

This command will generate a report file called "report.pdf" and put it under /reports directory in the container, which is mounted to "/tmp" directory on your host.

## Usage
```
NAME:
  reportgen - A tool to generate PDF reports for Khulnasoft CSP images and hosts

USAGE:
  main [-image|-host] <name> [parameters] 

OPTIONS:
  -image        Image name to generate report for (e.g. mongo:latest)
  -host         Host name to generate report for 

MANDATORY PARAMETERS:
  -server       Khulnasoft CSP server URL
  -user         User name
  -password     Password
  -output       Output file where to save PDF

OPTIONAL PARAMETERS:
  -severity     Comma seperated list of severities to export (critical, high, medium, low)
```
