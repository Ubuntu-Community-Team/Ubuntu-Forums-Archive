---
title: "Install Ubuntu along side Windows 8"
date: 2013-04-27
forum: General Help
---

### Post by tomharto on 2013-04-27
I've got a spare hard drive which I want to install Ubuntu and Windows 8 on to get to know the systems a little better. What would be the best way of going about doing this?

---

### Post by oldfred on 2013-04-27
What system do you have? Or specifically are you booting with BIOS or UEFI as that makes a huge difference.

If BIOS then it is similar to all the dual boot installs, but you do need to turn off fast boot in Windows 8 and make sure it is not hibernating. It will otherwise cause issues.

Install Windows first and change BIOS to boot that drive so it keeps its boot loader on that drive. If not partitioned in advance then use Windows to shrink the Windows partition, but do not create any additional partitions and reboot so it can make repairs for its new size.

       [URL="https://help.ubuntu.com/community/WindowsDualBoot"]https://help.ubuntu.com/community/WindowsDualBoot
[/URL]
 [URL="https://help.ubuntu.com/community/GraphicalInstall"]https://help.ubuntu.com/community/GraphicalInstall

      [/URL]
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

    [URL="https://help.ubuntu.com/community/GraphicalInstall"]
[/URL]

[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

---

### Post by tomharto on 2013-04-27
I'm currently running Windows 7. I've no idea about any BIOS or UEFI settings I'm afraid I'm not good with that kinda computer stuff. If you let me know what BIOS settings I need to find out I'll go look for them now.

---

### Post by oldfred on 2013-04-27
Only a few Windows 7 systems released before Windows 8 had UEFI. Most are BIOS and then have the 4 MBR(msdos) primary partition limit.
If drive is gpt then you have UEFI, if it says msdos then you have BIOS, but some newer systems have Windows in BIOS mode, but have UEFI/BIOS on the motherboard.
Post this
  sudo parted /dev/sda unit s print

A second install of Windows will want to put its boot files into the first install. As Windows only can boot from one active partition. But if you change BIOS to second drive it should install its boot files into that drive.

---

### Post by tomharto on 2013-04-27
Wow that sounds confusing, I might be better taking it to my local PC shop get them to do it, I don't wanna mess up my current Windows install.

---

