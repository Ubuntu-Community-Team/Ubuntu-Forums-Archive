---
title: "Unable to umount encrypted home directory during shutdown: device is busy"
date: 2014-01-04
forum: General Help
---

### Post by wonghang on 2014-01-04
I am using precise LTS (32 bits) and recently upgrade to raring kernel (apt-get install linux-image-generic-lts-raring), my uname -a show:

```
$ uname -aLinux machinename 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:28:45 UTC 2013 i686 i686 i386 GNU/Linux

```

I am using a dmcrypt device on a partition and use it as my home and use pam_mount so that it is mounted automatically when I login (in /etc/security/pam_mount.conf.xml):

```
  
<volume user="myname" fstype="crypt" path="/dev/sda5" mountpoint="/home/myname" options="defaults,noatime" uid="1000" gid="1000" />
<mkmountpoint enable="1" remove="true" />

```

When I shutdown or reboot my computer, the system will wait for a while and finally failed to umount /home/myname saying that device is busy.

I tried to login using lightdm, and then logoff. Switch to another console (Ctrl+Alt+F1), login as root:
Run different command like **lsof**, **fuser**, **ps aux | grep myname** and confirm there is no process opening any file in /home/myname.
I checked also I don't have **nfs-kernel-server**. I also cannot umount /home/myname under this situation. 

How can I resolve it? It is quite annoying for a long time and I just found a lot of errors when I fsck my home directory.

I have a little bit worry there is some rootkit/backdoor in my kernel silently reading my files. :(

---

