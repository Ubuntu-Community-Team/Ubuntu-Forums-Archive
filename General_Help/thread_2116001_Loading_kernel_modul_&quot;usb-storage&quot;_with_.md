---
title: "Loading kernel modul &quot;usb-storage&quot; with options not working during boot"
date: 2013-02-14
forum: General Help
---

### Post by orloff34 on 2013-02-14
Hi,

I am using Ubuntu 12.04 (32 bit with unity) and I encountered following problem: I would like to force MTP mode for my mp3 player (Sony Walkman NWZ-S545, VId = 054c, PId = 03fe). This player supports MSC mode as well. For that reason UBUNTU mounts this player as USB mass storage what causes problems whwn copying media files with nautilus.

Following the instructions found on [anythingbutipod.com]("http://anythingbutipod.com/forum/showthread.php?t=49138") I created a file usb-storage.conf in the folder /etc/modprobe.d:

```
#sets the kernel usb-storage module to ignore a Sony NWZ-S54x player
#http://anythingbutipod.com/forum/showthread.php?t=49138 
options usb-storage quirks=054c:03fe:i

```The test with **sudo rmmod usb-storage** and **sudo modprobe usb-storage** was successful and the mp3 player was in MTP mode after plugging in. I could mount the player with

```
sudo mtpfs -o allow_other /media/Walkman
```and I could copy files on the device using nautilus. I also could unmount it with 

```
sudo umount /media/Walkman
``` But after rebooting the system the kernel modul is loaded without the options given in usb-storage.conf. The mp3 player is still detected as USB mass storage and auto-mounted after plugging in. I can force the MTP mode again by repeating the above procedure.

What is going wrong during booting the system? Why is the kernel modul loaded without the options given with /etc/modprobe.d/usb-storage.conf on system boot?

Kind regards
orloff34

---

### Post by orloff34 on 2013-02-20
I am actually using the latest  version of gvfs MTP  Backend  available on [https://launchpad.net/~langdalepl/+archive/gvfs-mtp](https://launchpad.net/~langdalepl/+archive/gvfs-mtp) which is solving all my issues.

---

