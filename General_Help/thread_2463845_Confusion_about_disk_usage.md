---
title: "Confusion about disk usage"
date: 2021-06-19
forum: General Help
---

### Post by dorpapst on 2021-06-19
I am a bit confused about how space consumption is adding up on my Ubuntu computer. The activities app says that I have used 94% of my disk usage, but I just don't have any day how 94% of 500 GB got used.
If I use an app like ncdu to show folders consuming a lot of space, then it only adds up to 277 GB:
[ATTACH=CONFIG]288692[/ATTACH]

I am also using timeshift as an backup tool and there is one webdav folder mounted. The latter one is seen in the screenshot, the first isn't. Could that be due to one of those two or is there somebody elementary which I am missing out?

---

### Post by CharlesA on 2021-06-19
Can you run these commands from a terminal please:

```
sudo df -h
```

```
sudo du --human-readable --max-depth=1 --exclude /dev --exclude /proc --exclude /sys /
```

---

### Post by TheFu on 2021-06-19
Besides what CharlesA says, there are lots of ways for storage to appear different from what we know is on the system.

Some of my most used commands are:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
df -[COLOR="#FF0000"]i[/COLOR]T -x squashfs -x tmpfs -x devtmpfs
find . -type f -size +3G -ls -print 
du -sh *|sort -h
```
The last two are PWD sensitive. May want to add sudo before both, to avoid issues with permissions, but that depends on the directory where we run the command.
I have aliases setup for most of those commands. It gets old filtering out the extra junk that isn't really storage added to some of the commands.

If you are using advanced storage volume management, as LVM, ZFS or BRTFS provide, then other commands are necessary to see the truth.
Be certain to check for low i-nodes. That's what the **df -i** does. Running out of inodes on a file system that has plenty of unused blocks remaining will prevent those blocks from being used.

If it also possible to mount new file systems over old file systems, effectively hiding all the old storage.  This can happen most often with backup storage that isn't always mounted and verified as correctly mounted before a backup job is run.

---

### Post by dorpapst on 2021-06-19
Hello everybody,
Thank you for your answers. In fact, I am using btrfs, maybe that is one of the answers to my problem.
The output of 
```
sudo df -h
```
is
```
Filesystem                                                    Size  Used Avail Use% Mounted on
udev                                                          7,8G     0  7,8G   0% /dev
tmpfs                                                         1,6G  2,2M  1,6G   1% /run
/dev/mapper/cryptdata                                         462G  434G   22G  96% /
tmpfs                                                         7,9G   70M  7,8G   1% /dev/shm
tmpfs                                                         5,0M  4,0K  5,0M   1% /run/lock
tmpfs                                                         7,9G     0  7,9G   0% /sys/fs/cgroup
/dev/nvme0n1p1                                                511M  3,4M  508M   1% /boot/efi
/dev/mapper/cryptdata                                         462G  434G   22G  96% /home
tmpfs                                                         1,6G  100K  1,6G   1% /run/user/1000
https://cloud.someurl.net/remote.php/dav/files/DORpapst/  250G  171G   80G  69% /mnt/ncloud
/dev/mapper/cryptdata                                         462G  434G   22G  96% /run/timeshift/backup
```

For 
```
sudo du --human-readable --max-depth=1 --exclude /dev --exclude /proc --exclude /sys /
```
its
```
331M    /boot
278G    /home
27M    /etc
0    /media
5,8G    /var
```

So those two are not telling me what I want to know.

Other interesting outputs according to commands from TheFu:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME            SIZE TYPE  FSTYPE      MOUNTPOINT
nvme0n1       465,8G disk              
&#9500;&#9472;nvme0n1p1     512M part  vfat        /boot/efi
&#9500;&#9472;nvme0n1p2       4G part  swap        
&#9474; &#9492;&#9472;cryptswap     4G crypt swap        [SWAP]
&#9492;&#9472;nvme0n1p3   461,3G part  crypto_LUKS 
  &#9492;&#9472;cryptdata 461,3G crypt btrfs       /run/timeshift/backup
```

```
df -hT -x squashfs -x tmpfs -x devtmpfs

Filesystem                                                   Type   Size  Used Avail Use% Mounted on
/dev/mapper/cryptdata                                        btrfs  462G  434G   22G  96% /
/dev/nvme0n1p1                                               vfat   511M  3,4M  508M   1% /boot/efi
/dev/mapper/cryptdata                                        btrfs  462G  434G   22G  96% /home
https://cloud.someurl.net/remote.php/dav/files/DORpapst/ fuse   250G  164G   87G  66% /mnt/ncloud
/dev/mapper/cryptdata                                        btrfs  462G  434G   22G  96% /run/timeshift/backup
```

```
df -iT -x squashfs -x tmpfs -x devtmpfs
Filesystem                                                   Type   Inodes IUsed   IFree IUse% Mounted on
/dev/mapper/cryptdata                                        btrfs       0     0       0     - /
/dev/nvme0n1p1                                               vfat        0     0       0     - /boot/efi
/dev/mapper/cryptdata                                        btrfs       0     0       0     - /home
https://cloud.someurl.net/remote.php/dav/files/DORpapst/ fuse  5738345 87105 5651240    2% /mnt/ncloud
/dev/mapper/cryptdata                                        btrfs       0     0       0     - /run/timeshift/backup
```
Interesting that those Inodes are empty.

The other wo commands from TheFu are taking ages (I used sudo), I will have a look.

But what seems to be the solution is actually the btrfs thing, I will do a research on that

---

### Post by tea for one on 2021-06-19
> **dorpapst said:**
> In fact, I am using btrfs, maybe that is one of the answers to my problem.

This is (possibly) something to do with btrfs and snapshots.

There is a similar thread here [https://ubuntuforums.org/showthread.php?t=2456338](https://ubuntuforums.org/showthread.php?t=2456338)

May or may not throw some light on the problem.

---

### Post by deadflowr on 2021-06-19
btrfs is definitely an odd bird.
It has it's own df commands
Normal df commands give weird outputs like so.
See: [https://btrfs.wiki.kernel.org/index.php/FAQ#or_My_filesystem_is_full.2C_and_I.27ve_put_almost_nothing_into_it.21]("https://btrfs.wiki.kernel.org/index.php/FAQ#or_My_filesystem_is_full.2C_and_I.27ve_put_almost_nothing_into_it.21")

---

### Post by TheFu on 2021-06-19
I've never even played with BTRFS, so don't know that any of those commands are useful. When I learned that du and df output wasn't telling the truth on btrfs, that made it much less interesting to even play around.

---

### Post by dorpapst on 2021-06-20
Hello,
Thank you for all of you for your postings. It seems now that there is a difference between free- and unallocated space, which is ok if one knows the correct commands. Nice to finally have learned that.
I am now only wondering about the fact if Ubuntu is going to go on my nerves if one of its programmes thinks that the disk is full even if it isn't.
Is there anybody who has experience with btrfs and knows something about that?

Again: thank you to all of your contributions, I am glad to hear that the disk isn't as full as Ubuntu pretends.

---

### Post by TheFu on 2021-06-20
If it was me, I'd learn from a _btrfs tutorial_. All the commands will be spelled out there.  It isn't like they are hidden.  Additionally, everyone is in the "manpages" i.e. help files on your system already which explains the commands, all the options, and how to use them.

```
$ btrfs filesystem usage
```
seems like a useful command.  It was in the 2nd link below, which has some interesting reading and graphs.

[https://btrfs.wiki.kernel.org/index.php/Getting_started#Creating_a_filesystem](https://btrfs.wiki.kernel.org/index.php/Getting_started#Creating_a_filesystem)
[https://btrfs.wiki.kernel.org/index.php/SysadminGuide](https://btrfs.wiki.kernel.org/index.php/SysadminGuide)

btrfs is an interesting solution. You probably selected it for a reason, since it is NOT the default file system on any Ubuntu.

---

### Post by ActionParsnip on 2021-06-20
I'd dive into /var and see what is using the space there. Also look in ~/.cache and see what is going on. Possibly clear cache in your browser etc.

---

### Post by TheFu on 2021-06-20
A search for "btrfs out of space: found this : [https://ohthehugemanatee.org/blog/2019/02/11/btrfs-out-of-space-emergency-response/](https://ohthehugemanatee.org/blog/2019/02/11/btrfs-out-of-space-emergency-response/)
That link, which I've never seen before, has some commands to see the space issue, figure out where it is happening and possible steps to address it.
Lots of other results were returned for that query string too.

Sorry that the people responding here aren't using btrfs.  For me, "new" isn't appealing. Can't speak for others.  Data is more important to me than hardware.  Hardware can be replaced. Data cannot.

---

