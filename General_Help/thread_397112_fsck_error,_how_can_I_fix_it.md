---
title: "fsck error, how can I fix it?"
date: 2007-03-30
forum: General Help
---

### Post by Vinze on 2007-03-30
Hey, during bootup, my Xubuntu Feisty machine switches from the usplash to tty1 where it has just checked hdb1 and then starts checking hdb2. However, this takes ages. I discovered /var/log/fsck/checkfs which contains the following messages (also attached):

> Log of fsck -C -R -A -a 
Fri Mar 30 14:31:50 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 128165 files, 1899568/1917887 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:42/00, 72:52/00, 73:49/00, 74:44/00, 75:47/00, 76:45/00, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00
  Not automatically fixing this.
/dev/hda2: 14 files, 16/1176466 clusters
/dev/hdb2: clean, 54979/2562240 files, 3860032/5120718 blocks (check after next mount)
/dev/hdb3: clean, 13608/641280 files, 103961/1281183 blocks (check in 4 mounts)

Fri Mar 30 14:33:09 2007
----------------


What can I do to fix it?

Thanks in advance.

---

### Post by teaker1s on 2007-03-30
**Not had any problems myself but:**
one report of this I remember user disconnected second hard drive and booted shut down and reconnected and rebooted. i would advise reading the manual for fdisk and seeing if it has any ideas
```
man fsck
```

---

### Post by Vinze on 2007-03-30
> **teaker1s said:**
> **Not had any problems myself but:**
one report of this I remember user disconnected second hard drive and booted shut down and reconnected and rebooted. i would advise reading the manual for fdisk and seeing if it has any ideas
```
man fsck
```

You mean disconnecting as really removing it from the computer? I wouldn't be able to do that...

I also read the manual but I didn't get much wiser of it, it all sounded too risky to me to start fiddling around without any knowledge.

---

### Post by teaker1s on 2007-03-30
Okay these are the suggestions I have reading the forums, a quik search of fsck and reading the threads may help pinpoint your issue
1) issue with certain kernels-try booting older kernel
2)boot recovery kernel and see if fsck can complete
3)check your grub as the name of your hard drive may be causing issue

---

### Post by Vinze on 2007-03-31
> **teaker1s said:**
> Okay these are the suggestions I have reading the forums, a quik search of fsck and reading the threads may help pinpoint your issue
1) issue with certain kernels-try booting older kernel
2)boot recovery kernel and see if fsck can complete
3)check your grub as the name of your hard drive may be causing issue

I'm not at home right now, but I'll try 1) and 3) when I am, thanks. 2) is not it, I have already had to boot in recovery mode and I still had this issue.

But if indeed booting an older kernel works, what should I do then?

---

### Post by teaker1s on 2007-03-31
there is a kernel issue from what I see in some posts, while I openly admit that I don't know the answer-the most common issues are worth a go first. 
As for possible dodgy kernel-if it boots okay with previous one when you select from grub menu-look at launchpad for a bug, if there isn't one then file a bug:popcorn:

---

### Post by Vinze on 2007-04-02
> **teaker1s said:**
> there is a kernel issue from what I see in some posts, while I openly admit that I don't know the answer-the most common issues are worth a go first. 
As for possible dodgy kernel-if it boots okay with previous one when you select from grub menu-look at launchpad for a bug, if there isn't one then file a bug:popcorn:

Booting another kernel did not make a difference :(

Also, I could find nothing that looked strange to me in /boot/grub/menu.lst, but I've attached it to be sure. It'd be really cool if this problem could be solved...

---

### Post by teaker1s on 2007-04-02
compare mine to yours  I wonder if the mount points are incorrect causing an fsck error?
[QUOTE]
title		Ubuntu, kernel 2.6.15-28-k7
root		(hd0,0)
[COLOR="Red"]kernel		/boot/vmlinuz-2.6.15-28-k7 root=/dev/hda1 ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.15-28-k7
savedefault
boot
/QUOTE]

---

### Post by Vinze on 2007-04-02
> **teaker1s said:**
> compare mine to yours  I wonder if the mount points are incorrect causing an fsck error?
> 
title		Ubuntu, kernel 2.6.15-28-k7
root		(hd0,0)
[COLOR="Red"]kernel		/boot/vmlinuz-2.6.15-28-k7 root=/dev/hda1 ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.15-28-k7
savedefault
boot


Well, I do have two hard drives of which hdb is the one I use. I don't feel like messing in this anyway, as you never know ;)

---

### Post by teaker1s on 2007-04-02
until you use ```
sudo update-grub
``` changes are not permanant:) 
also you can always copy existing line

---

### Post by Vinze on 2007-04-02
> **teaker1s said:**
> until you use ```
sudo update-grub
``` changes are not permanant:) 
also you can always copy existing line

But how can I test if it worked if it's not permanent?

Also, if I were to do it, what should I change?

---

### Post by teaker1s on 2007-04-02
what I'm suggesting is
at grub hit "e" edit your kernel[COLOR="Red"] /boot/vmlinuz [/COLOR] line so you have either example:-
/dev/hda1 ro quiet splash

for sata or usb
/dev/sda1 ro quiet splash

so it looks something like mine below but with your kernel number
example mine
[COLOR="Red"]kernel /boot/vmlinuz-2.6.15-28-k7 root=/dev/hda1 ro quiet splash[/COLOR]

try booting,if it doesn't then try another combination- if you boot and all works
```
sudo update-grub
``` 

Reason I suggest this is there are similar errors caused by grub error and I think what has happened is grub refers to mount point and it doesn't match what fsck is expecting to see

---

### Post by Vinze on 2007-04-03
> **teaker1s said:**
> what I'm suggesting is
at grub hit "e" edit your kernel[COLOR="Red"] /boot/vmlinuz [/COLOR] line so you have either example:-
/dev/hda1 ro quiet splash

for sata or usb
/dev/sda1 ro quiet splash

so it looks something like mine below but with your kernel number
example mine
[COLOR="Red"]kernel /boot/vmlinuz-2.6.15-28-k7 root=/dev/hda1 ro quiet splash[/COLOR]

try booting,if it doesn't then try another combination- if you boot and all works
```
sudo update-grub
``` 

Reason I suggest this is there are similar errors caused by grub error and I think what has happened is grub refers to mount point and it doesn't match what fsck is expecting to see

But it's hdb1 that I want to boot. I've got four partitions on hdb, of which hdb2 is my home directory which is what fsck is checking.

---

### Post by teaker1s on 2007-04-03
okay my misunderstanding, still your grub I would expect something like
[COLOR="Red"]kernel /boot/vmlinuz-2.6.15-28-k7 root=/dev/hdb1 ro quiet splash[/COLOR]

the reason I thought this is the issue is I had my grub go weird  with a hexidecimal mount point appear
I found this also , while not your issue-it tells of how to find error logs etc
[http://www.cyberciti.biz/tips/fsck-died-with-exit-status-1.html]("http://http://www.cyberciti.biz/tips/fsck-died-with-exit-status-1.html")

---

### Post by mcduck on 2007-04-03
Most likely just disabling fsck for your FAT partition should fix the problem. Edit /etc/fstab and change the last number in the entry line for the FAT partition to '0'.

---

### Post by Vinze on 2007-04-03
> **mcduck said:**
> Most likely just disabling fsck for your FAT partition should fix the problem. Edit /etc/fstab and change the last number in the entry line for the FAT partition to '0'.

Sounds cool, can I enable it after a new boot?

---

### Post by mcduck on 2007-04-04
> **Vinze said:**
> Sounds cool, can I enable it after a new boot?

I'm not sure what you mean. That will disable fsck on the partition on next boot and every boot after that until you change the number back to '2'.

---

### Post by Vinze on 2007-04-04
> **mcduck said:**
> I'm not sure what you mean. That will disable fsck on the partition on next boot and every boot after that until you change the number back to '2'.

OK, I changed it to "0", that works, but if I change it back to "1" it will name the errors again. I've turned checking off for now (thanks!) but I'd rather have the problem solved of course ;)

---

### Post by Malac on 2007-05-08
```
sudo umount /dev/[COLOR=Gray]<*whatever*>
[/COLOR]sudo fsck -ar /dev/[COLOR=Gray]<*whatever*>
```[/COLOR]

---

### Post by Vinze on 2007-05-08
> **Malac said:**
> ```
sudo umount /dev/[COLOR=Gray]<*whatever*>
[/COLOR]sudo fsck -ar /dev/[COLOR=Gray]<*whatever*>
```[/COLOR]

Wow, I didn't think I'd be getting another answer to this, thanks!

Anyway, I tried it, on both /dev/hda1 and /dev/hda2 but it didn't work :(

It did mention some errors on /dev/hda2 which I restored to the backup's state, but it didn't fix the problem apparently.

---

