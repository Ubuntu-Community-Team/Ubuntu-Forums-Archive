---
title: "ntfs external hard drive problems"
date: 2008-01-12
forum: General Help
---

### Post by xGutsAndGloryx on 2008-01-12
Cannot mount volume.
Unable to mount the volume 'External Hard Drive 1'.

what do i do?

---

### Post by taurus on 2008-01-12
Is your external drive /dev/sdb1?  You can try something like

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
```
You probably get a message saying that you didn't shut down your windows or the drive cleanly so you have to use the force option to mount it.

```
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o force
```

---

### Post by xGutsAndGloryx on 2008-01-12
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo mkdir /media/sdb1
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo mount -t ntfs /dev/sdb1 /media/sdb1
Failed to access '/dev/sdb1': No such file or directory
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o force
Failed to access '/dev/sdb1': No such file or directory
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by taurus on 2008-01-12
Hey, I assume your drive is /dev/sdb1.  You should replace that with the actual one.

```
sudo fdisk -l
```

---

### Post by xGutsAndGloryx on 2008-01-12
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o force
Failed to access '/dev/sdb1': No such file or directory
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by taurus on 2008-01-12
Again, you need to replace /dev/sdb1 with the actual drive, /dev/sda1!

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
```

---

### Post by xGutsAndGloryx on 2008-01-12
i messed the last command up... what do i need to do to unmount it or can i just turn it off?

---

### Post by taurus on 2008-01-12
> **xGutsAndGloryx said:**
> i messed the last command up... what do i need to do to unmount it or can i just turn it off?

Since you don't have /dev/sdb1, it didn't do anything when you tried to mount it so no need to unmount anything.

```
df -h
```

---

### Post by xGutsAndGloryx on 2008-01-12
ok what do i need to do when i am finished using the hard drive. do you i need to unmount it through the command prompt?

---

### Post by taurus on 2008-01-12
Yes, unmount it first before you unplug it.

```
sudo umount /dev/sda1
```

---

