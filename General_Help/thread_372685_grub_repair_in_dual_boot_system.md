---
title: "grub repair in dual boot system"
date: 2007-02-28
forum: General Help
---

### Post by GolfGeek on 2007-02-28
I was moving some materials on my desk and the keyboard hit the reset button. At that time I was booted into WIN98SE. The machine went thru the reboot process and when it came to loading grub, I got error 27 and nowhere to turn. I tried to reboot again and received the same error. On another machine I went to the forums and found a thread to repair brub from live CD. What follows here is what happened as I tried to follow the instructions:

I followed the thread  224351
terminal mode:
sudo grub

grub> find /boot/grub/stage1
This generates error 15  file not found

Since that didn't work, I tried plan B from the same thread

sudo mkdir /mnt/root
This worked okay

sudo mount -t ext3 /dev/hd1 /mnt/root
This returned  mount: special device /dev/hd1 does not exist

I tried thi command using hd0 as well with the same results

Is there a way using Live CD to list the devices / drives in the system. I really need to repair this without having to reinstall Ubuntu.

---

### Post by confused57 on 2007-02-28
Yes, you can use the command:
```
sudo fdisk -l
```
the -l is a small "L"

your partitions are designated hda1, hda2, hda3, etc. or sda1, sda2, etc for SATA.
or for a second hard drive...hdb1,hdb2,etc.

---

### Post by GolfGeek on 2007-02-28
confused
Thanks. I just used the fdisk and got the information I needed. Hopefully the rest of plan B will now work

---

### Post by bodhi.zazen on 2007-02-28
You need to start grub with sudo :

```
sudo grub
```

Then re-try your find command and proceed ;)

---

### Post by GolfGeek on 2007-02-28
Plan B is not working exactly as planned. Aftter using the fdisk command Igot the following:

/dev/hda1   *              1   1048             8418028+  c  W95 FAT32 (LBA)

Obviously the ext3 section did not work

 wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Any suggestion as to what to try next. It might be faster to reinstall Ubuntu. As an aside, this is the seconf time I have crashed GRUB and I needed to reinstall. Is there an alternative to GRUB. It seems terribly fragile.

---

### Post by Marious on 2007-02-28
Just wanted to say I love the Sig bohdi hehe.

---

### Post by bodhi.zazen on 2007-02-28
Grub is reasonably stable.

I need more information to help ...

Can you post the output of ```
sudo fdisk -l
``` to look at your partitions.

Either you have a problem with your partitions or grub (or both)

Grub is very easy to re-install and you do not need to re-install Uubntu to do it.

Partition problems can be more difficult ...

FYI : Here is a great grub reference : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by bodhi.zazen on 2007-02-28
> **Marious said:**
> Just wanted to say I love the Sig bohdi hehe.

Thanks ;)

---

### Post by GolfGeek on 2007-02-28
Just a quick update. I followed one of the links to the grub "homepage" and discovered that the error 21 relates to a device that is not there. Sometimes you have to look at the most obvious sooner. Without checking, I did not confirm that the second hard drive was operating or being recognized. Will be back in the office in the AM to check the obvious. I do have a question tho... if there is a problem with the second hard drive and I can't get it recognized, is there a way to edit the menu.lst to change the default to the windows partition? I do need to get the windows partition booted in the morning. Thanks for the help and suggestions so far.

---

