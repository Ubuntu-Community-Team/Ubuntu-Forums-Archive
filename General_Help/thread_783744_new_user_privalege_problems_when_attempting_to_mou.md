---
title: "new user: privalege problems when attempting to mount a ntfs disk"
date: 2008-05-06
forum: General Help
---

### Post by jory88 on 2008-05-06
Hey Ive been reading the forums trying to get a solution but so far no luck.

I installed Hardy on my Vista disk (repartitioned the drive)  all works great.  But although I can see my second drive in the file browser window, when I attempt to open it I get the following error message: You are not privileged to mount the volume 'Data Disk'.

After a few more seconds get this message: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I read some posts that suggested: mount -t ntfs-3g /dev/sdb1 /media/Data Disk -o force

And get:  mount: only root can do that

Then tried: sudo mount -t ntfs-3g /dev/sdb1 /media/Data Disk -o force

And get: a long listing of mount commands...

Any suggestions?

---

### Post by amohanty on 2008-05-06
You can try the following:

sudo apt-get install pmount
pmount -t ntfs /dev/sdb windows

this will mount it to /media/Windows. 
If you are using Hardy gvfs should automatically mount this for you and put an icon on the desktop (you might need to set a gconf property). If that does not seem to be the case can you post the output of:

mount -l

HTH
AM

---

### Post by jory88 on 2008-05-06
Hi Am, Thanks for helping out.

I installed and tried the pmount, and get the following...
Error: device /dev/sdb is not removable

As requested here is the mount -l listing:
jory88@Office:~$ mount -l
/dev/sda2 on / type ext2 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/peryn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peryn)
gvfs-fuse-daemon on /home/jory88/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jory88)


Anything else I can try?

Jory

---

### Post by jory88 on 2008-05-08
bump... anybody have any advice for me ?

---

### Post by bodhi.zazen on 2008-05-08
Well, you have a few issues.

First if the partition is not listed in fstab you will need to mount it using sudo.

Second your mount point has a sapce in it,, linux does not like spaces so much.

You need to either quote or escape the space.

sudo mount -t ntfs-3g /dev/sdb1 /media/Data\ Disk

sudo mount -t ntfs-3g /dev/sdb1 "/media/Data Disk"

Third the mount point must exist, make one with :

sudo mkdir "/media/Data Disk"

==========

It may be easier if you use ntfs-config

```
sudo apt-get install ntfs-config
gksu ntfs-config
```

You can do it manually by adding this to /etc/fstab

```
gksu gedit /etc/fstab
```

Add this line :

```
/dev/sdb1 /media/Data\ Disk ntfs-3g auto,users,uid=1000,gid=100,rw 0 0
```

Then you can mount it with :

mount /media/Data\ Disk

---

### Post by jory88 on 2008-05-08
Thanks Bodhi!   I tried the following but as you'll see, no luck.

jory88@Office:~$ sudo mount -t ntfs-3g /dev/sdb1 "/media/Data Disk"
[sudo] password for jory88: 
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Data Disk -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Data Disk ntfs-3g force 0 0
jory88@Office:~$ sudo mkdir "/media/Data Disk"
mkdir: cannot create directory `/media/Data Disk': File exists
jory88@Office:~$ gksu gedit /etc/fstab

jory88@Office:~$ 
jory88@Office:~$ mount/media/Data\ Disk
bash: mount/media/Data Disk: No such file or directory
jory88@Office:~$

---

### Post by bodhi.zazen on 2008-05-08
Ah, yes you need to either boot to windows and let it repair the ntfs file system or use force

```
sudo mount -t ntfs-3g /dev/sdb1 /media/Data\ Disk -o force
```

Your second error message was a typo, there is a space between mount and /media/Data\ Disk

You need to either quote or escape the space ....

"/meida/Data Disk"

or

/media/Data\ Disk

---

### Post by jory88 on 2008-05-08
Bodhi,  WootWoot!!  You're awesome!

Thanks so much the code below worked!

sudo mount -t ntfs-3g /dev/sdb1 /media/Data\ Disk -o force

Cheers!

John

---

### Post by qpieus on 2008-05-08
yep, bodhi's pretty much the king of mounting stuff.
Here's a good how to by him that may interest you:

How to fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

