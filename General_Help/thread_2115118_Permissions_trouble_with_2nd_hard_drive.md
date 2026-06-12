---
title: "Permissions trouble with 2nd hard drive"
date: 2013-02-11
forum: General Help
---

### Post by mark2741 on 2013-02-11
I'm trying to get Plex working properly. 

I am pretty sure it's a permissions issue. I installed a 2nd internal hard drive into my desktop (the other internal drive contains a dual-boot of Windows 7 and Ubuntu 12.10 64-bit). 

The path to the new hard drive, as mounted automatically by Ubuntu, is: /media/mark/NETWORK_SHARE

My user name is 'mark' and the label of the drive is 'NETWORK_SHARE' (even though it's really not a NAS/network drive I eventually plan on accessing it from my wireless network).

The NETWORK_SHARE drive is formatted as NTFS. O used gparted to format it.

Permissions on the NETWORK_SHARE drive:

mark@mark-linux:~$ ls -al /media/mark
total 28
drwxr-xr-x+ 4 mark mark  4096 Feb 11 21:07 .
drwxr-xr-x  4 root root  4096 Feb 11 21:26 ..
drwx------  1 mark mark 16384 Feb 10 21:37 6260FEA760FE80D9
drwx------  1 mark mark  4096 Feb 11 21:31 NETWORK_SHARE
mark@mark-linux:~$ 

I tried setting the permissions on the drive to 775 so that any user can read/write to it, but I can't. See below for what I tried, and the result:

mark@mark-linux:/media/mark$ ls
6260FEA760FE80D9  NETWORK_SHARE
mark@mark-linux:/media/mark$ ls -al
total 28
drwxr-xr-x+ 4 mark mark  4096 Feb 11 21:07 .
drwxr-xr-x  4 root root  4096 Feb 11 21:26 ..
drwx------  1 mark mark 16384 Feb 10 21:37 6260FEA760FE80D9
drwx------  1 mark mark  4096 Feb 11 21:31 NETWORK_SHARE
mark@mark-linux:/media/mark$ sudo chmod 775 NETWORK_SHARE
mark@mark-linux:/media/mark$ ls -al
total 28
drwxr-xr-x+ 4 mark mark  4096 Feb 11 21:07 .
drwxr-xr-x  4 root root  4096 Feb 11 21:26 ..
drwx------  1 mark mark 16384 Feb 10 21:37 6260FEA760FE80D9
drwx------  1 mark mark  4096 Feb 11 21:31 NETWORK_SHARE
mark@mark-linux:/media/mark$ 


As you can see, the permissions don't change. I've tried this numerous times. Tried it with the -R flag, tried just individual directories within the drive, all result in me not being able to change permissions. Because of this, Plex is not able to see any of the directories on the drive, so I can't add them to the Plex library.

Any help is appreciated.

---

### Post by omeomi on 2013-02-12
NTFS does not support file permissions in the same way as Linux partitions. 

You can try to mount the NTFS partition with Linux permissions in /etc/fstab:
```
UUID=XXXXXXX  /media/mark/NETWORK_SHARE  ntfs-3g  auto,users,permissions  0  0
```

where you need to replace the UUID with the correct one for your drive (use 'sudo blkid' to find it)

This person appears to have a similar problem, so you can try the things mentioned there: [http://askubuntu.com/questions/86959/any-way-of-maintaining-permissions-when-using-ntfs-mounted-drive-in-ubuntu](http://askubuntu.com/questions/86959/any-way-of-maintaining-permissions-when-using-ntfs-mounted-drive-in-ubuntu)

---

### Post by Morbius1 on 2013-02-12
[COLOR=Blue]Please don't use the "**permissions**" option in fstab. It will cause you nothing but grief if you are dual booting.[/COLOR]

> I tried setting the permissions on the drive to 775 so that any user can read/write to it, but I can't. ** Create a mount point away from /media/mark:
```
sudo mkdir /media/NETWORK_SHARE
```** Add to /etc/fstab the following line:
```
LABEL=NETWORK_SHARE /media/NETWORK_SHARE ntfs defaults,nls=utf8,uid=1000,umask=002,windows_names 0 0

```** If you currently have the the partition mounted unmount it.
** Run the following command which will first test for syntax errors and then silently mount the partition if there are none:
```
sudo mount -a
```The fstab line above will produce permissions of:
[B]drwxrwxr-x mark root

[COLOR=Blue]EDIT[/COLOR]: [/B]Depending on what you want to achieve you can set umask=000. Then permissions will be drwxrwxrwx[B].
[/B]

---

### Post by mark2741 on 2013-02-12
Morbius -

THANK YOU! Plex can now see the drive and all subdirectories. This is so helpful! Thanks again!

I have to run off to work so don't have time to re-boot but I assume since this is in fstab it will always mount and be available at /media/NETWORK_SHARE, and I'll be able to control that folder by setting permissions/make it shareable, etc. so other computers on my network can access it (I have Windows 7, 8, and a Macbook Pro)?

---

### Post by Morbius1 on 2013-02-12
> I have to run off to work so don't have time to re-boot but I assume  since this is in fstab it will always mount and be available at  /media/NETWORK_SHAREIt should. If you ran "sudo mount -a" and it had no output and the partition is mounted then you should be good to go.
> and I'll be able to control that folder by setting permissions/make it  shareable, etc. so other computers on my network can access it (I have  Windows 7, 8, and a Macbook Pro)?     If by that you mean Samba yes you should be able to do that.

---

