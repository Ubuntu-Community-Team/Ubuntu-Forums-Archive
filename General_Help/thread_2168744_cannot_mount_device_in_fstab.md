---
title: "cannot mount device in fstab"
date: 2013-08-19
forum: General Help
---

### Post by nick20 on 2013-08-19
I have an iSCSI filesystem setup as /dev/sdb1
It currently mounts without error in /srv on boot with fstab

I want to mount it in /var/www/public

I CAN mount it in /var/www/public from command line with

-----------------------------------------------------------------------------------------------------
mount /dev/sdb1 /var/www/public
-----------------------------------------------------------------------------------------------------


but when I try to mount it on startup with fstab I get the following error

-----------------------------------------------------------------------------------------------------
The disk drive for /var/www/public is not ready yet or not present.
-----------------------------------------------------------------------------------------------------


copy of fstab
-----------------------------------------------------------------------------------------------------
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/www-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a27ec59f-3664-4bed-8a29-f8b6370ff0fc /boot           ext2    defaults        0       2
/dev/mapper/www-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /srv        ext4    defaults,auto,_netdev 0 0
# /dev/sdb1       /var/www/public        ext4    defaults,auto,_netdev 0 0
-----------------------------------------------------------------------------------------------------

---

### Post by rnerwein2 on 2013-08-19
hi
do you see the difference: 
--> your mount command is: mount /dev/[COLOR=#008000]sbd1[/COLOR] /var/www/public
      but your fstab entry is   : /dev/[COLOR=#ff0000]sdb1[/COLOR]       /srv        ext4    defaults,auto,_netdev 0 0
sbd1 is not sdb1  !  ;-) 
habe i nice day
ciao

---

### Post by nick20 on 2013-08-19
It's a typo in the post (corrected) sdb1 is what I have been using on the command line and in fstab.
So unfortunately hasn't solved my issue.
thanks

---

### Post by rnerwein2 on 2013-08-19
> **nick20 said:**
> It's a typo in the post (corrected) sdb1 is what I have been using on the command line and in fstab.
So unfortunately hasn't solved my issue.
thanks
hi
ok sdbX i guess is an removeable disk. therfore you have to use: the blkid !!! the /devicenames can change for a couple of reasons - not the blkid !
figure it out and use the blkid in the fstab instead of /dev/blablu
ciao

---

### Post by nick20 on 2013-08-19
Still getting the same error on startup using blkid (UUID) in fstab.

-----------------------------------------------------------------------------------------------------
The disk drive for /var/www/public is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery
-----------------------------------------------------------------------------------------------------

If I mount the disk in /srv no problem
If I mount the disk in /var/www/public I get above error

---

### Post by nick20 on 2013-08-20
I have tried using UUID to mount in fstab
I have tried putting the mount command in rc.local
I have tried putting the mount command in a script and running the script from rc.local

Why can't I run a mount command in rc.local?

I can only mount the device manually from the command line after booting.

Could the problem be apache related as I am trying to mount in /var/www?

---

### Post by bab1 on 2013-08-20
> **nick20 said:**
> I have an iSCSI filesystem setup as /dev/sdb1 ...
I want to mount it in /var/www/public

... when I try to mount it on startup with fstab I get the following error

```
The **disk drive** for /var/www/public **is not ready yet or not present.**
```


The network interfaces are not up yet when fstab attempts to mount the share.

See [**_[COLOR="#0000FF"]here[/COLOR]_**]("http://serverfault.com/questions/117584/upstart-scripts-run-a-task-after-networking-goes-up").

---

### Post by nick20 on 2013-08-20
Thanks for the link I will try.

Logic tells me that it might not work for the simple fact that if I mount the iSCSI disk in fstab to /srv instead of /var/www/public it works i.e. no error

Will post results

---

### Post by bab1 on 2013-08-20
> **nick20 said:**
> Thanks for the link I will try.

Logic tells me that it might not work for the simple fact that if I mount the iSCSI disk in fstab to /srv instead of /var/www/public it works i.e. no error

Will post results

Can you post the output of this command```
df -h
```

---

### Post by nick20 on 2013-08-20
I have found a workaround for now.
I am mounting the iSCSI disk to a new directory /public through fstab on boot
then I have created a symbolic link from /public to /var/www/
I also repartitioned iSCSI disk with LVM so the device is now /dev/mapper/iSCSI-storage This made no difference with my issue


I would still like to be able to mount directly to /var/www/pubic on startup so have not marked thread as solved. 


As it stands with my workaround df -h results in the following
----------------------------------------------------------------------
Filesystem                 Size  Used Avail Use% Mounted on
/dev/mapper/www-root        34G  2.0G   30G   7% /
udev                       7.9G  4.0K  7.9G   1% /dev
tmpfs                      3.2G  256K  3.2G   1% /run
none                       5.0M     0  5.0M   0% /run/lock
none                       7.9G     0  7.9G   0% /run/shm
/dev/sda1                  228M   27M  190M  13% /boot
/dev/mapper/iSCSI-storage  192G  188M  183G   1% /public
----------------------------------------------------------------------
If I try to map directly to /var/www/public through fstab obviously the las line is not there
If I mount manually on command line to /var/www/public df -h reflects this

---

