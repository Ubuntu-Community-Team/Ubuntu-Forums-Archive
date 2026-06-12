---
title: "brother printer"
date: 2006-10-14
forum: General Help
---

### Post by bas1234 on 2006-10-14
I have tired multiple linux drivers and searched both the brother download site and ubuntu with no luck finding the multitasking drivers that work. The printer supplies windows xp drivers which work fine but I want to continue to use Ubuntu. The printer is a network printer with an IP address.  Any help would be appreciated. Barry

---

### Post by drpaul on 2006-10-14
I have a Brother HL-5140, and while there is no driver for it there is one that is compatible [1250 or something]. Does the Brother site suggest something? How about an HP driver in a compatibility mode?

Paul

---

### Post by danbert on 2007-08-01
I have a Brother MFC-5460CN printer and the drivers and instructions from the Brother website work fine for USB,  However, I haven't been able to configure it correctly to access it over the network.  Any suggestions?

---

### Post by stinger30au on 2007-08-01
> **bas1234 said:**
> I have tired multiple linux drivers and searched both the brother download site and ubuntu with no luck finding the multitasking drivers that work. The printer supplies windows xp drivers which work fine but I want to continue to use Ubuntu. The printer is a network printer with an IP address.  Any help would be appreciated. Barry

whats the model number of the printer?

have you read thru the manual for the printer to see what kinds of printers it emulates?
You should be able to find a driver for it that will work if you use one of the emulated printer drivers.
when you setup the printer, tell Ubuntu the IP address of themachine with the emulated driver and you should be in business

---

### Post by danbert on 2007-08-01
Success!  I figured it out.  In the printer menu select the global settings drop down and select "Detect LAN Printers".  After that, add a printer and select use another printer by specifying port and it will list "unknown printer on xxx.xxx.xxx.xxx (IP address of printer)".  Select that and then specify the correct driver.  That worked for me.

---

