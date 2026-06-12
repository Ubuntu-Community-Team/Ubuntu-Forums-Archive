---
title: "Write on external harddrive with HFS"
date: 2014-02-15
forum: General Help
---

### Post by linuxnewbie3 on 2014-02-15
Hi there,

I want to secure my data on a external harddrive, but the only one available at the momente is the drive of my girlfriends which is in the HFS+ format because she uses MaC OS.

I installed hfsprogs but I still only can read on the drive.

Hier is my output of the *mount* command

```
kevin@VPCCB31SE:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda3 on /media/kevin/Windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/kevin/Dateien type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=kevin)
/dev/sdb2 on /media/kevin/NINA_FAT type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdb1 on /media/kevin/NINA_HFS+ type hfsplus (ro,nosuid,nodev,uhelper=udisks2)
```

After posting this in an other board somebody told me to use this command:
[I]sudo mount -t hfsplus -o remount force,rw /dev/sdb1 /media/kevin/NINA_HFS+

[/I]```
kevin@VPCCB31SE:~$ sudo mount -t hfsplus -o remount force,rw /dev/sdb1 /media/kevin/NINA_HFS+
[sudo] password for kevin: 
Aufruf: mount -V                 : Version ausgeben
        mount -h                 : Diese Hilfe ausgeben
        mount                    : eingehängte Dateisysteme auflisten
        mount -l                 : dito, inklusive Volume-Label
So weit mit dem informativen Part. Als nächstes das Einhängen.
Der Befehl lautet „mount [-t fstype] irgendwas irgendwo“.
Details, die in /etc/fstab stehen, können weggelassen werden.
        mount -a [-t|-O] …       : alles aus der /etc/fstab einhängen
        mount gerät              : Gerät an bekanntem Ort einhängen
        mount verzeichnis        : hier bekanntes Gerät einhängen
        mount -t typ ger verz    : normaler Mount-Befehl
Beachten Sie, dass man nicht wirklich ein Gerät einhängt, sondern vielmehr
ein Dateisystem (vom gegebenen Typ), dass sich auf dem Gerät befindet.
Man kann auch einen schon sichtbaren Verzeichnisbaum woanders einhängen:
        mount --bind altesVerz neuesVerz
oder einen Unterbaum verschieben:
        mount --move altesVerz neuesVerz
Die Einhängeart in einem Verzeichnis kann geändert werden:
       mount --make-shared verz
       mount --make-slave verz
       mount --make-private verz
       mount --make-unbindable verz
Und das ganze rekursiv:
       mount --make-rshared verz
       mount --make-rslave verz
       mount --make-rprivate verz
       mount --make-runbindable verz
Ein Gerät kann über seinen Namen, also /dev/hda1 oder /dev/cdrom, gegeben
werden, oder über sein Label, mittels -L Label, oder über die UUID, mit -U UUID.
Weitere Optionen: [-nfFrsvw] [-o optionen] [-p passwdfd].
Für viele weitere Details: man 8 mount.
```After that command he asked me to use *mount* again[I]:
[/I]
```
kevin@VPCCB31SE:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda3 on /media/kevin/Windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/kevin/Dateien type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=kevin)
/dev/sdb2 on /media/kevin/NINA_FAT type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdb1 on /media/kevin/NINA_HFS+ type hfsplus (ro,nosuid,nodev,uhelper=udisks2)
kevin@VPCCB31SE:~$ 
```After that he did not answer me anymore. What do I do now?

---

### Post by ajgreeny on 2014-02-15
There are several hfsplus packages that you need to install before you can access and use any hfs+ partitions, so start with ```
sudo apt-get install hfsplus
``` and see if that solves your problem.

---

### Post by tgalati4 on 2014-02-15
If the folders/directories do not match the owner and User ID (UID) of the Linux system then you have a problem.  Use:

```
ls -la
``` to display the owner and UID of the folders on both your Linux system and the external drive.

If they don't match, then you need to use *sudo* to mount the drive with root privileges.  But then any file written to the drive will also have a root marking and that will create problems.

So although you want to make a backup, it is better to get a blank drive than screw up your girlfriend's drive.

---

### Post by linuxnewbie3 on 2014-02-15
> **ajgreeny said:**
> There are several hfsplus packages that you  need to install before you can access and use any hfs+ partitions, so  start with ```
sudo apt-get install hfsplus
``` and see if that  solves your problem.

No still the same problem...


> **tgalati4 said:**
> If the folders/directories do not match the owner and User ID (UID) of the Linux system then you have a problem.  Use:

```
ls -la
``` to display the owner and UID of the folders on both your Linux system and the external drive.

If they don't match, then you need to use *sudo* to mount the drive with root privileges.  But then any file written to the drive will also have a root marking and that will create problems.

So although you want to make a backup, it is better to get a blank drive than screw up your girlfriend's drive.

```
insgesamt 292
drwxr-xr-x 49 kevin kevin  4096 Feb 15 16:51 .
drwxrwxr-x  3 root  root   4096 Okt  9 17:55 ..
drwx------  3 kevin kevin  4096 Okt  9 18:28 .adobe
drwxrwxr-x  5 kevin kevin  4096 Okt 16 18:39 .anki
-rw-r--r--  1 kevin kevin   166 Okt 13 22:43 .apport-ignore.xml
drwxr-xr-x  2 kevin kevin  4096 Feb 15 20:20 Arbeitsfläche
drwxrwxr-x  3 kevin kevin  4096 Dez 30 12:36 .audacity-data
drwxr-xr-x  3 kevin kevin  4096 Feb 12 01:40 .avidemux
-rw-r--r--  1 kevin kevin  6823 Feb 15 22:37 .bash_history
-rw-r--r--  1 kevin kevin   220 Okt  9 17:55 .bash_logout
-rw-r--r--  1 kevin kevin  3637 Okt  9 17:55 .bashrc
lrwxrwxrwx  1 kevin kevin    27 Okt 21 23:57 Bilder -> /media/kevin/Dateien/Bilder
drwx------ 38 kevin kevin  4096 Feb 15 00:41 .cache
lrwxrwxrwx  1 kevin kevin    36 Okt 20 13:12 Comedy & Kabarett -> /media/kevin/Dateien/Comedy-Kabarett
drwx------  3 kevin kevin  4096 Okt  9 18:29 .compiz
drwx------ 43 kevin kevin  4096 Feb 12 02:19 .config
drwx------  2 kevin kevin  4096 Dez 19 14:55 .cups
drwx------  3 kevin kevin  4096 Okt  9 18:15 .dbus
-rw-r--r--  1 kevin kevin    25 Feb 15 16:51 .dmrc
lrwxrwxrwx  1 kevin kevin    30 Okt 21 23:57 Dokumente -> /media/kevin/Dateien/Dokumente
drwxrwxr-x  3 kevin kevin  4096 Nov 22 19:24 .everpad
drwxrwxr-x  2 kevin kevin  4096 Nov  2 19:38 .FBReader
drwx------  5 kevin kevin  4096 Feb 15 16:51 .gconf
drwxr-xr-x 24 kevin kevin  4096 Jan 27 19:41 .gimp-2.8
-rw-r--r--  1 kevin kevin     0 Nov 25 17:45 .gksu.lock
drwx------  4 kevin kevin  4096 Feb 15 16:14 .gnome2
drwx------  2 kevin kevin  4096 Okt 23 15:14 .gnome2_private
drwx------  3 kevin kevin  4096 Nov 23 19:44 .gnupg
drwxrwxr-x  2 kevin kevin  4096 Feb 15 16:56 .gstreamer-0.10
drwx------  2 kevin kevin  4096 Okt 19 18:06 .gvfs
lrwxrwxrwx  1 kevin kevin    26 Okt 20 13:14 Handy -> /media/kevin/Dateien/Handy
drwxr-----  2 kevin kevin  4096 Okt 10 06:42 .hplip
-rw-------  1 kevin kevin 33000 Feb 15 16:51 .ICEauthority
drwxr-xr-x  4 kevin kevin  4096 Dez 12 14:17 .icedtea
drwx------  3 kevin kevin  4096 Okt 11 16:47 .icons
drwxr-xr-x  3 kevin kevin  4096 Dez 12 14:17 .java
drwx------  3 kevin kevin  4096 Okt 23 20:10 .kde
drwx------  2 kevin kevin  4096 Feb 13 14:28 .kino-history
-rw-r--r--  1 kevin kevin  2967 Feb 13 14:22 .kinorc
drwxr-xr-x  3 kevin kevin  4096 Okt  9 18:15 .local
drwx------  3 kevin kevin  4096 Okt  9 18:28 .macromedia
drwxr-xr-x  2 kevin kevin  4096 Dez 29 13:39 .MakeMKV
drwxrwxr-x  3 kevin kevin  4096 Okt 12 11:44 .matplotlib
drwxr-xr-x  3 kevin kevin  4096 Dez 29 13:40 .mc
drwx------  4 kevin kevin  4096 Okt  9 18:24 .mozilla
lrwxrwxrwx  1 kevin kevin    26 Okt 21 23:57 Musik -> /media/kevin/Dateien/Musik
lrwxrwxrwx  1 kevin kevin    32 Okt 20 13:14 Nützliches -> /media/kevin/Dateien/Nützliches
lrwxrwxrwx  1 kevin kevin    26 Okt 21 23:56 Offen -> /media/kevin/Dateien/Offen
drwxr-xr-x  2 kevin kevin  4096 Okt  9 18:15 Öffentlich
drwxr-x---  6 kevin kevin  4096 Feb 13 14:34 .openshot
-rw-r--r--  1 kevin kevin   226 Feb 11 20:54 .pam_environment
drwx------  3 kevin kevin  4096 Nov  3 11:25 .pki
-rw-r--r--  1 kevin kevin   675 Okt  9 17:55 .profile
drwxrwxr-x  3 kevin kevin  4096 Okt 15 13:29 Programme
-rw-r--r--  1 kevin kevin   256 Okt 15 14:02 .pulse-cookie
drwxrwxr-x  2 kevin kevin  4096 Okt 23 20:16 .screenlets
drwxrwxr-x  3 kevin kevin  4096 Feb  9 16:46 .shutter
drwx------  6 kevin kevin  4096 Feb 14 23:43 .Skype
lrwxrwxrwx  1 kevin kevin    27 Okt 20 13:14 Spiele -> /media/kevin/Dateien/Spiele
lrwxrwxrwx  1 kevin kevin    18 Okt 10 15:28 stata13 -> /usr/local/stata13
drwxr-xr-x  4 kevin kevin  4096 Okt 10 15:46 .stata13
drwxrwxr-x  2 kevin kevin  4096 Jan 16 11:34 .steam
lrwxrwxrwx  1 kevin kevin    30 Jan 16 11:34 .steampath -> /home/kevin/.steam/bin32/steam
lrwxrwxrwx  1 kevin kevin    28 Jan 16 11:34 .steampid -> /home/kevin/.steam/steam.pid
drwx------  3 kevin kevin  4096 Okt 24 07:21 .thumbnails
lrwxrwxrwx  1 kevin kevin    86 Okt 10 12:13 .thunderbird -> /media/kevin/Windows/Users/Kevin/AppData/Roaming/Thunderbird/Profiles/8705dope.default
drwxr-xr-x  3 kevin kevin  4096 Okt 11 07:23 .tuxpaint
lrwxrwxrwx  1 kevin kevin    33 Okt 20 13:14 Universität -> /media/kevin/Dateien/Universität
lrwxrwxrwx  1 kevin kevin    27 Okt 24 23:56 Videos -> /media/kevin/Dateien/Videos
drwxr-xr-x  2 kevin kevin  4096 Okt  9 18:15 Vorlagen
drwxr-xr-x  4 kevin kevin  4096 Jan  9 18:55 .wine
-rw-------  1 kevin kevin    54 Feb 15 16:51 .Xauthority
drwx------  2 kevin kevin  4096 Nov 30 17:13 .xournal
drwxr-xr-x  3 kevin kevin  4096 Jan 10 20:12 .xpaint
-rw-------  1 kevin kevin   126 Feb 15 16:51 .xsession-errors
-rw-------  1 kevin kevin   353 Feb 15 16:14 .xsession-errors.old
drwx------  3 kevin kevin  4096 Okt 13 15:01 .zotero

```

```
insgesamt 81944
drwxrwxr-x  1 root root       24 Jan  1 17:36 .
drwxr-x---+ 6 root root     4096 Feb 15 22:37 ..
drwxr-xr-x  1   99   99       10 Apr  8  2011 09-11-23
drwxr-xr-x  1   99   99        8 Dez 30 17:03 09-12-16
drwxr-xr-x  1   99   99        7 Dez 30 16:59 10-09-01
drwxrwxrwx  1   99   99        8 Dez 31 16:00 11-07-28- nicht löschen
drwxr-xr-x  1   99   99       25 Dez 30 17:22 11-10-24
drwxrwxrwx  1   99   99        6 Dez 31 16:54 12-01-02
drwxr-xr-x  1   99   99        6 Dez 30 17:55 12-07-28
drwxr-xr-x  1   99   99        7 Dez 30 17:13 13-01-21
drwxr-xr-x  1   99   99        6 Jan  1 12:51 13-08-26
drwxr-xr-x  1   99   99        8 Jan  1 13:56 14-01-01
drwxr-xr-x  1   99   99        5 Jan  1 16:05 ältere Datensicherungen
d--x--x--x  1   99   99        8 Jan  1 17:55 .DocumentRevisions-V100
-rw-r--r--  1   99   99    12292 Jan  1 14:39 .DS_Store
drwx------  1   99   99       14 Jan  1 17:55 .fseventsd
dr-xr-xr-t  1 root root        2 Dez 31 14:55 .HFS+ Private Directory Data?
----------  1 root root 83886080 Dez 31 14:55 .journal
----------  1 root root     4096 Dez 31 14:55 .journal_info_block
drwx------  1   99   99        5 Dez 31 14:56 .Spotlight-V100
drwxrwxrwt  1   99   99        3 Jan  1 17:36 .TemporaryItems
d-wx-wx-wt  1   99   99        3 Jan  1 16:18 .Trashes
drwxr-xr-x  1   99   99        9 Okt 24  2011 xx-xx-xx - nicht löschen

```

Does this mean there is no way to use the drive without screwing up the drive

---

### Post by tgalati4 on 2014-02-15
Notice that 99 does not equal kevin.  Yes, you can use the drive, but I'm not going to describe the procedures and then have you screw it up and have two angry people.  It's not worth it.

Basically, you would squeeze the mac partition to create space for a new ext4 partition.  Then you can mount the new partition and write to it easily.  The issue is there is a chance of data loss by squeezing the mac partition.  You can do this from a mac using Disk Utility and then verify the partition after resizing so that you know it is intact.

---

### Post by fdrake on 2014-02-15
before attempting to mount the hfs+ partition make sure to  turn off the journaling using your mac.([http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write))
Still I'd be carefull in mounting hfs. Mac tend to lock them everytime you access them. User your mac and create a fat32 patrion so both linux anfd mac can access it with no problem.

---

### Post by linuxnewbie3 on 2014-02-16
Thanks for your really nice answers.

Since the Mac unfortunately is not available at the moment this is only an option for later. 

I am using Win 7 in Dualboot and I discovered a Software with a 10 days trial which lets me write on HFS with Windows, so I think at the moment this will be the easiest option. Later when I am at home I will keep you informed if I succeeded.

---

