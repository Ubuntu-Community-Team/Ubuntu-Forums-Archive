---
title: "No signal on boot until the welcome screen on windows"
date: 2014-06-30
forum: General Help
---

### Post by alley2 on 2014-06-30
Hi, this problem started after i installed Ubuntu on my PC with hopes to dual booting. However, after i restarted my computer after boot-repair gave me an error I can no longer access bios, boot from a usb or cd or dvd, or get into Linux.
Go ahead and ask questions, cause i know i'd probably miss a few things.
Cheers!

---

### Post by yancek on 2014-06-30
What might that error be from boot repair?  Why did you run boot-repair?  Were you ever able to successfully boot the installed Ubuntu system?  Installing Ubuntu or any Linux system has no effect on your BIOS nor does it change anything there nor should it prevent booting from a CD/DVD/flash drive.  Do you change the boot priority in the BIOS before trying to boot a CD/DVD/flash drive?

You indicate you wanted to dual-boot but neglected to mention with what.  The other operating system or systems you have are what?  From your post title, you seem to boot into windows??.  So is the problem that you can no longer boot Ubuntu but can boot windows (and which windows).  Where did you run 'boot-repair' from?  A CD, Ubuntu??

---

### Post by alley2 on 2014-06-30
Im not sure what the error was about nor can i find it. I ran boot repair because grub wasnt showing to choose os' , it just booted straight into windows ( the os im trying to dual boot with). I ran boot repair from the same cd i installed ubuntu with. No, i never managed to boot fully into ubuntu.

---

### Post by yancek on 2014-06-30
You still have not indicated which windows version you are using.  If you are using windows 8 or 8.1 it involves a whole different scenario for booting.

---

### Post by alley2 on 2014-07-01
windows 8

---

### Post by yancek on 2014-07-01
Windows 8 uses uefi rather than a regular BIOS.  Ubuntu can be booted with uefi.  Windows 8 requires 'Secure boot' in the BIOS being disabled and also Fastboot.  I don't have any experience with uefi so won't offer any other advice.  I have seen a number of posts here at the forum regarding problems with uefi so you might try using the Search function at the top right of the page or, wait for someone with a little more knowledge to respond.

---

