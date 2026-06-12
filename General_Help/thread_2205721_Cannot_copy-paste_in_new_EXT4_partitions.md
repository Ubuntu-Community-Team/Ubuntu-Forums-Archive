---
title: "Cannot copy-paste in new EXT4 partitions"
date: 2014-02-15
forum: General Help
---

### Post by lymphor on 2014-02-15
Hi,

I'm using **Ubuntu 12.04 32bit** and I just upgraded my PC with a new HDD. Therefore I have 2 new EXT4 partitions (900 GB and 650 GB). The thing is that I cannot copy-paste anything into them, unless I access **Nautilus** via terminal (I use the command "**sudo nautilus**"). I don't know if it matters but when I check the **properties** of the partitions, in the **Permissions** tab it is written: "**You are not the owner, so you cannot change these permissions**". If I convert the partitions to NTFS it's all fine, but I would like them to be EXT4. Could you please help me? :)

Thank you,
Alex

---

### Post by oldos2er on 2014-02-15
You can take ownership of an ext4 partition with ```
sudo chown -R user:user /media/sdb2/
``` You'll need to change "user" to your user name and the mount point to wherever the partition's mounted.

---

### Post by ajgreeny on 2014-02-15
To avoid confusion I suggest you use gparted to give a meaningful label to the partition on this new disk as it will then mount to that named folder in /media/*user*/label.

Just my opinion, but I recall partitions mounting to **/media/0707fdc8-1299-4c11-9f93-8158d3c313d0** (ie the UUID of the partition) in previous systems I ran

---

### Post by lymphor on 2014-02-16
**@oldos2er**: thank you very much, that did the trick! Now everything is fine :)
**@ajgreeny**: thank you also, yours is a very good tip. In my case the partitions were already labelled, so it was easy :D

---

### Post by lymphor on 2014-03-01
Hi all,
I have recently installed **Storage Device Manager** in order to have all HDD's boot at startup. But after this operation I again cannot copy anything on certain HDD's. I have tried to use the command you suggested (**sudo chown -R user:user /media/sdb2/**) but I get the answer "**Read-only file system**". The full reply in the terminal is:

[B]chown: changing ownership of `/media/Usa/$RECYCLE.BIN/S-1-5-21-1569345450-1471465237-1804068876-1000/desktop.ini': Read-only file system
chown: changing ownership of `/media/Usa/$RECYCLE.BIN/S-1-5-21-1569345450-1471465237-1804068876-1000': Read-only file system
chown: changing ownership of `/media/Usa/$RECYCLE.BIN': Read-only file system
chown: changing ownership of `/media/Usa/System Volume Information/tracking.log': Read-only file system
chown: changing ownership of `/media/Usa/System Volume Information': Read-only file system
chown: changing ownership of `/media/Usa': Read-only file system
[/B]
Could you please help me once again? :)
Thank you!

---

### Post by oldos2er on 2014-03-01
What's the exact package name, and/or executable name? The closest thing I can find is system-storage-manager, which I've never used.

If you're talking about pysdm, don't use it. It's quite buggy and hasn't been updated in a long time (I'm not even sure it was ever updated to work with ext4).

---

### Post by ortermagic on 2014-03-02
For what it's worth,
I had the same problem and found it too difficult to resolve so I copied the files i wanted to transfer on to a 32gb flash drive, then simply transerred them to the empty drive (it's not exactly empty since it has a pristine 14.04 waiting for the tweakin)I just copied into the home folder in the new install, and it worked, I had transferred and gained read and write status.
wasn't too difficult, maybe a bit long winded,but it worked.

---

### Post by lymphor on 2014-03-02
**@Ann (oldos2er)**: the package name is indeed **pysdm**. I uninstalled it and tried again to gain ownership of my partition, but the result is the same as before, I still get the message "**Read-only file system**". Is there anything I could do?
**@ortermagic**: thank you, but the data I have to transfer is much bigger than an USB stick. Nevertheless I have tried what you suggested (copy-pasted a file to an USB stick, then into the home folder, then tried to copy-paste it in the target partition) but it didn't work :neutral:

---

### Post by steeldriver on 2014-03-02
Can you open a terminal (Ctrl-Alt-t) and post the out put of the following commands please?

```
cat /etc/fstab
```

and

```
mount
```

You can copy-paste from the terminal by selecting with the mouse and then hitting Ctrl-Shift-c

---

### Post by lymphor on 2014-03-02
**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc  nodev,noexec,nosuid         0  0  
# / was on /dev/sda2 during installation
UUID=fa2329ae-1868-43ee-a4af-df9296462a73  /                ext4  errors=remount-ro           0  1  
# swap was on /dev/sda5 during installation
UUID=dee7c295-3d73-4a5c-9ac5-148946c2f602  none             swap  sw                          0  0  
/dev/fd0                                   /media/floppy0   auto  rw,user,noauto,exec,utf8    0  0  
/dev/sdb6                                  /media/Usa       ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sdc1                                  /media/IDE       ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb1                                  /media/FENICE1   ext4  defaults                    0  0  
/dev/sdb5                                  /media/FENICE2   ext4  defaults                    0  0  
/dev/sda4                                  /media/NTFS      ntfs  defaults                    0  0  
/dev/sdd                                   /media/VERBATIM  ntfs  defaults                    0  0  

**mount**
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb6 on /media/Usa type fuseblk (ro,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/FENICE1 type ext4 (rw)
/dev/sdb5 on /media/FENICE2 type ext4 (rw)
/dev/sda4 on /media/NTFS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd on /media/VERBATIM type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/IDE type fuseblk (ro,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ale/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ale)
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


Thank you :)

---

### Post by steeldriver on 2014-03-02
So /media/Usa is not one of your new ext4 partitions - it is an NTFS partition that is explicitly mounted read-only (ro) - possibly because they are part of a dual-boot Windows system that you don't want to accidentally mess with

Your ext4 partitions appear to be mounted at /media/FENICE1 and /media/FENICE2

```

[B]/dev/sdb6                                  [COLOR=#ff0000]/media/Usa[/COLOR] [COLOR=#ff0000]      ntfs  [/COLOR]nls=iso8859-1,[COLOR=#ff0000]ro[/COLOR],umask=000  0  0  
[/B]/dev/sdc1                                  /media/IDE       ntfs  nls=iso8859-1,ro,umask=000  0  0  
[B]/dev/sdb1                                  /media/FENICE1   ext4  defaults                    0  0  
/dev/sdb5                                  /media/FENICE2   ext4  defaults                    0  0  
[/B]/dev/sda4                                  /media/NTFS      ntfs  defaults                    0  0  
/dev/sdd                                   /media/VERBATIM  ntfs  defaults                    0  0

```

---

### Post by lymphor on 2014-03-02
Yes, but I would like the **NTFS patitions** not to be **read only**. Could this be done?
In any case the **NTFS partition** containing the **Windows OS** is not even mentioned in the list, and is not automounted at boot, so I guess it should be safe :)

---

### Post by lymphor on 2014-03-03
Issue solved, I just modified the **fstab** file as follows:

**/dev/sdb6                                  /media/Usa       ntfs  ****[COLOR=#008000][B]defaults                    0  0**[/COLOR]  
/dev/sdc1                                  /media/IDE       ntfs  [/B]**[COLOR=#008000][B]defaults                    0  0**[/COLOR]  
/dev/sdb1                                  /media/FENICE1   ext4  defaults                    0  0  
/dev/sdb5                                  /media/FENICE2   ext4  defaults                    0  0  
/dev/sda4                                  /media/NTFS      ntfs  defaults                    0  0  
/dev/sdd                                   /media/VERBATIM  ntfs  defaults                    0  0[/B]

Thank you all for your help, bless you! :)

---

