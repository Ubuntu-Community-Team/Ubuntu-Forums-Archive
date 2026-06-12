---
title: "/mnt/storage gone?"
date: 2013-03-26
forum: General Help
---

### Post by fewjr on 2013-03-26
Hello All,
I have been working on a media server, slowly trying to learn as I go. I have Ubuntu Server 12.04 LTS installed on a 120 GB SSD drive. I have 3 WD RED 1 TB drives in a raid5 configuration. So far all I have done is learned how to openssh from another computer, installed webmin (which I haven't used), and installed Plexmediaserver. I wanted to use the raid for storage of all my music, movies and pictures. I created the directory storage on /mnt (/mnt/storage). I followed a tutorial somewhere. Then I mounted my external drives and put 480 GB's of music in there (/mnt/storage on /dev/md0). I openssh into server and had a message that a reboot was required. After the reboot Plex stopped working.

I re-mounted the raid5 and rescanned the music in Plex, but no go. I'm not sure whats wrong. The folder I made in /mnt for storage is still there but if I cd into /mnt/storage my data isn't there. Says:  No such file or directory. 


> goblin@*****:/$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra      id10]
md0 : active raid5 sdb1[0] sdd1[3] sdc1[1]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>


> goblin@*****:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/goblinservant-root /               ext4    errors=remount-ro 0            1
# /boot was on /dev/sda1 during installation
UUID=9f9e1cf4-4287-49d8-b56f-36c4a4ea12bd /boot           ext2    defaults             0       2
/dev/mapper/goblinservant-swap_1 none            swap    sw              0            0
/dev/md0: UUID="27708998-1b52-48ba-86a1-931b075000a5" TYPE="ext3"


> goblin@*****:/$ cat /etc/mtab
/dev/mapper/goblinservant-root / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda1 /boot ext2 rw 0 0


Can someone get me on the right track? I'm not sure what to do first at this point. I am searching and reading, but am going in circles. I kind of figure that upon reboot the directory I created isn't mounting automatically. I'm sure I missed something along the way. Thank you in advance.

fewjr

---

### Post by steeldriver on 2013-03-26
looks like you copied your blkid output verbatim into the fstab file - afaik you need to take the UUID and fstype values but the format needs to look like

```
UUID=27708998-1b52-48ba-86a1-931b075000a5 /mnt/storage ext3 defaults 0 2
```

(i.e. **UUID or label** then **mount point** then **fstype** then **options**) not 

```
/dev/md0: UUID="27708998-1b52-48ba-86a1-931b075000a5" TYPE="ext3"
```

See [FONT=courier new]man fstab[/FONT]

---

### Post by fewjr on 2013-03-26
Thank you so much for the quick reply. That did the trick and I'll be sure to read up a bit more. A long process when you have to go to work all the time..lol. So that should make it mount now during a reboot right? That was the whole idea behind being in fstab. Thanks again

fewjr

---

### Post by steeldriver on 2013-03-26
well... no promises ;)

but yes if the UUID is correct and everything is OK with the RAID volume it should mount on boot

---

### Post by fewjr on 2013-03-27
Well to make sure everything was going to work, I rebooted the server this morning to see if all was okay. I'd like to add an edit about the directory that my music is in. It is actually /mnt/storage/Music, not /mnt/storage. I figured eventually there would be a folder for movies and pictures, videos, etc. Well now my raid5 is active after the reboot, so thanks again for the help on that:

> goblin@*****:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[1] sdb1[0] sdd1[3]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>


I still have the problem with Plexmediaserver working after the reboot. I am running a refresh of the library now, and that takes a long time. I'll know if Plex is working right when its done I guess. 

I have a new problem now though. After I rebooted, I tried to list my music (ls -l /mnt/storage/Music) and I got:

> goblin@goblinservant:~$ ls -l /mnt/storage/Music
total 20
drwx------   2 root root 16384 Mar 14 08:08 lost+found
drwxr-xr-x 170 root root  4096 Mar 18 18:43 Music


So instead of my music I get another Music folder. I had to do: (ls -l /mnt/storage/Music/Music). Then my music came up. Can anyone tell me what happened to make this directory expand or whatever you would call it. I am at loss as to how rebooting the server caused my Music folder to get moved into a new Music folder that I didn't create. Here is the fstab file after fixing it as per Steeldriver's input:

> goblin@goblinservant:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/goblinservant-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=9f9e1cf4-4287-49d8-b56f-36c4a4ea12bd /boot           ext2    defaults        0       2
/dev/mapper/goblinservant-swap_1 none            swap    sw              0       0
UUID=27708998-1b52-48ba-86a1-931b075000a5 /mnt/storage ext3 defaults 0 2




fewjr

---

### Post by fewjr on 2013-03-29
bump please

---

### Post by steeldriver on 2013-03-29
What's the problem exactly? Can't you just move everything in the /mnt/storage/Music/Music directory up one level, and then delete the empty directory?

---

### Post by fewjr on 2013-03-31
Well yes, I'd thought of doing that but when I openssh in again the directory was back to normal, (mnt/storage/Music). That was so odd and I would love to know what happened there. As far as Plex goes, I guess that may be a subject for another section of the forum. My mount point is good now.Thanks again.

fewjr

---

