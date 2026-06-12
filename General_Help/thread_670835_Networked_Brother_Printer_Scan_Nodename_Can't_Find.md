---
title: "Networked Brother Printer Scan Nodename Can't Find IP Address MFC7820N"
date: 2008-01-17
forum: General Help
---

### Post by RazorFish1 on 2008-01-17
I have a Brother MFC7820N multi-function printer in a networked configuration; i.e. attached to the network rather than to the PC via USB.  I followed the instructions on the Brother site and have the printer working wonderfully.  I've installed, de-installed, and re-installed the scanner with utilities several times and continue to receive the following error when loading the XSANE Image Scanner: Failed to open device 'brother2:net1;dev0':Invalid argument.  I'm trying to define the printer using the nodename capability since the router is not capable of establishing a static IP address when in DHCP mode for the other devices.  All ideas are welcome.

---

### Post by dcstar on 2008-01-17
> **RazorFish1 said:**
> I have a Brother MFC7820N multi-function printer in a networked configuration; i.e. attached to the network rather than to the PC via USB.  I followed the instructions on the Brother site and have the printer working wonderfully.  I've installed, de-installed, and re-installed the scanner with utilities several times and continue to receive the following error when loading the XSANE Image Scanner: Failed to open device 'brother2:net1;dev0':Invalid argument.  I'm trying to define the printer using the nodename capability since the router is not capable of establishing a static IP address when in DHCP mode for the other devices.  All ideas are welcome.

Simply put an entry in your hosts file with the IP of the printer with that name.

---

### Post by RazorFish1 on 2008-01-18
dcstar - thanks for the help.  Does Ubuntu have a way to detect when the IP address of the printer changes or do I have to monitor and update the Nodename affiliation manually?

---

### Post by dcstar on 2008-01-18
> **RazorFish1 said:**
> dcstar - thanks for the help.  Does Ubuntu have a way to detect when the IP address of the printer changes or do I have to monitor and update the Nodename affiliation manually?

You would have to do it manually - the easier way would be to set a Static IP for the printer - easy to do via the web interface (IIRC).

---

### Post by RazorFish1 on 2008-01-21
dcstar: I need more hand holding.  Can you take me through a step by step process to set a static IP using the iirc web interface?

---

### Post by RazorFish1 on 2008-02-18
For anyone who follows me:

My fundamental issue was that I was using a nodename when I should have used the IP address - contrary to the Brother website documentation.  Secondly, I was using the zero's   in front of the numbers when specifying the IP address and ubuntu doesn't like that.  I removed the zeros and everything worked fine.

Here's lookin' at you kid!

---

