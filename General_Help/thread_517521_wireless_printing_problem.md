---
title: "wireless printing problem"
date: 2007-08-04
forum: General Help
---

### Post by xjgnsdof on 2007-08-04
I have two laptops, one that dual-boots Ubuntu and WinXP and uni-boots Ubuntu. I bought the printer specified above and configured it for wireless printing on the dual-booting laptop in Windows. The driver installation went without a hitch because it ran in an OS it was made for. When I am connected to the wireless network that I specified during installation, I print wirelessly and flawlessly.

However, I cannot set up my uni-boot laptop to wirelessly print to the same printer because it doesn't recognize the "setup" file on the installation disc, even when I open it with WINE. Therefore, I have to print via USB cable...

How can I set up my Deskjet for wireless printing from my uni-boot laptop? Also, how can I run the HP utilities that monitor ink levels and so on in Ubuntu?

---

### Post by TBerben on 2007-08-04
HP printers should work without a hitch in Ubuntu, the HPLIP toolkit is installed and enabled by default. If the printer is shared via the network CUPS should be able to autodetect it after which you can select the proper driver for it. Could you please specify how your printer is connected to the network? (e.g. directly plugged into the router, via a print server, etc)

---

### Post by xjgnsdof on 2007-08-04
I connected my uni-boot laptop to the printer via USB cable, and it works fine.

My uni-boot laptop uses a wireless adapter to connect to the wireless network emitted from the router in my apartment. To be clear, my problem is wirelessly printing from the uni-boot laptop to the  printer.

---

### Post by xjgnsdof on 2007-08-04
So I have to enter Windows the Terrible to configure my uni-boot laptop for wireless printing access?

---

### Post by strabes on 2007-08-05
No, go to [http://localhost:631](http://localhost:631) in firefox and add the printer. The easiest way is to add it using the url which is of the format: ```
http://hostnameorip:631/printers/printername
```

---

### Post by xjgnsdof on 2007-08-05
"Problem loading page."

If this has to do with CUPS, don't bother. I've already set it up for wired printing through CUPS. Any other ideas?

---

### Post by xjgnsdof on 2007-08-12
up

---

### Post by xjgnsdof on 2007-08-17
one week of no responses? so this is the Linux community?

---

### Post by Ozor Mox on 2007-08-17
I should think it's pretty obvious why this doesn't work. I also have a wireless printer, but from Ubuntu I can only print through a USB cable because the drivers on the CD-ROM that enable wireless printing are made for Windows only (as usual) and, as of yet as far as I know, no one has created an open source driver that can do the same thing in Linux, at least for my particular printer (also HP).

---

### Post by xjgnsdof on 2007-08-17
There's a Linux driver for the HP Deskjet 6980, but I need the installation software to load because it will configure wireless access. Is there a way to emulate the installation? I've tried WINE to no avail.

---

### Post by Ozor Mox on 2007-08-17
I'm not very knowledgeable when it comes to Wine, but I'm not sure that even if you got the setup program running in Wine that it would work because it is for configuration of the Windows driver that HP include, not the Linux driver. I could be wrong on this however.

---

