---
title: "ACPI error, does not boot."
date: 2022-09-30
forum: General Help
---

### Post by dennnic on 2022-09-30
Hi, I'm running dual boot setup with Ubuntu 22.04 and bloody win10 .
After recent update on windows, for some reason I can't boot into Ubuntu anymore.

Acpi error.
Mys device must be supplied.

I've tried editing in advance options, adding acpi=off or strict or whatever, tried reinstalling grub, purging the grub, boot repair stuff (with Kernel set to noacpi) and still stuck.

Is there a way to fix it, without formatting everything?

---

### Post by dennnic on 2022-09-30
Update - I've noticed that my Ubuntu hard drive is over 95% full. Could that be the cause for this error?
On the other hand, I use it just as a system drive. It can't be that filled up and when I mount it in boot repair browser, there isn't anything that could take up that much space. Curious that 50gb free space just disappeared like that.

Could it be something wrong with SSD?

---

### Post by tea for one on 2022-10-01
> **dennnic said:**
> After recent update on windows, for some reason I can't boot into Ubuntu anymore.

Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Check the UEFI setting - Sata mode is AHCI

---

### Post by dennnic on 2022-10-01
Thanks for answering.
Fast boot is still disabled, nothing seems to have changed over there.

---

### Post by tea for one on 2022-10-01
> **dennnic said:**
> Thanks for answering.
Fast boot is still disabled, nothing seems to have changed over there.
There are various speedy boot iterations with similar names:-

Fast Start Up (Widows system setting)
Fast boot (UEFI setting)
fastboot (grub setting to prevent file system check at boot) e.g.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fastboot"
```

I was referring to the Windows setting where you have to disable it within Windows.

---

### Post by dennnic on 2022-10-01
I've checked and disabled fast boot from Windows power settings and added fastboot to quiet splash.
The Ubuntu starting animation appears and goes back to acpi, if no acpi=off is added.

---

### Post by tea for one on 2022-10-01
I wasn't expecting you to add fastboot as a grub parameter.
I was trying to illustrate the variety of settings containing [COLOR="#0000FF"]fast[/COLOR].

Anyway, can you boot into an Ubuntu live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

It may yield some more clues.

---

### Post by dennnic on 2022-11-06
Hi, just to share the rest of the story.
I've reinstalled Ubuntu through it's live cd (amazingly it kept most of the stuff and settings).

However, acpi problem still exists, it's visible every time on boot screen. Ubuntu boots past it and seem to work just fine. I still don't know the reason behind it. 
Hard drive was also full - syslog1 file had increased all the way to 70gb, taking the rest of the available free space.

Thank you for your help,
Stefan

---

