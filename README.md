# traceAMS

SIP message and active session monitoring tool for Avaya Media Server.

## Intro

The Avaya Aura® Media Server is a highly scalable software based solution for media control and media processing. Avaya Aura® Media Server (AMS), is always deployed with another Avaya product or application referred to as the "adopting product". Adopting products use the media processing features of AMS by employing Media Server Markup Language (MSML) to control and invoke various services of AMS. MSML is transported over either SIP or REST, depending on the adopting product.

## Business Problem

Many Avaya applications come with a command line tool which provides a consolidated, graphical view of SIP and other type of messages the application sends or receives, for example traceSM in Session Manager, tracePS in Presence Services or traceSBCE in Session Border Controller for Enterprise. These tools can assist the troubleshooting process and are often also used to gather an overall view of how the application is interacting with the outside world. One of the adopting products is the Avaya Communication Manager which utilizes SIP protocol to request from and manage media resources in AMS. However at the time of this writing neither the Communication Manager nor the AMS provide a tool to monitor the exchange of SIP messages amongst them in the Linux shell. The AMS is able to visualize SIP and REST messages on its Web UI but only for one call at a time which may or may not end up to be the call which requires the attention of the system administrator.

## Solution

This tool is aiming at addressing the aforementioned problem in AMS by:

- enabling SIP debug logging from Linux shell
- parsing and retaining 10000 SIP messages in memory
- visualizing the captured messages in a ladder diagram with a brief summary
- querying the "active sessions" at regular intervals (every 3secs by default)
- maintaining and displaying the obtained "active sessions" with their corresponding QoS metrics

## How it works

It makes use of the standard sip.txt debug log file and MYSQL shell commands available to any system administrator with root access. It was developed on Media Server version 8.0 but it was also tested on version 7.8.

## Options

```
  -h, --help     show this help message and exit
  -n <num>       number of SIP messages retained in memory,
                 default 10000, maximum 20000.
  -i <secs>      active sessions refresh interval,
                 default 3secs, minimum 2secs
```

## Demo

![alt text](./images/traceAMS.gif?raw=true "traceAMS")


## Disclaimer

The author in no way provides any warranty, express or implied, towards the content of traceAMS which was not developed or endorsed by the vendor of Avaya Media Server. It is the user's responsibility to determine the value and quality of this tool which is intended for testing purposes and for use by person at their own discretion and risk.