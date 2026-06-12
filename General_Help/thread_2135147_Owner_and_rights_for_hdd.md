---
title: "Owner and rights for hdd"
date: 2013-04-13
forum: General Help
---

### Post by Azyx on 2013-04-13
I had a external USB-disk, that I have problem with. Probably the USB-SATA-interface...

But anyway, I formatted another USB-disk to ext4. I think it asked if I sould take ownership of the file system and I say yes. Now I put in the disk in the computer with SATA and have mounted it with fstab in /home/Azyx/1500GB.

Is that a good idea?

I have also another 500GB disk  mounted in /home/Azyx/500GB

when I ls -all i get;
....
```
drwx------ 10 Azyx    Azyx      4096 apr 12 14:15 1500GB
drwxrwxrwx 22 Azyx    root 593920 apr 13 13:51 500GB
```
....

How do I change the right so they get as the 500GB? No I need to change ownership more that in the mount-folder? fore instance owner ship of the hdd och the filesystem.

---

### Post by prodigy_ on 2013-04-13
For native file systems you need to change actual permissions. The easy way: ```
 chmod -R 777 /home/Azyx/1500GB
``` However this will mark all files as executable. A cleaner way would be: ```
find /home/Azyx/1500GB -type -d -exec chmod 777 '{}' \;
find /home/Azyx/1500GB -type -f -exec chmod 666 '{}' \;
```

Since these commands change permissions recursively, you should be careful with them. And since **rw** for everyone isn't really secure, you want to be careful with what you put on that drive.

---

### Post by oldfred on 2013-04-13
I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable. Change example /mnt/data to your data partition(s).
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name


 chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

---

### Post by Azyx on 2013-04-16
It is only storage for media and other files I have on the disk. Now it is like this:

```
drwxrwxrwx 10 Azyx    Azyx      4096 apr 12 14:15 1500GB
drwxrwxrwx 22 Azyx    root 593920 apr 13 13:51 500GB
```

As you may see, the other disk is owned by the group root, and it work well. But then I samba-share the folder 1500GB it's goes really slow to write and read and system load get hight.

My fstab lookes like this.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=d85c5374-17d7-4482-99c7-24ef41d31c35 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=f73abdd8-e708-4a95-87f2-c2eb160dbc29 /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=aee6a155-4b79-40c4-b59c-c615556b4cf7 none            swap    sw              0       0
#500GB-disken
UUID=5352c56f-108c-4a55-a351-fbfd1de72c00 /home/Azyx/500GB ext4 defaults   0       0
#1500GB-disken
UUID=78610a00-6b42-407b-b1d5-0d484fc12514 /home/Azyx/1500GB ext4 defaults  0       0

```

I have a weak memory of that you should let the filesystem, some were be owned by root, but can not remember how...

---

### Post by oldfred on 2013-04-16
chmod is permissions and chown is ownership.

sudo chown $USER:$USER /mnt/data
Where $USER is the your the user otherwise if you want someone else you have to use name of that user.
fred@fred-Precise:~$ echo $USER
fred

---

### Post by Azyx on 2013-04-16
> **oldfred said:**
> chmod is permissions and chown is ownership.

sudo chown $USER:$USER /mnt/data
Where $USER is the your the user otherwise if you want someone else you have to use name of that user.
fred@fred-Precise:~$ echo $USER
fred

No, no other user, but there is something wrong because copying stop and take a lot of time if i share the folder. I don't have anything in /mnt

But in /dev

```
Azyx@Blackus:/dev$ ls -all sd*
brw-rw---- 1 root disk 8,  0 apr 16 15:02 sda
brw-rw---- 1 root disk 8,  1 apr 16 15:02 sda1
brw-rw---- 1 root disk 8,  2 apr 16 15:02 sda2
brw-rw---- 1 root disk 8,  3 apr 16 15:02 sda3
brw-rw---- 1 root disk 8,  4 apr 16 15:02 sda4
brw-rw---- 1 root disk 8,  6 apr 16 15:02 sda6
brw-rw---- 1 root disk 8, 16 apr 16 15:02 sdb
brw-rw---- 1 root disk 8, 17 apr 16 15:02 sdb1
brw-rw---- 1 root disk 8, 32 apr 16 15:02 sdc
brw-rw---- 1 root disk 8, 33 apr 16 15:02 sdc1
brw-rw---- 1 root disk 8, 34 apr 16 15:02 sdc2
brw-rw---- 1 root disk 8, 48 apr 16 15:02 sdd
brw-rw---- 1 root disk 8, 64 apr 16 15:02 sde
brw-rw---- 1 root disk 8, 80 apr 16 15:02 sdf
brw-rw---- 1 root disk 8, 96 apr 16 15:02 sdg
a@Blackus:/dev$ 

```
  never seen the group 'disk' before...

---

### Post by oldfred on 2013-04-16
There are many other users and groups than / (root) that many are system related. Do not attempt to change them or the only fix will be a reinstall.

Only your /home or only your data partitions should have your user as owner.

```
[NOPARSE]sudo cat /etc/group

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:fred
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:fred
fax:x:21:fred
voice:x:22:
cdrom:x:24:fred
floppy:x:25:fred
tape:x:26:fred
sudo:x:27:
audio:x:29:pulse,fred
dip:x:30:fred
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:fred
sasl:x:45:
plugdev:x:46:fred
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:fred
colord:x:105:
scanner:x:106:colord,fred
messagebus:x:107:
lightdm:x:108:
nopasswdlogin:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
avahi:x:113:
netdev:x:114:fred
bluetooth:x:115:
lpadmin:x:116:fred
ssl-cert:x:117:
admin:x:118:fred
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
fred:x:1000:
sambashare:x:124:fred
whoopsie:x:125:
winbindd_priv:x:126:
haldaemon:x:127:
powerdev:x:128:[/NOPARSE]
```

---

