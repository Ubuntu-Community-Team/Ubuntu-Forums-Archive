---
title: "openOCD, UDEV rules, and USB Access"
date: 2017-12-13
forum: General Help
---

### Post by mcdeltat on 2017-12-13
<SOLVED>
Geez. So maybe someone can explain to me what the difference is between restarting the machine and running "udevadm control --reload-rules". I had previously run that and no changes occurred. Given I had just posted this, I figured it was a good time to restart and that fixed my problem. My user was already a member of plugdev, so it shouldn't have required me to log out to grant those permissions. The world may never know at this point.

Hi all. My system is running Ubuntu 16.04. I have a STM32 Nucleo board that I'm trying to start developing freeRTOS with, I have an environment set up in Eclipse, but when trying to run openOCD I'm running into some USB Access problem that is just killing me. 

What I've done:
1. Made sure my user was a member of plugdev. This was already done when working with the Teensy Microcontroller, and that worked fine. 
2. Copied the UDEV rules provided by the GNU MCU Eclipse openOCD fork, which provides specific rules for the board interface.

When running it in Eclipse I get the error:
Error: libusb_open() failed with LIBUSB_ERROR_ACCESS
Error: open failed
in procedure 'init' 
in procedure 'ocd_bouncer'

Wheras running the same command in the terminal with SUDO works fine. So this is clearly a permissions issue, what else can I do?

Thanks.

---

