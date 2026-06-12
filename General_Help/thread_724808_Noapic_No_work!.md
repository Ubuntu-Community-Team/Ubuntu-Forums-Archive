---
title: "Noapic No work!"
date: 2008-03-15
forum: General Help
---

### Post by galactus1 on 2008-03-15
My kubuntu crashed.  When booting I get this message:
[HTML]Starting up...
.
Decompressing Linux... done.
booting the kernel.
[   0.000000] ACPI: Unable to locate RSDP
Ubuntu 6.10 username-desktop tty1
username-desktop login:_[/HTML]
 I tried the noapic command on the kennel at the grub menu list but wound up with the same error message.  Any ideas?  
Also: I'm running kubuntu on a partition, windows on a partition, and another storage partition thats fat32 so kubuntu and windows can both read it.  Question: Is it possible to run a fresh install of kubuntu that won't write over my other two partitions? 

I'm still pretty green when it comes to working with linux so you  might have to dumb down your answers.  Thanks!

---

### Post by Shazaam on 2008-03-15
Try these.....

noalpci
acpi=off

---

### Post by Felix-the-Cat on 2008-03-15
IMHO I doubt the fact that acpi doesn't work on your computer is the cause of the crash. I have several computers running fine without acpi at all. First of all , however, what exactly do you mean by "my kubuntu crashed"? Will it boot at all, by the looks of what you have posted it appears that you at least got to a login screen which would mean that kubuntu didn't crash just kdm which is why your aren't seeing a pretty login screen. Before I can say anything for sure we need more info. From what I am inferring from your description and the output that you submittedi would suggest that you try to so sudo /etc/init.d/kdm start. if that doesn't work Copy the output of dmesg and copy /var/log/syslog here.

---

