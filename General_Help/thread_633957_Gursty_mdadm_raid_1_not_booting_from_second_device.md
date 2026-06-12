---
title: "Gursty: mdadm raid 1 not booting from second device"
date: 2007-12-07
forum: General Help
---

### Post by z0mbi3 on 2007-12-07
Hoping some one can help me out with this.

I'm trying to get raid 1 working but not having much joy at all.

Basically I have everything syncing and seemingly working correctly with grub installed to the MBR on both drives, however when I fake a drive failure I'm running into problems.

If I unplug the first drive in the array and restart the PC, I eventually get the folowing:

```

Starting up ...
Loading, please wait...
stdin: error 0
kinit: name_to_dev_t(/dev/md1) = md1(9,1)
kinit: trying to resume from /dev/md1)
[207.997551] Read-error on swap-device (9:1:8)
kinit: No resume image, doing normal boot
Usage: modprobe [-v] [-V] followed by some stuff suggesting modprobe isn't being used correctly.
mount: cannot read /etc/fstab: No such file or directory
<A string of errors stating no such file or directory>
Target Filesystem doesn't have /sbin/init
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```


I setup softraid using [this]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") guide and as I say it all appears to work correctly until I'm actually under failure conditions.

Can anyone please help?

edit:

Gursty lol, too early.

---

### Post by frankabel on 2007-12-18
See this post [http://ubuntuforums.org/showthread.php?p=3976466#post3976466](http://ubuntuforums.org/showthread.php?p=3976466#post3976466)

I have the same error few time after install, but don't seen due to a disk problem because I don't unplug the disk because I can't :)

The system now is working well, and just add that the error is at boot time, I see it with dmesg | grep swap after boot.

Salute
Frank Abel

---

### Post by frankabel on 2007-12-19
After lots of reboot I realize that problem raise random, I saw a solution at [http://hodza.net/2007/07/25/no-devices-listed-in-conf-file-were-found-ubuntu-704/](http://hodza.net/2007/07/25/no-devices-listed-in-conf-file-were-found-ubuntu-704/) that work for me

Salute
Frank Abel

---

