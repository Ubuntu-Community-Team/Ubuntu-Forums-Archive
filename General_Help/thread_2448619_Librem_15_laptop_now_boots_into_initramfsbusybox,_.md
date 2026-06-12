---
title: "Librem 15 laptop now boots into initramfs/busybox, shows no errors"
date: 2020-08-10
forum: General Help
---

### Post by plink1 on 2020-08-10
I've been running Ubuntu-Mate 20.4 for a few months now with no issues, until yesterday.
I noticed that I was at 5% power, so I plugged in the power cord, and then decided to shut down the machine, which I did via the System/Shutdown dialog.
I noticed that it took around 15 seconds or more for the laptop to finally power down, but I saw no error messages.

Now when I try to boot up, I get the GRUB menu screen, and I select Ubuntu. I then see the Ubuntu-MATE prompt for the encrypted disk password. After I enter that I get the BusyBox/initramfs prompt, but with no error messages.
I ran **dmesg** from there, but the output shows all at once, even with the **more** command.  Also, I can't select level for **dmesg**, the only available flag is **c**.
The only **fsck** output I got was for sda5, which showed "clean".  The others return nothing, or "no such file or directory".
I can browse directories, such as usr, bin, etc. so I don't think that the disk is bad.

I am running a memtest86+ now, but it shows no screen information or status at all.  However, I do hear the fan, so I know that some process is running.

Any ideas would be greatly appreciated.

---

### Post by plink1 on 2020-08-10
I decided to re-install Ubuntu, so no need to respond, unless you want to for the general education of Ubuntu users.
Thanks.

---

