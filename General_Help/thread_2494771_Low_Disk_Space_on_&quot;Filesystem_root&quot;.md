---
title: "Low Disk Space on &quot;Filesystem root&quot;"
date: 2024-01-26
forum: General Help
---

### Post by webmanoffesto on 2024-01-26
I'm getting the Low Disk Space on "Filesystem root" error message. Below are some diagnostics I did. 
Do I really have low disk space on root? Running df -h gives me "/dev/sda4 29G 25G 2.4G 92% /". Is that root? Doesn't that mean I have 4G free on root? Which I guess should be okay. But, anyway why is only 8% remaining on a 30G root partition? I understand that 30G should be plenty of space.

Please tell me what you recommend I do.

The volume "Filesystem root" has only 738.6 MB disk space remaining.

$ sudo parted -l
```
Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 
Number   Start  End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
 2      274MB  290MB   16.8MB               Microsoft reserved partition  msftres
 3      290MB  968GB   968GB   ntfs         Basic data partition          msftdata
 4      968GB  999GB   31.5GB  ext4         Basic data partition          msftdata
 5      999GB  1000GB  879MB   ntfs                                       hidden, diag

```
$ df -hT -x squashfs -x tmpfs -x devtmpfs | grep -v 'snap'
```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda4      ext4       29G   25G  2.4G  92% /
efivarfs       efivarfs  192K  110K   78K  59% /sys/firmware/efi/efivars
/dev/sda1      vfat      256M   91M  166M  36% /boot/efi
/dev/sda3      fuseblk   902G  736G  167G  82% /home
```

---

### Post by SeijiSensei on 2024-01-26
I'd start with looking in /var.

---

### Post by Dennis N on 2024-01-26
Using Ubuntu?
Launch Disk Usage Analyzer to see what is using your disk space.

---

### Post by webmanoffesto on 2024-01-26
> **SeijiSensei said:**
> I'd start with looking in /var.

Thanks /var was at 12GB
I ran the script I found at [https://itsfoss.com/clean-snap-packages/](https://itsfoss.com/clean-snap-packages/)
It's now 8.9GB. So I recovered over 3GB. That's a big improvement. And it should put an end to the error messages. 

Does 8.9GB seem like a reasonable size for /var, or should I look for more ways to remove unnecessary files?

---

### Post by Tadaen_Sylvermane on 2024-01-26
depends on snap and flatpaks. with ubuntu defaulting / demanding snaps moving forward var will need to grow more and more each release I'd surmise. Gone are the days of a 2g var or whatever people used to do. var is going to become the new /usr with snaps.

What I'd personally do is repartition with lvm and have either space to grow var or a separate volume that is mounted at /var/snap that you can grow. it will be the bulk of everything as far as desktop is concerned.

---

### Post by MAFoElffen on 2024-01-26
You can also reset the size of journal to something smaller to save room... And delete some of the older log archives... Empty trash on the disk, and for users.

---

### Post by deadflowr on 2024-01-26
if you use Software Updater to update, it defaults to cache the packages in /var/cache/apt.
No need to rm anything, just run
```
sudo apt clean
```
to clear the archived packages.

You also look at your journal log size
```
journalctl --disk-usage
```
There are various ways to clean that out, either by time or byte.
Like
```
sudo journalctl --vacuum-time=1day
```
this will remove the logs older than 1 day old.
```
sudo journalctl --vacuum-size=100M
```
This will remove the oldest 100 megabytes of old logs.
SystemMaxUse=XXX
Like from here: [https://andreaskaris.github.io/blog/linux/setting-journalctl-limits/](https://andreaskaris.github.io/blog/linux/setting-journalctl-limits/)

> You can also reset the size of journal to something smaller to save room... 
I take my time and I see this, lol.

> <snip> separate volume that is mounted at /var/snap <snip>

Nothing is mounted there since it's used for the system-wide configurations of whatever snap needs system-wide configurations.
You probably mean /var/lib/snapd since that's where snap packages reside.

---

### Post by TheFu on 2024-01-26
> **webmanoffesto said:**
> Does 8.9GB seem like a reasonable size for /var, or should I look for more ways to remove unnecessary files?

It depends on what is in /var/ and what you use it for.  

Here's my /var/ on a VM host.
```
$ dft
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01                  ext4   35G  7.1G   26G  22% /
/dev/mapper/vg01-var01                   ext4   20G  4.2G   15G  23% /var
/dev/mapper/vg01-libvirt--01             ext4  134G  131G  2.8G  98% /var/lib/libvirt

```
Notice how I have multiple storage areas there? That's because I knew I'd need more than a typical amount from 2010 which was 2GB.  With snaps and lxd containers, Canonical has decided to use more and more of /var/ for non-var stuff.  Used to be that /var was just for logs. That changed with lxd and snap packages.

On another system, 
```
$ dft
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G   28G  4.6G  86% /
/dev/mapper/vg00-var                        ext4   54G   15G   37G  30% /var
/dev/mapper/WDBLK_8T-jellyfin               ext4   20G  8.0G   11G  44% /var/lib/jellyfin
```
Again, I knew that more storage would be needed, so I provided it.

You may also note that 
a) I split off the /var file system from /.  This is on purpose.
b) I place swap into a separate storage are and NEVER, EVER, use swap files.  By default Ubuntu places a swapfile in / that can eat 1-20GB of storage.
c) On both those systems, the /, file system use is vastly different.  One used just 4.6GB and the other 26GB?  Why such a huge difference?  Before you try to answer, /home/ is placed into dedicated storage areas as well.

So, in the end, it depends on how the storage is laid out and how it gets used, what the "appropriate size" might be.

---

### Post by yancek on 2024-01-27
The /var directory also contains log files and you can delete many of those.  The filesystem has 5% of the space reserved for itself so once you hit 95% used on the / filesystem, you are likely to have trouble booting.

---

### Post by SeijiSensei on 2024-01-27
When I manually format a drive in ext4 these days, I routinely reduce the reserved space down to 1% with "sudo mkfs -m 1 ...". The 5% figure was decided back when drives were orders of magnitude smaller than they are today. 1% of a 512GB drive is 5 GB. That's more than the size many disk drives were back when the 5% figure was chosen.

---

### Post by MAFoElffen on 2024-01-27
Another thing is to look in the Downloads folders of the users. We tend to 'collect' things that are no longer needed after a while. Just a thought.

---

