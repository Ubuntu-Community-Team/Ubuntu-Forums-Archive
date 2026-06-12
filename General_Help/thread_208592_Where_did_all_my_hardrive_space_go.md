---
title: "Where did all my hardrive space go?"
date: 2006-07-03
forum: General Help
---

### Post by Aelfric5578 on 2006-07-03
So here I was working on my ubuntu machine trying to compile a program.  After hours of dealing with various dependencies I finally got everything compilied and running.  After all that was done, I tried to create a new directory, but I get this error "No space left on drive"

Okay, because I had been installing and compiling software all day, my first thought was maybe I really had filled up my hard drive.  I couldn't remember how big my drive was so I thought it was possible.  I ran "df --si" and it returned  38 GB used 0 free.  This is basically a clean install of Dapper I've only been using the computer for about a month.  I really didn't think I had installed 40 GB worth of programs.  

After some research I found the command "du."  "du -sk / --si" returns 4.7 GB.  Unless I'm missing something (other than my hard drive space) wouldn't those two numbers be almost the same if my hard drive was full?  What have I done to my computer?

---

### Post by tonyr on 2006-07-03
As a start, see what's in directories **/tmp**, **/var/tmp**, and **/var/log**,
and clean out your browser cache.

Then **cd** to / and do sudo **du -s ***.  This might yield some clue as to where
the space has gone.  

I'm assuming that your hard drive is partitioned with one large partition for Ubuntu
and a single swap partition.

It would help if you could post the actual output of your commands, too.

---

### Post by Aelfric5578 on 2006-07-03
I hope you don't mind me using the si option, but it makes it easier for me to understand the output.
```
-----@thorin:/$ du -sk /tmp --si
599k  /tmp
-----@thorin:/$ du -sk /var/tmp --si
17k   /var/tmp
-----@thorin:/$ du -sk /var/log --si
4.2M  /var/log
-----@thorin:/$ cd /
-----@thorin:/$ sudo du -s * --si
4.7M  bin
39M   boot
0     cdrom
127k  dev
15M   etc
72M   home
4.1k  initrd
0     initrd.img
0     initrd.img.old
362M  lib
50k   lost+found
8.2k  media
4.1k  mnt
4.1k  opt
943M  proc
476k  root
11M   sbin
4.1k  srv
0     sys
599k  tmp
2.5G  usr
684M  var
0     vmlinuz
0     vmlinuz.old


```

Thank you for your willingness to help me.  As you can see, it doesn't seem like anything is taking up anything close to 40G

---

### Post by tonyr on 2006-07-03
OK, show more information.
Do
```

sudo fdisk -l
df

```
and post the output.

EDIT: ...or **df --si** if you prefer.

---

### Post by Aelfric5578 on 2006-07-03
```
----@thorin:/$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris
----@thorin:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             36875340  36867588         0 100% /
varrun                  513272        96    513176   1% /var/run
varlock                 513272         4    513268   1% /var/lock
udev                    513272       108    513164   1% /dev
devshm                  513272         0    513272   0% /dev/shm
lrm                     513272     18316    494956   4% /lib/modules/2.6.15-25-686/volatile

```

---

### Post by tonyr on 2006-07-03
We may not be catching all of the files, especially the ones that start with '.'
Try this:
```

sudo find / -type f -size  +1G -ls

```

This looks for **all** regular files on the whole disk whose size is greater than 1G.
If that doesn't turn up anything, you could try a smaller size like +100M or +10M.

---

### Post by Aelfric5578 on 2006-07-03
Nothing shows up greater thatn 1 G, One file is close:
```
----@thorin:/proc$ sudo find / -type f -size  +500M -ls
4026531861 917508 -r--------   1 root     root     939528192 Jul  3 22:28 /proc/kcore
----@thorin:/$ du /proc/kcore --si
940M  /proc/kcore

```

But it's still only 940 M.

There's only one other file that's over 100M and only three including those two that are greater than 50 M.

---

### Post by tonyr on 2006-07-03
/proc/kcore is a pseudo file that is a window onto your physical memory.

I gotta say, this is really weird.

The only other thing I can think of is that you have some process running that is
holding on to an open file of gargantuan proportions.  Does the **disk full**
condition persist across reboots?

---

### Post by Aelfric5578 on 2006-07-03
I can't believe I didn't think to reboot.  Everything is as it should be now.  11% used.  I just wish I knew what I did so that I could prevent it from happening again.  

Thank you for all your help.

---

### Post by tonyr on 2006-07-03
It points to temporary files owned only by processes (ie, no directory entry anywhere),
and those processes never die, or the delete/close of the file didn't take, or some such.

If you are using an IDE of some kind, I'd suspect that first.

---

