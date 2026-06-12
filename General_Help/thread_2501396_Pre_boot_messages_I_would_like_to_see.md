---
title: "Pre boot messages I would like to see"
date: 2024-10-05
forum: General Help
---

### Post by georgesgiralt on 2024-10-05
Hello,
The culprit is a laptop running Ubuntu 24.04.I after upgrade to Noble. 
Secure boot is turned ON and it has dual boot with Windows 11.
Since the upgrade, when I select Ubuntu in the Grub menu, there are 3 lines of messages displayed a few milliseconds before the splash screen is displayed. 
All I could read is "EFI Stub ........"
I've tried to remove the "quiet splash" options on the Linux Grub line but, the messages are not anymore readable. 
So my question is, as these messages are displayed BEFORE the kernel get invoked/loaded, how could I see them for more than a few short time before they vanish and are there ways to log them somewhere ? 
Thank you very much for your help. 
Have a nice and bright day. 
P.S.:  If I remember correctly, before the upgrade, there was only one line of messages displayed here. But I'm not even sure there was something at all.

---

### Post by yancek on 2024-10-05
Had you been successfully booting an earlier version of Ubuntu before this upgrade?  You have not indicated if your current Ubuntu boots successfully?  Log files are in the /var/log directory and some of them require root permissions to access.  Look for /var/log/boot.log file or /var/log/dmesg

---

### Post by georgesgiralt on 2024-10-05
Hello Yancek,
Thank you for your answer.
Yes the laptop was booting and running fine before (and after) the upgrade. 
There is nothing pertaining to these messages in any log I can look at in /var/log. My bet is that it is because they appear before the kernel get loaded.

---

### Post by grahammechanical on 2024-10-05
Once we select a boot option in the Grub menu then Grub loads that operating system. The messages you see are from Linux. That is why doing this does not work

> I've tried to remove the "quiet splash" options on the Linux Grub line but, the messages are not anymore readable.

Ubuntu is running in a Linux terminal. When we power off Ubuntu the OS hands back control to Linux to shutdown. We see a black screen that most likely still shows those Linux messages. A second opportunity. They usually are messages about a file system check.

Depending on the version of Ubuntu we may see a message about the TPM. You are not running Ubuntu, are you? Tell us what Linux distribution you are using and someone here might have knowledge of messages put on screen by that distribution's Linux kernel.

Regards

---

### Post by georgesgiralt on 2024-10-05
Hello grahammechanical,
As I wrote in my first post, I run Ubuntu 24.04.1 LTS.
The messages I see arose BEFORE the first kernel message, so before the kernel is loaded/started. 
I removed the splash screen in the hope that, as the screen is not cleared as when switching to graphics mode, the message would stay on the screen. But I was mistaken ;-) 
Do anyone of you know how to get the Grub messages and log them somewhere ?

---

### Post by oldfred on 2024-10-05
Probably not important.
You can use camera in video mode to capture output.

Reporting  file system clean which just a message saying everything is ok. Or no fsck required.
And reporting some other settings which if you can boot are not critical.
Some UEFI settings are needed for virtual installs, secure boot, or drive settings, but otherwise not required.

---

### Post by grahammechanical on 2024-10-05
Thank you and sorry. Things are a bit clearer. I have found this:

> An **EFI boot stub** (aka **EFI stub**) is a kernel that is an EFI executable, i.e. that can directly be booted from the UEFI.

I got it from here:

[https://wiki.archlinux.org/title/EFI_boot_stub](https://wiki.archlinux.org/title/EFI_boot_stub)

And this:

[https://wiki.ubuntu.com/EFIBootLoaders](https://wiki.ubuntu.com/EFIBootLoaders)

> Linux kernels since v3.3.0 are bootable via system firmware; no bootloader needed

Why are you getting that message? I am guessing that it is because of some setting in the UEFI settings utility. Perhaps the boot priority has check for EFI stub first and look for boot loader on disk next.

Regards

---

### Post by georgesgiralt on 2024-10-05
So OldFred had a nice and fine idea.
I used a camera set to video and recorded the messages. 
They read : ```

EFI Stub: loaded initrd from LINUX_EFI_INITRD_MEDIA_GUID device path
EFI Stub : Measured initrd data into PCR 9
EFI Stub: UEFI Secure Boot is enabled

```
The last one was displayed when booting the previous Ubuntu version. 
The first one is an information explaining where it get it's initrd file. 
The second line, though, puzzle me. What is it and what does that mean ? 

I've done the same on 3 other computer I own, running Ubuntu (2 on 22.04, one on 24.04). The 22.04 show the first line and the last line. The 22.04 computer show only the third line. 
So definitely something has changed on Grub verbosity or messaging ... 
Have a nice day !

---

### Post by georgesgiralt on 2024-10-05
So OldFred had a nice and fine idea.
I used a camera set to video and recorded the messages. 
They read : ```

EFI Stub: loaded initrd from LINUX_EFI_INITRD_MEDIA_GUID device path
EFI Stub : Measured initrd data into PCR 9
EFI Stub: UEFI Secure Boot is enabled

```
The last one was displayed when booting the previous Ubuntu version. 
The first one is an information explaining where it get it's initrd file. 
The second line, though, puzzle me. What is it and what does that mean ? 

I've done the same on 3 other computer I own, running Ubuntu (2 on 22.04, one on 24.04). The 24.04 show the first line and the last line. The 22.04 computer show only the third line. 
So definitely something has changed on Grub verbosity or messaging ... 
Have a nice day !

---

