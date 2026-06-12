---
title: "Wubi with Ubuntu 7.10 on USB Stick ?"
date: 2007-11-13
forum: General Help
---

### Post by Scoty on 2007-11-13
can i install Ubuntu with Wubi on a USB Stick ? or can i install the Boot Option on the USB Stick?

---

### Post by ago on 2007-11-13
> **Scoty said:**
> can i install Ubuntu with Wubi on a USB Stick ? or can i install the Boot Option on the USB Stick?

You should be able to. If the USB stick is to be used as sole linux device, i'd install Linux directly on it, there are some guides on the topic.

---

### Post by ahecht on 2007-11-13
Installing Ubuntu to a USB Stick (or pen drive, or flash drive, or USB key, or whatever you want to call it) isn't that hard. There is a guide at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) that has instructions, but because the guide creates a pen drive that will actually run Ubuntu and save your settings (unlike a Live CD which starts fresh each time), it requires you to use Linux to format your USB stick.

If you just want the Live CD to run off your USB Stick, do the following:

[LIST=1]
[*]**Gather **the following:[LIST]
[*]A USB Stick with 700MB of free space
[*]The latest syslinux zip file (syslinux-3.52.zip as of 9/25/07) unzipped to c:\Syslinux
[*]Either a burned Ubunto LiveCD or:
[LIST][*]A Program installed on your PC that will allow you to mount an ISO image, such as [Daemon Tools]("http://www.daemon-tools.cc/dtcc/download.php?mode=ViewCategory&catid=5") or Nero ImageDrive.
[*]The Ubuntu LiveCD ISO
[/LIST]
[/LIST]
[*]**Copy** the contents of the LiveCD ISO to your USB Stick. If you have a burned CD, use Windows Explorer to copy everything on the CD to your USB stick. If you are using the LiveCD ISO, mount the ISO as a drive (for Daemon Tools, right-click on the DAEMON Tools trayicon, select Virtual CD/DVD-ROM, select drive letter [?:], click Mount, find the Ubuntu ISO, click OK, and a new drive called Ubuntu should appear in My Computer), and then use Windows Explorer to copy everything in that drive to your USB stick.
[*]**Delete** the following from your USB stick:
[LIST]
[*]"bin" folder
[*]"programs" folder
[*]start.exe
[*]start.bmp
[*]start.ini
[*]autorun.inf
[/LIST]
[*]**Move **everything in the "isolinux" directory to the root of the USB Stick except isolinux.bin. Then **delete** the isolinux directory.
[*]**Copy** the following to the root of the USB stick:[LIST]
[*]casper/vmlinuz
[*]casper/initrd.gz
[*]install/mt86plus
[/LIST]
[*]**Rename** the file isolinux.cfg to syslinux.cfg and **open **in WordPad (not NotePad, as it messes up the formatting). **Remove** any instances of "/cd-rom/", "/casper/", or "/install/" using the Replace tool (Ctrl+H) and **save**. Make sure to include the slashes so the "boot=casper" lines remain. I have attached syslinux.cfg for Gutsy below.
[*]**Open** a command prompt, **navigate** to c:\syslinux\win32, and **type**:
syslinux -f X:
Where X is the drive letter of your USB Stick (make sure you get this correct!). **Press** enter.
[/LIST] 

You should be all done!

Gusty syslinux.cfg is attached below. Make sure to rename the syslinux.cfg.txt to just syslinux.cfg (no .txt).

---

### Post by iwilliam on 2008-03-13
Hi,

I have tried following the above steps but using an external hard disk rather than a USB stick - should this work or are the steps different ?. It did not work for me - I get Missing operating system

Ian

---

