---
title: "Can I repartition my Ubuntu drive?"
date: 2006-08-25
forum: General Help
---

### Post by PathSpace on 2006-08-25
I currently have Ubuntu installed on my entire hard drive.  I was wondering if it is possible to resize this drive in order to create a new partition for trying out other distros/OS's (without having to reinstall my Ubuntu).  If this is possible, and I did it, would it be possible to later re-merge the new partition with the Ubuntu partition?  

Thanks for any answers.

---

### Post by BlaineM on 2006-08-25
look up gpart in the forum search.  There might be a how to in there somewhere.

---

### Post by nrwilk on 2006-08-25
yes, all of that is quite easy to do.

Gparted is good, or you can also use qtparted if you use kde.

In order to do what you want to do you will have to resize your partitions first, and then add partitions in the newly created free space.  If you have multiple distributions of Linux running, they can all use the same swap partition, so you do not need to create another.

In order to get your drive back to the way it was, just delete the new partitions and resize your ubuntu partition (or whichever distribution you choose to keep) to fill the drive again.

One other point I'd like to make if you're going to be running multiple distributions is that the new distributions you install will not automatically be added in your boot manager (probably GRUB).  To add them to your boot list, you must edit your /etc/menu.lst file and add the entries pointing to the partitions where they reside.  This can be a little tricky, but each time I've done it I figured it out after a little tinkering pretty easily.  I've successfully installed Fedora Core 5, Open SuSE 10, and Mepis this way.  A good tip that I found helpful is googling to find copies of people's menu.lst files who use the distribution you are trying to install.

So, google for:```
Mepis correct menu.lst
``` You will most probably come across forum posts by people who have screwed their Mepis menu.lst up, and are requesting help from other Mepis users to fix it.  Use the help replies to try to build the correct menu.lst entry so that you can add Mepis to your boot list.  You also may find documentation files which illustrate Mepis' default menu.lst configuration.  That's even better.

I hope I've helped here.  If you have any questions, please continue to ask them and we'll help as much as possible. :)

nrwilk

---

### Post by tormod on 2006-08-25
> **nrwilk said:**
> 
One other point I'd like to make if you're going to be running multiple distributions is that the new distributions you install will not automatically be added in your boot manager (probably GRUB)

It is also awkward that for instance update-grub in one distribution does not update the menu.lst in another distribution, so that you'll have to manually edit the right menu.lst after for instance a kernel update. The best solution to this is:

1. Your first installation (say Dapper on /dev/hda1) installs grub in MBR (hd0)
2. When you install the second installation (say Edgy on /dev/hda2), do not install its grub in MBR, but in /dev/hda2 (hd0,1)
3. Edit your Dapper menu.lst to include
```
# chain load Edgy grub
title Edgy boot menu
root (hd0,1)
chainloader +1
boot
```
This way, each distribution updates its own menu.lst without screwing up the other. For booting Edgy, you'll have to go through two grub menus, but you can for instance hide the second or shorten the timeout.

You can also add this to the Edgy menu.lst:
```
# chain load Dapper grub
title Back to Dapper boot menu
root (hd0)
chainloader +1
boot
```

---

### Post by PathSpace on 2006-08-25
Ok, yeah, it looks like I will use GParted.  Thanks for the help.  :)

---

