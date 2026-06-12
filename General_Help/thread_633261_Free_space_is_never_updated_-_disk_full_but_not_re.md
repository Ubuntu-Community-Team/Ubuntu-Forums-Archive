---
title: "Free space is never updated - disk full but not really"
date: 2007-12-06
forum: General Help
---

### Post by Redsandro on 2007-12-06
Hi,

I have a problem where I cannot store big (500MB+) files on my /var (ext3) partition any more because Ubunti 7.04 thinks the disk is too full - 404 MB of free space is not enough, even though there should be more free space.

I removed a bunch of files, worth a total of about 6GB, but still there was only 404 MB free. I remounted, rebooted, fsck'ed and googled a lot, but nothing helped and I can't find a solution, although a lot of people post about 'df' giving off results.

Here's my result for the drive I'm talking about.
```
sander@MC-RED:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
(...)
/dev/sda9             132G  125G  404M 100% /var

```
And here I thought 132G - 125G = 7000M != 404M

Then I uploaded a ±160MB file to a samba share on the same drive (/var/upload)
```
sander@MC-RED:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
(...)
/dev/sda9             132G  125G  225M 100% /var

```
You see it's using up some space.

I removed the file in Nautilus 2.8 as root, bypassing the Trashcan, which was and is empty.
```
sander@MC-RED:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
(...)
/dev/sda9             132G  125G  225M 100% /var

```
See? Available disk space will not increase!

I have not used up all my inodes with small files
```
sander@MC-RED:~$ df -i
(...)
/dev/sda9             17M   19K   17M  1%   /var

```

What is wrong? I cannot use my computer anymore for serious tasks this way because I work with video (big files).

In case it's important, here is the whole output:
```
root@MC-RED:/etc/init.d# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.9G  406M  9.0G   5% /
varrun                506M  276K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  116K  506M   1% /proc/bus/usb
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda5              92M   31M   57M  35% /boot
/dev/sda8              12G  2.4G  8.9G  21% /home
/dev/sda10            5.8G   33M  5.4G   1% /tmp
/dev/sda7              18G  3.4G   14G  21% /usr
/dev/sda9             132G  125G  225M 100% /var

```

---

### Post by mahiyar on 2007-12-06
errrrrr not so sure did you try rebooting?

---

### Post by Redsandro on 2007-12-06
Yes I did. I booted in recovery mode just to be sure unmounting and fsck'ing wouldn't screw anything up.

---

### Post by atlfalcons866 on 2007-12-06
reclaim the 5% ext3 reserves by doing 
> sudo tune2fs -m 1 /dev/sda9

---

### Post by pointone on 2007-12-06
Does /root/.Trash exist? Anything in there?

---

### Post by metalheart on 2007-12-06
Run the following command in /var
```
du -sh *
```
to get size for all directories.

---

### Post by Redsandro on 2007-12-11
> **metalheart said:**
> Run the following command in /var
```
du -sh *
```
to get size for all directories.

Thanks. It confirmed that I should have free space.
```
root@MC-RED:/var# du -sh
125G    .
```

> **pointone said:**
> Does /root/.Trash exist? Anything in there?
It contains a few old versions of xorg.conf is all.. nothing that really eats up space.
/root is on a different partition from /var anyway.

> **atlfalcons866 said:**
> reclaim the 5% ext3 reserves by doing
```
sudo tune2fs -m 1 /dev/sda9
```

If 5% is reserved, it's probably for a reason. So I'm affraid to run that command. It made me wonder though if more freeing space would finally come through, and it does:
```
root@MC-RED:/# df -h
(...)
/dev/sda9             132G  125G  226M 100% /var
root@MC-RED:/# cd /var/upload/
root@MC-RED:/var/upload# ls -lah
total 734M
drwxrwxrwx  2 sander root   4.0K 2007-12-06 16:43 .
drwxr-xr-x 19 root   root   4.0K 2007-09-28 07:01 ..
-rwxr--r--  1 guest  guest  734M 2007-12-01 06:30 In Europa 06.mkv
root@MC-RED:/var/upload# unlink In\ Europa.mkv
root@MC-RED:/var/upload# df -h
(...)
/dev/sda9             132G  125G  960M 100% /var

```

What I do not understand, though, is how I could fit stuff on there that wouldn't free up space after being deleted in the first place?
And why is 5% reserved?

---

### Post by HermanAB on 2007-12-11
I have seen this with Ext3 too.  It defies all logic and fsck attempts at repair.  One day, it may magically fix itself though.

The result is that I don't use Ext3 anymore if I can help it.  Unless a disk is encrypted, I use JFS instead.

Cheers,

Herman

---

### Post by Redsandro on 2007-12-11
> **HermanAB said:**
> I have seen this with Ext3 too.  It defies all logic and fsck attempts at repair.  One day, it may magically fix itself though.

The result is that I don't use Ext3 anymore if I can help it.  Unless a disk is encrypted, I use JFS instead.

This is indeed about an Ext3 FS. I used Ext3 during installation because I read some reviews praising it to heaven. I don't know JFS. I often think some linux thing defies all logic so it's a funny thing you say it like that. When unpacking some RAR files I got the craziest error message. It coult have just said *'disk is full'*. But I usually relax myself by thinking everything's rational, just in a complicated way that I don't fully understand.


> **atlfalcons866 said:**
> reclaim the 5% ext3 reserves by doing
> sudo tune2fs -m 1 /dev/sda9


Even though I still want to know what's the use of keeping space from being used and how I was able to add those files beyond the reserved space (was there a recent Ubuntu update that increased the reserved space?), I couldn 't help really wanting to try it out.

```
root@MC-RED:/var/upload# df -h
(...)
/dev/sda9             132G  125G  960M 100% /var
root@MC-RED:/var/upload# tune2fs -m 1 /dev/sda9
tune2fs 1.40-WIP (14-Nov-2006)
Setting reserved blocks percentage to 1% (351281 blocks)
root@MC-RED:/var/upload# df -h
(...)
/dev/sda9             132G  125G  6.4G  96% /var
root@MC-RED:/var/upload# 

```

So.. THANK YOU!
Thank you all for participating in my quest for hard drive justice :)

---

### Post by atlfalcons866 on 2007-12-11
from man tune2fs 

>  -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem fragmentation, and to allow system  daemons,  such  as  sys&#8208;
              logd(8),  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.


About JFS, i would stay away from JFS unless you have special use for it, like mythtv where ext3 is slow at deleting large files. My computer lost power today and my file system got corrupted byond repair from fsck. but my /home ext3 just said recovering journal and all the data is fine. I have reformatted my /partition as ext3. Even though jfs is faster than ext3 i would use any reliable file system over a faster file system any day. 

Two more things about JFS. One it only journals metadata. By default ext3 journals metadata but in an ordered way.

Second JFS is very prone to fragmentation. At 25% full on my old /home partition i had a torrent in 30000 extents. Even the maintainer of JFS says fragmentation can be a problem on JFS.

---

### Post by renaux on 2008-03-05
hello,
  I just reclaimed over 6 gigs by cleaning the trash through the command line.  I'm running linux mint, so they changed a few things from vanilla ubuntu.  My trash folder is not viewable in nautilus, but I have a "lost+found" which was empty.  Anyways, the command I used was 
rm -rf /home/<username>/.Trash

---

### Post by idomagic on 2008-06-02
Finally, I was pulling my hair trying to figure out why df -h was inconsistent with gparted in free space, until I found this thread.
I reclaimed some +40gb today on my fileserver after finding out about reserved blocks on ext3.

Found some more information here -> [http://www.walkernews.net/2007/02/28/tune2fs-increase-linux-free-disk-space/](http://www.walkernews.net/2007/02/28/tune2fs-increase-linux-free-disk-space/)

---

### Post by rex@rexconsult.com on 2008-07-21
Hi,
I have exactly the same problem of not being able to release disk space on two (old) Dell Dimension 2400's. 
I am NOT a ops system person so I need a blow by blow guide as to how to get free of this problem.
Does anyone have the patience to show me the way. Please!
R

---

