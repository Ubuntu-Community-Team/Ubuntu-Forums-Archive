---
title: "Moved partitions, can't login"
date: 2013-06-09
forum: General Help
---

### Post by BZO34 on 2013-06-09
hello, 

I searched the forum, and it seems that others have had this issue. I moved my partitions and now I can't login to my user profile because it returns me directly to the start page.

I created a new administrator profile do see if I could at least access the files in my original profile. However, when I looked in the Home folder, the my original user profile folder was not there.

I don't mind the fact that, I've lost my original user profile, I am just trying to access the files that I had on it.

Thanks

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by BZO34 on 2013-06-09
I resized the partitions on my HDD, and then I added a new ext3 partition using Easus partition manager. I did not realize that there was a specific way to do it for Ubuntu. I'm running 12.10.

thanks

---

### Post by ajgreeny on 2013-06-09
Did you use  Easus partition manager when running windows, as it seems that it is a windows application/utility?

If this is what you did it is possible that the partitions are no longer readable from ubuntu.  My first action in this situation would be to boot to a live Ubuntu CD/USB and from that run the command ```
sudo e2fsck /dev/sdx#
``` where sdx# is your ubuntu root partition; this may repair the filesystem if it is now corrupted in some way.

---

### Post by BZO34 on 2013-06-09
thanks for the reply yes, I ran Easus Partition Manager with windows

When I went, 

sudo fdisk -l

All the partitions showed up,

I then went "sudo e2fsck /dev/sdx6" and 

it said "no such file or directly while try to open dev/sdx6  Possibly non-existent device?"

it said the same thing when i tried sdx7



I also tried
"sudo e2fsck /dev/sd[SIZE=5]**a**[/SIZE]6" and it says device already mounted


In summary, the problem persists

---

### Post by BZO34 on 2013-06-10
bump

---

### Post by ahallubuntu on 2013-06-10
sda6 was probably it (sdx6 certainly wasn't unless you have 23 hard drives installed - counting starts at sda, then sdb, sdc....).  In any case, use fdisk -l output to figure out the correct partition where your Linux / was before.  Run e2fsck on that.

But you can't run e2fsck on a mounted partition.  You must umount it first.  (Assume you are running on a live USB or live CD.)

---

### Post by BZO34 on 2013-06-12
no dice trying to remount. Any other suggestions?

thanks

---

### Post by BZO34 on 2013-06-13
bump

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by BZO34 on 2013-06-14
yea I ran e2fsck, it didnt fix the problem

---

