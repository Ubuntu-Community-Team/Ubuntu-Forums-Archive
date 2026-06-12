---
title: "Gparted Issue (Resizing)"
date: 2008-04-02
forum: General Help
---

### Post by Mwelsh on 2008-04-02
[http://ubuntuforums.org/showthread.php?t=649664](http://ubuntuforums.org/showthread.php?t=649664)

Very similar problem to the one above, but I have a bit more information...

When I start gparted, it fails to load /dev/hda, which makes sense since I only have an sda drive attached. However, it mounts them as read only. I am unable to resize, the button is grayed out.

Also, there is issues with the GCC compiler I believe. But since the program is installed, I don't see how they are related.

Any help would be greatly appreciated,

Thanks in advance.

---

### Post by forrestcupp on 2008-04-02
You can't resize any partition that is mounted.  So you need to either unmount the drive, or use [GParted LiveCD](http://gparted.sourceforge.net/livecd.php) because it's made specifically for that purpose, so it doesn't mount any drives.

---

### Post by Mwelsh on 2008-04-02
I'd like to stay away as much as possible from the Live CD as this is part of a process, and having to reboot the computer everytime would be an unneeded waste of time.

I will ensure the drive isn't mounted, but I don't believe it was.

Thanks

---

### Post by 4Foot on 2008-04-02
Might be easier to just hijack this post with my question on this matter.

I have a 70 Gig drive with Hardy on it and it was partitioned as follows.

root 13 Gigs Sda1

Data 54 Gigs Sda6

Swap 3 Gigs  

I had permissions problems with Sda6 and could not get that fixed but I needed to make root larger because, for instance, a prog like DeVeDe would not write to Sda6 and would tell me that I did not have enough room to create a DVD file set on Sda1.

After some thought, I got my hands on Gparted LiveCD, booted into it and attempted to 'grow' Sda1 by 10 gigs. No joy.

I then decided that I needed to create room for it to 'grow" so I 'shrunk' Sda6 by 10 gigs successfully. I was very pleased with myself.

However, I now have an 'unallocated' drive of approx. 10 gigs and when I try to 'grow' Sda1 into that space it just does not allow me to do anything with it unless I want to shrink it.

Thinking it was unavailable, I chose the unallocated drive, clikked on 'new' and created it as an ext3 drive. Then I retried 'growing' Sda1 into that space and still no joy.

So, I have made available 10 gigs of space but cannot get my Sda1 to use it. I would be grateful for some insight into the reasons for my failure in this matter. 

Just saying that I must be stupid has already been taken as a response. 

Thanks

4Foot

---

### Post by Mwelsh on 2008-04-02
My hard drive is not mounted, and it still won't resize, only delete. I get a warning about not being able to read the drive, since it is NTFS (Ensure you have drivers installed?). However, if I mount it I can see the files fine, but not with Gparted. What am I missing?

---

### Post by cdenley on 2008-04-02
Just a guess, maybe you need ntfsprogs?
```

sudo apt-get install ntfsprogs

```
It has a ntfs resize tool, and is recommended by gparted, so that is probably required by gparted to resize ntfs partitions.

---

### Post by 4Foot on 2008-04-02
Please accept my apologies MWelsh, on reading this thread I had concluded that you were done with it. I did not mean to step on your active thread. I will try this elsewhere.

4Foot

---

