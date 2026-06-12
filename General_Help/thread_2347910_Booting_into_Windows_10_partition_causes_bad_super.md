---
title: "Booting into Windows 10 partition causes bad superblock."
date: 2016-12-29
forum: General Help
---

### Post by nonbeing2 on 2016-12-29
Hi, sorry if this has been answered other places. I tried googling this and using the forums' search, but there was simply too much to sort through.

I am dual-booting Ubuntu Gnome 16.10 and Windows 10. They are installed on two separate partitions (ext4 and ntfs respectively) on a single SSD. Fast boot is disabled in the Windows settings, since from what I have heard this can cause problems for Linux. IIRC, my motherboard has a UEFI but Ubuntu was installed in BIOS compatibility mode as suggested by the installer. I have updated grub through the terminal several times since installing, but it has not affected the problem I'll describe here.

So basically, after using the Windows partition, and then booting into Ubuntu, the Ubuntu Gnome logo will appear and spin as usual, but then instead of showing me the login screen it will drop to "Busybox (intramfs)" or something along those lines, and I can't switch to tty3 or anything. Now, the first time this happened, I did solve it by finding this thread: [https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox). According to that, this is due to a bad superblock. I have followed the instructions in the top reply on that thread (use a live system to repair the file system with an alternate superblock) and so far it has worked every time. However, I would like to know how to stop it from happening in the first place. Does anybody know the cause of this problem and what I can do to avoid it in the future?

---

### Post by Mark Phelps on 2016-12-29
This is most likely because Win10 enables a new form of hibernation by DEFAULT known as Fast Startup.  This is NOT to be confused with FastBoot -- which is different.

With this new hibernation, the Windows filesystems REMAIN mounted, even when Windows is not running.  This, of course,will prevent you from trying to mount them again using your Linux distro.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

### Post by Bucky Ball on 2016-12-29
... or it could be because you installed Ubuntu in BIOS mode and Windows 10 is almost definitely installed in UEFI. You can't have both. Ubuntu should be installed in whatever mode you have installed Windows in.

So, everything works as it should after you have run that fix every time?

There's also a lot of info on how to recover from a bad superblock. [Here's an example]("https://ubuntuforums.org/showthread.php?t=1245536"). A search for 'bad superblock' will find dozens more. ;)

---

### Post by nonbeing2 on 2016-12-30
> **Mark Phelps said:**
> This is most likely because Win10 enables a new form of hibernation by DEFAULT known as Fast Startup.  This is NOT to be confused with FastBoot -- which is different.

Oh whoops, looks like I used the wrong terminology. I meant to say I had already disabled fast startup (from the power options).

> ... or it could be because you installed Ubuntu in BIOS mode and Windows  10 is almost definitely installed in UEFI. You can't have both. Ubuntu  should be installed in whatever mode you have installed Windows in.

That could be the culprit. But when I first installed Ubuntu after building this PC and installing Windows 10 first, the installer told me that it detected that another operating system was already installed on the machine in BIOS compatibility mode, and that if I installed in UEFI mode then I wouldn't be able to access the other OS. It's given me the same notification every time I've reinstalled. I assumed this referred to Windows, though I did think it was strange that Windows 10 wouldn't take advantage of UEFI. After reading your post, I did some searching and found this thread about seeing whether Win10 is in UEFI mode: [https://superuser.com/questions/946868/how-to-test-whether-windows-10-was-installed-with-uefi](https://superuser.com/questions/946868/how-to-test-whether-windows-10-was-installed-with-uefi). Following it's instructions, I see that "BIOS mode" in sys info says "Legacy" and disk manager does not show an EFI system partition as far as I can see. This suggests that it really is in BIOS mode for some reason, though I have no idea why since I don't remember telling it to do that during installation, and this is a brand-new motherboard (MSI B150M Mortar) that's advertised as having UEFI according to MSI's site. So I'm not quite sure what's going on here really.

Edit: Also, I will say that I haven't yet repaired the latest superblock issue, since I'm going to be using Windows regularly for the next few days and there would be no point in fixing it until I know how to stop it from breaking again. But there's nothing at the moment to suggest the solution I linked in the OP won't work like last time.

Edit 2: Someone outside this forum suggested that the bios mode thing could be because uefi is not enabled in the uefi's own menu. I checked the settings in said menu, and there were two modes: one to use either legacy mode or uefi mode depending on the OS's needs, and another to force UEFI. The first was enabled, but it's not like uefi was disabled or anything.

[U][B]
Final edit, 2/28/2017:[/B][/U]

Just wanted to update this for the benefit of anyone who might have had the same problem without necroing the whole thread. This problem was caused by my own noob mistake when I first set up my computer. I used gparted to partition my drive *before* installing any OSes. Gparted used a partition table that wasn't particularly compatible with Windows 10. Win 10 did install, but in an imperfect way that caused it to be installed in legacy mode. So what I did was clean install Windows 10, let it wipe everything and do a default install, then change the partitions *afterward* during the Ubuntu installation. In the process I realized the mistake I made last time. Now both OSes are running in UEFI mode and this problem has been resolved.

---

### Post by oldfred on 2016-12-30
Both Windows & Ubuntu install in the mode you select to boot install media, UEFI or BIOS/CSM/Legacy.
And that mode may not be the same mode you have set as default boot mode for internal system.

With installer, in UEFI you should see two boot options if you have UEFI Secure boot off. With Secure Boot on, you may not have any boot options, unless you specifically turn on allow USB bot. 
One is "UEFI:flash" and other just "flash" for BIOS. Where flash is name, brand or label on flash drive installer.

UEFI & BIOS are not really compatible. Once you start booting in one mode you cannot switch. Or with systems in different boot modes, you can only choose dual booting from UEFI boot menu.

---

