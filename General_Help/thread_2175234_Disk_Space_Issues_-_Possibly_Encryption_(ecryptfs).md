---
title: "Disk Space Issues - Possibly Encryption (ecryptfs) Related"
date: 2013-09-18
forum: General Help
---

### Post by sam17 on 2013-09-18
Hi

I'm having disk space issues on my Ubuntu 12.04 LTS PC. It seems to be related to ecryptfs. I've looked through other posts, and they either seem to be different issues, or in some cases the same issue, but the thread has been closed without a satisfactory resolution. The symptoms I see are as follows.

I have a dual boot laptop with a 13GB ubuntu partition on a 256GB hard disk (/dev/sda6)[INDENT][FONT=courier new]# fdisk -l /dev/sda[/FONT]

[FONT=courier new]Disk /dev/sda: 256.1 GB, 256060514304 bytes[/FONT]
[FONT=courier new]255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors[/FONT]
[FONT=courier new]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=courier new]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]Disk identifier: 0xe86cba39[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=courier new]/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT[/FONT]
[FONT=courier new]/dev/sda2          206848   457764863   228779008    7  HPFS/NTFS/exFAT[/FONT]
[FONT=courier new]/dev/sda3       457766910   500117503    21175297    5  Extended[/FONT]
[FONT=courier new]/dev/sda5       491962368   500117503     4077568   82  Linux swap / Solaris[/FONT]
[FONT=courier new]/dev/sda6       457766912   483805183    13019136   83  Linux[/FONT]
[FONT=courier new]/dev/sda7       483807232   491958271     4075520   82  Linux swap / Solaris[/FONT][/INDENT]

I am using 13GB of this according to df (This is correct, I have tested this by trying to write a 2GB file using the command "dd if=/dev/zero of=file1 bs=1024k count=2048, the write stops at 1.5GB with a no space on device error)[INDENT][FONT=courier new]# df -Th[/FONT]
[FONT=courier new]Filesystem         Type      Size  Used Avail Use% Mounted on[/FONT]
[FONT=courier new]/dev/sda6          ext4     13G   11G  892M  93% /[/FONT]
.
.
[FONT=courier new]/home/sam/.Private ecryptfs   13G   11G  892M  93% /home/sam[/FONT][/INDENT]

checking my disk usage with du gives the following (95% of the usage is under /home)[INDENT][FONT=courier new]# du -sh /home[/FONT][/INDENT]
[INDENT][FONT=courier new]9.1G    /home[/FONT][/INDENT]
[INDENT][FONT=courier new]# du -sh /home/sam /home/.ecryptfs/[/FONT]
[FONT=courier new]4.6G    /home/sam[/FONT]
[FONT=courier new]4.6G    /home/.ecryptfs/[/FONT][/INDENT]


Which seems to say that I am double using my disk space with ecryptfs?

I tried not mounting the ecryptfs partition by removing the link ~/.ecryptfs/auto-mount

When I did this, and re-booted and logged in I got the following:[INDENT][FONT=courier new]# du -sh /home[/FONT][/INDENT]
[INDENT]4.6G    /home

[FONT=courier new]# du -sh /home/sam /home/.ecryptfs/[/FONT][/INDENT]
[INDENT]416K    /home/sam[/INDENT]
[INDENT]4.6G    /home/.ecryptfs


[/INDENT]
[INDENT][FONT=courier new]# df -Th
[/FONT][/INDENT]
[INDENT][FONT=courier new]Filesystem     Type      Size  Used Avail Use% Mounted on[/FONT][/INDENT]
[INDENT][FONT=courier new]/dev/sda6      ext4       13G   11G  890M  93% /[/FONT][/INDENT]
[INDENT][FONT=courier new].
.
[/FONT]
[/INDENT]

Note the ecryptfs file system is no longer mounted, and no longer taking up space according to du, but still reported by df.

---

### Post by oldfred on 2013-09-18
Your data is actually stored in the encrypted file system. But once you give pass phrase it is mounted and is usable just like any data un-encrypted. So it may show both the encrypted and un-encrypted while booted, but it really is just one with two views of same data.

It seems like you have added data and are filling up system.  You do have two swaps and only need one.

---

### Post by sam17 on 2013-09-19
Hi Oldfred,

Thanks for replying to my post. I understand that when mounted, the usage in my home directory shows as well as the encrypted files in the .ecryptfs folder. Unfortunately I don't understand why I am unable to write any more files when I have about 6GB free on a 13GB partition.

Also when I set the encrypted filesystem not to mount, and reboot (to make sure, although I think logging out would be enough), I have over 11GB used, alough I can only track down 4G of it. (details of the commands used are below.)

Any suggestions as to why this is, or what commands I should try to give more diagnostics would be much appreciated.

p.s. I know I have an extra swap partition, and may use it long term, but I am more interested in solving this issue currently.

Thanks



root@ubuntu:/home# cd /

root@ubuntu:/# ls -la
total 108
drwxr-xr-x  24 root root  4096 Sep 19 15:35 .
drwxr-xr-x  24 root root  4096 Sep 19 15:35 ..
drwxr-xr-x   2 root root  4096 Jul  5 14:28 bin
drwxr-xr-x   3 root root  4096 Sep  6 16:01 boot
drwxr-xr-x   2 root root  4096 Jan  4  2013 cdrom
drwxr-xr-x  17 root root  4160 Sep 19 15:26 dev
drwxr-xr-x 145 root root 12288 Sep 19 15:26 etc
drwxr-xr-x   4 root root  4096 Jan  4  2013 home
lrwxrwxrwx   1 root root    37 Sep  6 16:00 initrd.img -> /boot/initrd.img-3.2.0-53-generic-pae
lrwxrwxrwx   1 root root    37 Aug 20 08:06 initrd.img.old -> /boot/initrd.img-3.2.0-52-generic-pae
drwxr-xr-x  22 root root  4096 Jul  5 14:40 lib
drwx------   2 root root 16384 Jan  4  2013 lost+found
drwxr-xr-x   2 root root  4096 Sep 16 14:51 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   4 root root  4096 Jul 23 13:56 opt
dr-xr-xr-x 164 root root     0 Sep 19  2013 proc
drwx------  25 root root  4096 Sep  3 02:25 root
drwxr-xr-x  27 root root   920 Sep 19 15:26 run
drwxr-xr-x   2 root root 12288 Sep 18 12:40 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Aug 17  2012 srv
drwxr-xr-x  13 root root     0 Sep 19  2013 sys
drwxrwxrwt  11 root root  4096 Sep 19 15:36 tmp
-rw-r--r--   1 root root     0 Sep 19 15:35 typescript
drwxr-xr-x  10 root root  4096 Aug 17  2012 usr
drwxr-xr-x  13 root root  4096 Sep 19 15:25 var
drwxr-xr-x   2 root root  4096 Feb 16  2013 VirtualBox
lrwxrwxrwx   1 root root    33 Sep  6 16:00 vmlinuz -> boot/vmlinuz-3.2.0-53-generic-pae
lrwxrwxrwx   1 root root    33 Aug 20 08:06 vmlinuz.old -> boot/vmlinuz-3.2.0-52-generic-pae

root@ubuntu:/# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        13G   11G  980M  92% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           784M  880K  783M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  144K  2.0G   1% /run/shm

root@ubuntu:/# du -sm * | sort -n
du: cannot access `proc/2939/task/2939/fd/4': No such file or directory
du: cannot access `proc/2939/task/2939/fdinfo/4': No such file or directory
du: cannot access `proc/2939/fd/4': No such file or directory
du: cannot access `proc/2939/fdinfo/4': No such file or directory
du: cannot access `var/lib/lightdm/.gvfs': Permission denied
0    initrd.img
0    initrd.img.old
0    proc
0    sys
0    typescript
0    vmlinuz
0    vmlinuz.old
1    cdrom
1    dev
1    lost+found
1    media
1    mnt
1    run
1    selinux
1    srv
1    tmp
1    VirtualBox
9    bin
9    sbin
17    etc
195    boot
265    root
343    opt
766    var
838    lib
3777    usr
4526    home       **# N.B. this shows as 9062 when the .ecryptfs partition is mounted**

root@ubuntu:/# cd /home

root@ubuntu:/home# ls -la
total 16
drwxr-xr-x  4 root root 4096 Jan  4  2013 .
drwxr-xr-x 24 root root 4096 Sep 19 15:35 ..
drwxr-xr-x  3 root root 4096 Jan  4  2013 .ecryptfs
dr-x------  3 sam  sam  4096 Jan  5  2013 sam

root@ubuntu:/home# du -sm sam .ecryptfs/
1    sam
4526    .ecryptfs/

root@ubuntu:/# cd /tmp

root@ubuntu:/tmp# dd if=/dev/zero of=file1 bs=1024k count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 3.78548 s, 284 MB/s


root@ubuntu:/tmp# dd if=/dev/zero of=file2 bs=1024k count=1024
dd: writing `file2': No space left on device
590+0 records in
589+0 records out
618065920 bytes (618 MB) copied, 2.37467 s, 260 MB/s

root@ubuntu:/tmp# ls -lh file?
-rw-r--r-- 1 root root 1.0G Sep 19 15:36 file1
-rw-r--r-- 1 root root 590M Sep 19 15:37 file2

---

### Post by sam17 on 2013-09-19
Hi Oldfred,

I've just read my post again, and gone through the maths and realised I was using all the disk space, sorry to bother you. :oops:

Sam

In my defence, when I was originally chasing down the culprit, using du showed the home directory as using 9 GB when I knew it only contained 4.5 GB. I got too wrapped up in working out this issue that I didn't go back and do the maths with the other space in use on the disk.

I guess that the moral of the story is trust df, but not du with encrypted filesystems.

---

### Post by oldfred on 2013-09-19
Glad you found it.

But different tools do show different things. You have the different math of binary and decimal, you have Linux formats hiding 5% so you may still be able to boot when full and some tools showing all mounted partitions.
When I list my root partition of 25GB it may show 125GB as I have linked in my data partition. 
So I always look at system with different tools and still do not knows which shows what version.

---

### Post by sam17 on 2013-09-19
Initially I thought it was a bug, but my main mistake was not realising that encryption works by adding another mounted filesystem, and that du has no way of seeing it as anything other than that. (my other mistake was not being able to add up)

If I had used du -x (skip directories on different file systems) I would have saved myself a world of pain.

---

