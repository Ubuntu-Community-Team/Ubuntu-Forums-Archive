---
title: "problems adding second hard drive"
date: 2007-05-26
forum: General Help
---

### Post by diablofish on 2007-05-26
After searching these (and other) forums, I was able to mount and see my second internal hard drive.  I'm running Feisty Fawn.

I can see the HD (called "disk" on the desktop), but I can't read or write to it.  For example, I'm trying to copy files from the primary hard drive over to the second hard drive, but the Paste command is ghosted when I try to use it.

When I type "mount" in the terminal, here's what I get:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb5 on /media/disk type ext3 (rw,noexec,nosuid,nodev)


I think sdb5 is the second hard drive, but I'm not familiar with what the rest of it means.

Any help is appreciated.

---

### Post by taurus on 2007-05-26
Try to change the ownership of /media/disk from root to your login name so you can write to it.

```
sudo chown -R **username**:**username** /media/disk
ls -la /media
```
Replace **username** with your actual login name.

---

### Post by diablofish on 2007-05-26
Taurus,

Thanks for the tip.  I tried doing that and nothing changed. 

More information:

In the File Browser, I can see and navigate to a "232.9 GB volume disk".  WHen I righ-click and pull up properties and navigate to the "permissions" tab, it lists Owner as "unknown" and says permission is Read-Only in each of the boxes.

Is there another way to change the owner of the drive?

---

### Post by taurus on 2007-05-26
How did you mount /dev/sdb5?  Did you mount it by hand or through /etc/fstab?

Can you post the output of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
id
```

---

### Post by diablofish on 2007-05-26
Taurus,

Somewhat sheepishly I must admit that I did not restart once I ran that command.  After a restart, I am able to access the drive normally.

Thank you for your help.

---

