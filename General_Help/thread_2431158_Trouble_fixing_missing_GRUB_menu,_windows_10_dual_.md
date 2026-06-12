---
title: "Trouble fixing missing GRUB menu, windows 10 dual boot"
date: 2019-11-12
forum: General Help
---

### Post by ggaug on 2019-11-12
I am running Windows 10 home on a Lenovo laptop with a 1 TB Samsung SSD and a 128 GB Toshiba NVMe SSD. About five months ago I installed dual boot Ubuntu onto the Toshiba - there is nothing else on there except for Ubuntu, and there is nothing but windows on the Samsung. I configured the boot order so that the GRUB menu would be the one that pops up first when I boot my laptop.

About a month ago I came back from a trip and booted up my laptop to find that the GRUB menu had disappeared - it booted straight into windows. I think this is due to the fact that I had enabled automatic updates for Windows 10 which may have caused this problem. After trying a bunch of different solutions I saw on this forum and others I wanted to make a post asking for help.

When I go into my BIOS and boot menu Ubuntu no longer shows up. It is not showing up on EasyBCD either. Today I found some software that recognized my linux partition, so I backed up everything from my toshiba SSD. To do this I did method 2 from this [[https://www.eassos.com/blog/how-to-backup-ubuntu-partition/](https://www.eassos.com/blog/how-to-backup-ubuntu-partition/)]. It finished backing up the partition but in the error box I got the following messages:

> Read disk error: "Data error (cyclic redundancy check).  
Note: Error has been omitted. The backup file will have errors.  
Read disk error: "Data error (cyclic redundancy check).  
Note: Error has been omitted. The backup file will have errors.  

I downloaded Ubuntu onto a USB drive to try using the boot repair tool. When I tried doing so, after 40 minutes the program hung on saying 

> Unhide boot menu. This may require several minutes...

For the first 20 or so minutes the progress bar kept sliding back and forth, for the last 20 or so the progress bar was simply frozen.

At this point I know I could just do a clean install of Ubuntu and restore my backup, but the error messages I got after backing up are making me nervous - I'd really prefer to just get everything working again

Has anyone ever been in a similar situation or have any advice?

---

