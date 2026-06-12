---
title: "Operating System Not Found -- I hate you, Windows."
date: 2007-12-30
forum: General Help
---

### Post by Prefectionist on 2007-12-30
Okay. Like many people, I'm sick of Vista, but I have a brand new computer with a bunch of high-end hardware. I wasn't sure if Windows XP would function properly on it, recognize my video card and all that, so I made a third partition (Vista and Ubuntu Gusty on my first hard drive, this one on my second) and installed a trial version of XP Home Edition onto it, just to test it out. Big mistake!

"Error loading operating system" shows up  when I try to turn on my computer. When I try to boot into Ubuntu using GAG, a grub command line comes up, but won't let me install grub into the MBR. GAG isn't able to install to the MBR either. XP, Vista, and Vista's System Restore partition all display the same Error message. My BIOS recognizes all my hardware, so nothing is amiss there.

Is there any way that I could save Ubuntu and Vista? Vista would be especially helpful; the partition manager allows me to delete troublesome partitions very easily...
Any insight would be deeply appreciated. Thanks for your time.

---

### Post by taurus on 2007-12-30
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

or

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Prefectionist on 2007-12-30
I'll give those a try, thanks. There'll be an update by tomorrow.

---

### Post by Prefectionist on 2007-12-31
Okay, my mistake; the error had read "Error loading operating system" -- I edited it. 

With the help of my LiveCD I discovered through fdisk -l that absolutely *none* of my partitions "end on cylinder boundary." I'm assuming that's bad news, as it never displayed that before I tried installing XP... Perhaps fixing this will fix my system?
I got GRUB to install on the mbr, but no operating systems will load. Arg.
Help?

---

### Post by kellemes on 2007-12-31
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Taurus gave you a couple of links you need to read too.

---

### Post by Prefectionist on 2007-12-31
I'm going to try that Supergrub program... hopefully it will work.
Still wondering about the cylinder boundaries, though.

Thanks, both of you.

---

### Post by dcstar on 2007-12-31
> **Prefectionist said:**
> I'm going to try that Supergrub program... hopefully it will work.
Still wondering about the cylinder boundaries, though.


Some O/Ss like to have partitions beginning/ending on cylinder boundaries, some (most?) don't.

In the "Olden days" this sort of thing used to help with disk performance a bit, but nowdays with modern disk drives it is basically irrelevant.

If your system works then don't worry too much about the messages.

---

### Post by Prefectionist on 2008-01-01
> 
If your system works then don't worry too much about the messages.

That's just it, though -- it isn't working :(

On a whim, figuring it wouldn't screw anything up more than it already was, I installed Gusty onto the second HD. Well, XP is gone, and I can boot into both Gusty partitions -- I have all my old files back, and I can get rid of the unnecessary Ubuntu on my second HD.

This is a great step in the right direction, especially since I was worried that all was lost, but I still cannot boot into Windows Vista. GRUB doesn't even recognize Vista's recovery manager partition, so it doesn't show up.

I think it's become a whole new case and problem, so I'm going to do quite a bit of clicking around. Maybe Super GRUB will work this time...?

Sigh. If I fix it, I'll post what I did. Until then, insight would be appreciated. Thanks all.

---

### Post by Sef on 2008-01-01
When you partitioned Vista, did you use its partitioner?

---

### Post by Prefectionist on 2008-01-01
Yes, I did use Vista's partitioner. I only got into multi-booting because I don't like Vista, so I've never had to use any other.
There's only been problems since I tried installing XP. I recently read somewhere that Windows acts up unpleasantly unless it's on the first hard drive... so that may be what started it.

---

### Post by HermanAB on 2008-01-01
Well, the basic mistake you made is that you got to install Windoze first and Linux second.  Now you either have to reinstall everything, or jump through some hoops to get the boot loader fixed, since Windoze schkrewed it up for you.  The guys above already gave you the links to the remedy.

---

### Post by Prefectionist on 2008-01-01
Agh. HP never gave me a Vista disk. Just that recovery partition... *grumbles*
Well, if I really *really* need it... I guess I could call in and have them send me one. Maybe I'll get lucky and figure it out in the meantime.

I'll go through the GrubHowTo once more...

fdisk -l:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19741   158565138+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           19742       36996   138600787+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           36997       37732     5911920    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           37733       38913     9486382+   7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           36997       37732     5911888+  82  Linux swap / Solaris
```

and I'm going to try testdisk :(

---

