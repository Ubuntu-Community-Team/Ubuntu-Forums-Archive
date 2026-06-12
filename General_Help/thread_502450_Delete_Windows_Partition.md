---
title: "Delete Windows Partition"
date: 2007-07-16
forum: General Help
---

### Post by cmat on 2007-07-16
I want to delete my Windows XP partition in order to reclaim some space on a relatively small hard drive. I really need help in doing this without damaging my data or making my GRUB go haywire. 

Some info....

XP was installed on my drive first, it was a dual boot. 
XP is on an NTFS partition. 

Any help will be appreciated. :)

---

### Post by ayoli on 2007-07-16
use gparted to edit your partitions , dont be afraid about grub, formatting your XP partition will not erase your mbr (where grub is installed)
gparted can be found in ubuntu repos.

---

### Post by inter-m on 2007-07-16
> **ayoli said:**
> use gparted to edit your partitions , dont be afraid about grub, formatting your XP partition will not erase your mbr (where grub is installed)
gparted can be found in ubuntu repos.

Well I already did that, but now I can not resize the partition that the "/" is on... Any feedback on this will really help me alot...

---

### Post by merlinus on 2007-07-16
Use gparted live cd for this -- you cannot resize a partition that is in use.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You may be able to use the gparted that is on the ubuntu live cd, but the one on gparted live is a later version with more capabilities.

-merlin

---

### Post by ayoli on 2007-07-16
or any livecd that embed gparted (ubuntu livecd does, i think)

---

### Post by cmat on 2007-07-16
But will deleting XP mess up GRUB. When I failed with Linux the first time, I deleted the Ubuntu partition. GRUB gave me and error and I had to use a DOS recovery disk to fix it.

---

### Post by inter-m on 2007-07-16
I deleted XP and when I boot GRUB still gives the option to log onto XP as if it was still there... But as for any problems everything is fine... Its working for me...

---

### Post by merlinus on 2007-07-16
At the worst, you will have to reinstall grub.  It is quite straightforward.

You can reinstall it from the ubuntu live cd.

-merlin

---

### Post by bodhi.zazen on 2007-07-16
> **inter-m said:**
> I deleted XP and when I boot GRUB still gives the option to log onto XP as if it was still there... But as for any problems everything is fine... Its working for me...

Open a terminal, enter this command :

```
gksu gedit /boot/grub/menu.lst
```

Remove the windows stanzas at the bottom of the file, save and exit.

---

### Post by inter-m on 2007-07-16
I think I made a mistake when I resized and moved partition using gparted... Now I can not boot from my hard dirve... GRUB is giving me and error... Can someone just tell where did I go wrong???

---

### Post by merlinus on 2007-07-16
When you re-size and/or move partitions, their UUIDs change and so grub will not find them.

Try these commands one at a time in a terminal:

```

sudo fdisk -l
blkid

```

(l is a lowercase L)

The first will identify your ubuntu partition, and the second will show its UUID.

Then you will have to mount your root partition and edit both /boot/grub/menu.lst and /etc/fstab to make sure the UUIDs are consistent with these results.

-merlin

---

### Post by cmat on 2007-07-16
I'm in gparted. I deleted my partition and it's not allowing me to resize it to take up space that my Windows partition took up.

This is what it looks like.

| ---- unallocated ---- | ---- /dev/hda2 ---- | ---- swap ---- |

 Please help, I can't afford to make any mistakes. :(

---

### Post by merlinus on 2007-07-16
If you are running from your hard drive installation, then you cannot do any re-sizing and moving, since you are using that partition.

You can use the live cd, or better yet, gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by cmat on 2007-07-16
I'm on the 6.10 livecd right now.

---

### Post by merlinus on 2007-07-16
That has a rather old version of gparted.  Use the gparted live cd from the link in my last email -- it has more features and versatility.

-merlin

---

### Post by inter-m on 2007-07-16
The UUID is consistent with the results... This might help the error number that I get GRUB tries to boot is 15... But I dont understand what exactly I have to edit in /etc/fstab file???

---

### Post by merlinus on 2007-07-16
You might also compare the UUID with that in /boot/grub/menu.lst

If it is the same as in /etc/fstab then no editing of that file is required.

-merlin

---

### Post by Hex42 on 2007-07-17
i am want to delete my windows partition. i accidentally made the windows partition too bit when i installed ubuntu, and now i've decided to get rid of it all together.

i have already gotten gparted and have made my windows partition an unallocated partition. the problem is that when i set it up as a ext3 partition, it won't let me use it for anything, saying that i am not the owner and don't have permission to delete the stuff on there. i really just want it so there is just one linux partition and nothing else (other than the other partition that i don't know why its there. its shown as a linux swap.) 

any suggestions would help

---

### Post by cmat on 2007-07-17
The new gparted LiveCD had the ability do all the operations I needed it to do. Like move the partition and resize it. Just hope it boots up. But the drive names haven't changed so I'm all good :)

---

### Post by bodhi.zazen on 2007-07-17
Well personally I would use the gparted live CD as it has a few more options.

Second run gparted as root ;)

```
gksu gparted
```

Third the new gparted will both move and re-size your partition.

Last, you may need to re-install grub. This should be very easy, here is how 9don't let the title throw you)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by cmat on 2007-07-17
Boots up perfectly! I'm Windows free now. Also how can I clean out my GRUB menu. I have the Windows keys and who bunch of obsolete kernels on the list. How can I safely clean them?

---

### Post by merlinus on 2007-07-17
You can remove the old kernels via Synaptic.  Do a search for 2.6.20-15-generic

Then you can edit the grub file:

```

gksudo gedit /boot/grub/menu.lst

```

and delete the stanzas referring to the old kernels and windows.

-merlin

---

### Post by cmat on 2007-07-17
For safety's sake I just commented out all the lines regarding the other OS. Just in case something bad happens and I need to recover the information. ;)

---

### Post by merlinus on 2007-07-17
Good idea.  I always keep the next-to-last kernel just in case something untoward happens and I need to revert to it.

Good job!

Have fun....

-merlin

---

### Post by inter-m on 2007-07-17
> **bodhi.zazen said:**
> Well personally I would use the gparted live CD as it has a few more options.

Second run gparted as root ;)

```
gksu gparted
```

Third the new gparted will both move and re-size your partition.

Last, you may need to re-install grub. This should be very easy, here is how 9don't let the title throw you)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I reinstalled GRUB its working agian now... But the problem now when I choose the OS from the menu it gives me Error 15 file not found...

---

