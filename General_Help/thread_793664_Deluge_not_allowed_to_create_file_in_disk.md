---
title: "Deluge not allowed to create file in disk"
date: 2008-05-14
forum: General Help
---

### Post by iamah on 2008-05-14
Hi, I'm trying to chmod my torrents directory because Deluge seems unable to create anything there.

So now permissions are 770, owner root, group plugdev. 

The problem is I try to chmod 775 or 777 and nothing happens, no error, but no change too. :confused:

---

### Post by bingoUV on 2008-05-14
When you try to chmod, do you do this as root i.e.
```

sudo chmod 777 /path/to/dir

```

775 may or may not work depending on the group id of the torrent client program (Deluge)

When you say "no change too", does that mean
1. permissions of the folder do not change?
2. permissions change but the behaviour of Deluge of not being able to create files there does not change?

---

### Post by iamah on 2008-05-14
I'm using sudo like you said, and option 1: permissions don't change, I'm using ls to check.

The directory is on another partition, I believe NTFS because is shared with windows.

I wonder  if there's a problem if I put deluge in the same group as the directory, "plugdev" I believe.

---

### Post by bingoUV on 2008-05-14
Sorry, no idea about how permissions are handled in NTFS mounted in linux.

---

### Post by chrisccoulson on 2008-05-14
You can't use chmod or chown to change permissions on NTFS or FAT volumes, as they have no concept of POSIX file permissions. The permissions are defined by the mount options. Could you explain how the volume is mounted? Is it automounted or is it statically identified in /etc/fstab? If it is automounted and you are a member of plugdev, then you will have write access unless the volume is mounted read only.

With the volume mounted, could you post the output of:
```
mount -l
cat /etc/fstab
```
and also say which filesystem you are trying to save to (if there are multiple NTFS filesystems)

---

### Post by iamah on 2008-05-14
I'm aiming at hda4, seems to be FAT32 actually:

```
$ mount -l
/dev/hda3 on / type reiserfs (rw,notail) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
**/dev/hda4 on /media/hda4 type vfat (rw,utf8,umask=007,gid=46) [BAU]**
/dev/hda5 on /media/hda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096) []
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/scratchbox on /scratchbox/users/hilmilho/scratchbox type none (rw,bind)
/tmp on /scratchbox/users/hilmilho/tmp type none (rw,bind)
/proc on /scratchbox/users/hilmilho/proc type none (rw,bind)
/dev on /scratchbox/users/hilmilho/dev type none (rw,bind)
/dev/pts on /scratchbox/users/hilmilho/dev/pts type none (rw,bind)
/dev/shm on /scratchbox/users/hilmilho/dev/shm type none (rw,bind)
/sys on /scratchbox/users/hilmilho/sys type none (rw,bind)

```

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=2a1f9af6-6aaf-4328-95b4-89b525c44471 /               reiserfs notail          0       1
[b]# /dev/hda4
UUID=59E0-C794  /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1[/b]
# /dev/hda5
UUID=4CD84F23D84F0AA2 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=afd59242-6a4b-4291-8855-dc8994cda346 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Here is the directory's permissions:
```
drwxrwx--- 11 root plugdev     32768 2008-05-11 16:41 torrents
```

---

### Post by chrisccoulson on 2008-05-14
Ok, the partition is FAT32, and the mount options look ok. Is your user definately a member of plugdev? if so, then it is likely your volume is mounting read only for some reason.

Could you open a terminal, and type the following:
```
sudo tail -f /var/log/syslog
```

In another terminal, could you unmount and remount your volume, monitoring the output in the first terminal. Could you paste the outputs to both terminals here:
```
sudo umount /media/hda4
sudo mount /media/hda4
```

Could you also post the output of
```
groups
```

Cheers

---

### Post by iamah on 2008-05-14
User was in plugdev already, I tried to do it and got this confirmation. 

I forgot to mention that I've been able to modify files in that partition since the beginning, this is probably the first time I have a problem with that. Only noticed now Deluge was refusing to start any downloads, but was able to resume downloads created by Windows uTorrent.

So I got in Deluge's FAQ 
[http://deluge-torrent.org/faq.php#6n38](http://deluge-torrent.org/faq.php#6n38)
> Deluge keeps the torrents paused or pausing and resuming and then pausing my torrents repeatedly. What's the problem?

The first thing you should check is if you need to increase the number of maximum active torrents in the Downloads tab of Preferences. If that's not the problem, then you probably don't have enough room to download the torrent. **Also, on Linux, it could be that the directory that you're trying to download to has the wrong permissions, so Deluge isn't being able to write to it.** If you've checked the free space and permissions and everything looks fine, try switching to compact allocation and removing and re-adding the torrent. Full allocation *may* sometimes have problems with some more exotic filesystems, such as UFS2 or FAT32 on Linux.



Nothing changed while umounting and remounting, worked ok. This is the output before and after:
```
$ sudo tail -f /var/log/syslog
May 14 20:02:39 ferrugem kernel: [   80.662811] lo: Disabled Privacy Extensions
May 14 20:02:40 ferrugem avahi-daemon[4688]: Registering new address record for fe80::250:8dff:fee7:e5a7 on eth0.*.
May 14 20:02:37 ferrugem ntpdate[5441]: step time server 91.189.94.4 offset -3.689667 sec
May 14 20:02:46 ferrugem kernel: [   90.772932] eth0: no IPv6 routers present
May 14 20:08:42 ferrugem gdm[5155]: WARNING: Não foi possível autenticar o usuário 
May 14 20:08:55 ferrugem hcid[5103]: Default passkey agent (:1.18, /org/bluez/passkey) registered
May 14 20:08:55 ferrugem hcid[5103]: Default authorization agent (:1.18, /org/bluez/auth) registered
May 14 20:08:58 ferrugem NetworkManager: <info>  Updating allowed wireless network lists. 
May 14 20:08:58 ferrugem NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 14 20:17:01 ferrugem /USR/SBIN/CRON[5757]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

```
$ groups
hilmilho adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev sbox
```


I found this:
[http://ubuntuforums.org/showthread.php?t=619185](http://ubuntuforums.org/showthread.php?t=619185)

---

### Post by chrisccoulson on 2008-05-15
Your few lines from syslog don't contain the information I'm looking for. It doesn't look like they contain the messages from unmounting / remounting the volume.

Could you open a terminal and cd to your torrent directory (I assume something like cd /media/hda4/torrents), then do:
```
touch test
```
...and post the output. 

Could you also post the output of:
```
grep panic /var/log/syslog
```

---

### Post by iamah on 2008-05-15
Nothing changed again, weird... 
```
May 15 15:38:00 ferrugem NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May 15 15:38:02 ferrugem kernel: [   77.807398] NET: Registered protocol family 10
May 15 15:38:02 ferrugem kernel: [   77.807943] lo: Disabled Privacy Extensions
May 15 15:38:00 ferrugem ntpdate[5453]: step time server 91.189.94.4 offset -3.231631 sec
May 15 15:38:00 ferrugem avahi-daemon[4700]: Registering new address record for fe80::250:8dff:fee7:e5a7 on eth0.*.
May 15 15:38:09 ferrugem kernel: [   88.204960] eth0: no IPv6 routers present
May 15 15:38:11 ferrugem hcid[5113]: Default passkey agent (:1.18, /org/bluez/passkey) registered
May 15 15:38:11 ferrugem hcid[5113]: Default authorization agent (:1.18, /org/bluez/auth) registered
May 15 15:38:17 ferrugem NetworkManager: <info>  Updating allowed wireless network lists. 
May 15 15:38:17 ferrugem NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```


The file was created with those attributes
```
-rwxrwx---  1 root plugdev        0 2008-05-15 15:44 test

```
Everything I create there even using the file manager gets the same owner, group and permissions. Dunno if thats normal...

Thanks anyway for your attention :)

---

### Post by chrisccoulson on 2008-05-15
Yes, that's normal for FAT32. So, you have read-write permissions there, but Deluge can't create anything. Does Deluge give you an error when it tries to save the torrents? Can you try running it from a terminal to see if anything gets spat out.

---

### Post by iamah on 2008-05-15
I did that but nothing comes in the output.

---

