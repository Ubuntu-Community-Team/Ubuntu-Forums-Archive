---
title: "GRUB entry removed for XP"
date: 2008-04-08
forum: General Help
---

### Post by Dthdealer on 2008-04-08
Long story

I tried the Ubuntu live-cd. Loved it so I installed it. I thought I partitioned 20 gig to Linux and 60 to Windows, but I got them the wrong way around and so I had half a gig of space left on the windows partition.
Then I though it was annoying that XP was on the bottom of the GRUB boot list, so I cut and pasted it to the top. Saved the boot file, restarted, and worked perfectly.
The next day XP was not on the list. *bugger*
So today I fixed the partition problems by using Gpartition (something along those lines) to fix it. First I shrank the Linux partition to 10 gigs and then realized I can't make the NTFS XP partition any bigger, and so I just formatted another NTFS partition in the free space.
That all worked, but now I am stuck at problem #2-The GRUB entry is gone. All I remember from it' settings was [COLOR="Red"]root(hd0,0)[/COLOR]. I tried adding the following to the end of the file with [COLOR="Red"]sudo nano /boot/grub/menu.lst [/COLOR]
```

title           XP sp2
root            (hd0,0)

```
But now all that happens when I choose the boot-option is that the screen blacks for 2 seconds and then goes back to the GRUB list.

```

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a6709f88-970f-4c99-96$
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a6709f88-970f-4c99-96$
initrd          /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title           XP sp2
root            (hd0,0)

```

I ask anyone who runs Windows XP SP2, and Installed Linux by using the installer's reduce-partition option to install along-side Windows to please post their boot script.

P.S. Linux FTW!
EDIT: I also had removed the memtest option. I really need to lay off the hacking and slicing with machetes I do to the boot file from now on-lesson of life learned.

---

### Post by TeoBigusGeekus on 2008-04-08
Add
```
makeactive
chainloader +1
```
at the end.

---

### Post by Dthdealer on 2008-04-08
Thankyou! Going to restart now.
Wow these forums are fast and helpful!
EDIT: Is thanking disabled for my account as it's new?

---

### Post by Dthdealer on 2008-04-08
Now my only dilemma is that I don't know what to transfer to the second NTFS partition. I wanted to move my program files but that would render the un-installers and all my shortcuts illegit. My documents is only a few gigs, and I can't really think of anything else to move apart from a few hundred megabytes worth of games.

Is it possible to RAID (or merge) partitions?

---

