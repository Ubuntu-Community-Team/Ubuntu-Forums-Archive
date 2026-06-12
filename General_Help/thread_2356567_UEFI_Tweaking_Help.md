---
title: "UEFI Tweaking Help"
date: 2017-03-24
forum: General Help
---

### Post by semonski on 2017-03-24
Hello,

I've (finally) successfully installed a dual boot system with Windows 10 & Ubuntu 16.04 LTS.  Basic HW description is Dell Alienware 15 R2, 16 GB RAM, 1TB M.2 SSD (d0), 256GB M.2 SSD (d1),  1TB SATA SSD (d2)

d0 contains Windows 10 along with the EIF partition
d1 formatted NTFS (used for shared storage between OS's)
d2 partitioned to 200GB for Ubuntu OS, 700GB (/home), and 18GB SWAP   
NOTE: there is NO BOOT partition at all on this Ubuntu Drive  (could be trouble later, but I've been trying many different variations and this one seems to work)

Ubuntu EFI installed "alongside of windows"

Machine BIOS recognizes 2 UEIF boot options (Windows & Ubuntu)

Here is the problem:

IF I set the default boot to Ubuntu, the system ALWAYS drops to a Grub Prompt instead of the GRUB boot menu
IF I boot to Windows, then reboot to Ubuntu, it works (finds the Grub Boot Menu) MOST OF THE TIME
IF I set the first boot option to IPv4 Network boot, the system attempts a net boot for about a minute, then cascades to the next option (UBUNTU) and GRUB ALWAYS works as expected.

My assumptions:

This is a race / timing issue.  The system is booting too fast ( who would think this to be a problem <SMILE>).
Grub is looking for the OS before the partition is available / on-line.

The challenges:
I see no particular way to increase the boot time in the BIOS (e.g. verbose boot mode, memory test, etc.).

My thoughts on mitigation / remediation:

edit the UEIF boot scripts (?) to force a delay before the system looks for the boot / OS partitions.

My ASK:

Does anybody know IF it is possible to delay the boot process via the UEIF script (?) files?
IF it is, can anybody suggest the proper syntax and file path / name in which to apply these edits?
IF it is, and the edits are applied, what "other" possible issues may be caused / experienced with the edit?

Kos

---

### Post by oldfred on 2017-03-24
If all are SSD, I do not think you have a timing issue.
I normally boot SSD with Ubuntu, but have installed Ubuntu several times on HDD and it boots without issue.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Which version of 16.04? I have original and it still is 4.4 kernel. But 16.04.2 has newer kernel.
This may may apply?

 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

### Post by semonski on 2017-03-24
Thanks for getting back to me....

As for the timing, I'm open to any help you can render, but the only thing that seems to work faithfully, is causing the machine to "take a breath" before booting...

here is the link to the Boot-Repair log.

[http://pastebin.com/GV5QSWhW](http://pastebin.com/GV5QSWhW)



Thanks,

Kos

---

### Post by oldfred on 2017-03-25
I do not see anything that stands out.
Do not know specifically how to delay UEFI boot process. My system has Fast Boot setting that controls UEFI loading but not then grub/ubuntu on SSD/HDDs.

---

### Post by rbmorse on 2017-03-25
you want this:

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

but, as always, read the docs first.

---

### Post by oldfred on 2017-03-26
A lot of users particularly Mac as it was first with EFI have used rEFInd.
I have not tried it yet with my PC, but plan to.

---

### Post by semonski on 2017-03-29
UPDATE:

Got tired of the "weirdness" of the shared UEIF installation and simply created separate volumes for the Windows and Linux OS's, each with their own EFI partition.  From there, I'm just using the machines Boot Manager (F12) to select Ubuntu or Windows.  So far, all is well...

Kos

---

