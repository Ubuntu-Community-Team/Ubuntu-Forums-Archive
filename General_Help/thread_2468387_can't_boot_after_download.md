---
title: "can't boot after download"
date: 2021-10-27
forum: General Help
---

### Post by headmuirdunc on 2021-10-27
At home I took delivery of a pc with ubuntu installed. It was working fine, until the system said it wanted to download some more recent software. I agreed and went out. When I came back the system said it wanted to restart. I agreed. Alas that was the last thing the computer did. It came back to a black screen. After a while I cyceld the power, but the same result -- black screen. I came into work (where I am now) in the hope that I could find out what I can do.

---

### Post by headmuirdunc on 2021-10-27
Sorry, I'm new here, indeed to forums generally. How can I find " [CENTER][COLOR=#C61919]appropriate support sub-forum" ?

[/COLOR][/CENTER]

---

### Post by QIII on 2021-10-27
In the upper left corner, click on "Forum".  This will display all the categories.

This would be best in the General Help sub-forum, so I have moved it there.

---

### Post by grahammechanical on 2021-10-27
I assume that Ubuntu is the only operating system on that machine. I also assume that as you recently took delivery of the machine it has a UEFI motherboard and not a BIOS motherboard. You may not know it but there is a boot menu (Grub) that only appears naturally when there is more than one OS installed. To bring up this boot menu when only one OS is installed you need to press the ESC key perhaps several times when the manufacturers splash screen is showing.

> With  BIOS, quickly press and hold the Shift key, which will bring up the GNU  GRUB menu. (If you see the Ubuntu logo, you've missed the point where  you can enter the GRUB menu.) With UEFI press (perhaps several times)  the Escape key to get grub menu. Select the line which starts with  "Advanced options".

When the Grub menu appears select Advanced Options for Ubuntu. There you will see a list of Linux kernels. The first one on the list is the kernel you are at present booking and getting a black screen. There will certainly been another kernel listed as being recovery mode. Select that.

When the recovery menu appears you have options. Resume will load Ubuntu using a low resolution open source video driver. Or, it may load to a black screen. If that happens select network. That will establish an internet connection. Then select Root - Drop to a root shell prompt. Then run at least these two commands.

```
apt update
apt upgrade
```

Pay attention to any error messages. They will be useful to us. If the error messages are about missing or broken packages you can also run these commands

```
apt --fix-missing update
apt install -f
```

When this is done type exit to get back to the recovery menu. And select Resume again. If things seem to be working fine a reboot should load Ubuntu with a high resolution video driver.

Regards

---

### Post by HermanAB on 2021-10-30
If you are very new to Linux, find a local Linux user group and go to a meeting to find someone that can fix it for you.

In general, an update has to be earned.  There has to be a good reason to do it.   If a machine is working properly, then an update won’t make it better - it will either be the same (with a few minor security issues fixed), or worse (like in this case - unusable), after the update.  YMMV…

---

### Post by yancek on 2021-11-29
The OP hasn't been back for 4 weeks so I imagine s/he has either resolved the problem or moved on..

The windows bootloader since vista is BCD, managed with bcdedit.  Not sure what 'winboot' is unless the link below describes it, malware? 

[https://www.bleepingcomputer.com/startups/winboot.exe-22457.html](https://www.bleepingcomputer.com/startups/winboot.exe-22457.html)

Also, it is generally not a good idea to have any Linux system on a windows filesystem partition such as vfat or ntfs.  vfat (FAT32) partitions can and are used for UEFI partition and for 'live' systems and a Linux iso or extracted iso can be put on a partition of any filesystem (including ntfs) but an actual install to an ntfs/vfat filesystem is a bad idea. .

---

