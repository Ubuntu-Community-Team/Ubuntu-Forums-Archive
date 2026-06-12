---
title: "I  broke my Kubuntu! (/tmp mounting problems?)"
date: 2007-09-11
forum: General Help
---

### Post by OfficeLinebacker on 2007-09-11
Hi.  In installed Kubuntu 7.04 onto a machine made up of spare parts (Asus CUW-AM, 733MHz Celeron, 256MB memory, 2HD--2.6 and 3.2 GB)

I put /var/cache on the small HD, since I have tended to run out of space on little HDs from the cached packages I download, and, in my infinite wisdom:lolflag:, I put /swap AND /tmp on that drive, too.  So it breaks down to 1.6, .5 and .5 (GB) for cache, swap, and tmp respectively.

I messed around with /etc/fstab (following a guide about improving HD performance--noatime and somesuch) and now, AFAICT, /tmp not getting mounted properly.  At the login screen, I enter my uname/pw, it thinks a bit, the screen goes black (with a mouse pointer) for a bit, and the login screen reappears.  The only login I can do is the console.

In order to read a man page, I need to be root--as me, I get "unable to create a temporary file name--permission denied".

My current fstab has the three (/, /tmp,/var/cache) entries by UUID, nouser,defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid 0 0

I messed with the last numbers thinking changing the timing of when they're mounted had something to do with it, but it didn't make a difference.

I probably just need to edit the line for /tmp and remove some of the options, but which ones? 

In a side issue, when I attempt to upgrade the RAM size, I get a GRUB error--does this have something to do with the swap size to physical RAM ratio?  I'd like to add another 256 or 128MB stick....but after I get a GUI working.  :)

LMK what other info I can include--since the machine itself has only a text-interface, copying data to post is laborious at best.  I am a Perl programmer, so I am very lazy and impatient and have lots of hubris!

Thanks!

---

### Post by OfficeLinebacker on 2007-09-11
Quick update--I just took out the errors= and noatime parts of the entry for /tmp in fstab; no dice.

I also tried installing xfce4.  

No dice.

Thanks,
j

---

### Post by Happy_Man on 2007-09-11
Perhaps try this: press ctrl-alt-f1, and then log in. After you get a text prompt, enter ```
sudo fdisk -l
``` Find the partition that has your /tmp stuff on it, and then enter this: ```
sudo mount -t ext3 </dev name of partition that you just found> /tmp
```. Then press ctrl-alt-f7 and try logging in again.

---

### Post by OfficeLinebacker on 2007-09-11
> **Happy_Man said:**
> Perhaps try this: press ctrl-alt-f1, and then log in. After you get a text prompt, enter ```
sudo fdisk -l
``` Find the partition that has your /tmp stuff on it, and then enter this: ```
sudo mount -t ext3 </dev name of partition that you just found> /tmp
```. Then press ctrl-alt-f7 and try logging in again.

Hi!  Thanks for your help.

I tried what you said and the mount command didn't give any output.  After C-A-f7, same result.

So, back to square...1.5?

j

---

### Post by Happy_Man on 2007-09-12
No, the mount command isn't supposed to give any output. What matters is that you should be able to access you /tmp partition again. Should fix your problem.

---

### Post by OfficeLinebacker on 2007-09-13
well, it appears that something even more sinister was also afoot.  the root drive failed unspectacularly earlier this evening.  new system is a fresh install of Dapper on ONE 13GB disk.

j

---

