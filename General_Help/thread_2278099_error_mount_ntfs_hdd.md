---
title: "error mount ntfs hdd"
date: 2015-05-13
forum: General Help
---

### Post by minh_nguyen2 on 2015-05-13
Hello everyone,
I get this error,
"Error mounting /dev/sda2 at /media/minhnh/DATA: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/minhnh/DATA"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
"
Can anyone help me out!!
Thanks in advanced

---

### Post by coffeecat on 2015-05-14
Not an Ubuntu, Linux and OS Chat thread.

*Thread moved to **General Help**.*

The error message tells you why Ubuntu will not mount that partition read-write. There is metadata in the Windows cache. Possible reasons are that you hibernated Windows before booting into Ubuntu, or that if you are running Windows 8 you have not disabled fast start. Tell us more about your system, which version of Windows you are using and people will be able to help you.

---

### Post by minh_nguyen2 on 2015-05-14
Yup,
I installing Ubuntu 14.04 LTS after restart in Windows 8.1,
Because it very important file in DATA driver so I cannot format it but too lazy to take HDD out,
so any solutions else???

---

### Post by coffeecat on 2015-05-14
You need to disable fast startup in Windows 8:

[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

The problem with fast startup in Windows 8 is that it relies on a partial hibernation for shutdown. 

After you have made those settings in Windows 8, always choose shutdown before restarting the machine with Ubuntu. If you choose restart in Windows and reboot into Ubuntu you will see the same problem. This can occur when Windows updates are applied and the system prompts you to restart.

---

