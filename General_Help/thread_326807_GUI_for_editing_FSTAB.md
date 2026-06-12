---
title: "GUI for editing FSTAB?"
date: 2006-12-28
forum: General Help
---

### Post by jrohde on 2006-12-28
Hi,

I've been searching for a tool to help me in editing fstab, but I haven't found any. Does such a tool exist (for Edgy/Gnome)?

Thanks,

Jakob

---

### Post by Olav on 2006-12-28
> **jrohde said:**
> Hi,

I've been searching for a tool to help me in editing fstab, but I haven't found any. Does such a tool exist (for Edgy/Gnome)?

Thanks,

Jakob

I always use gedit or even nano as a "GUI" of sorts, in other words, an editor. What sort of problem would another GUI solve for you?

---

### Post by jrohde on 2006-12-28
I'm not familiar with the new syntax of fstab (see below). So it would be nice to have a tool so    I'm sure to get the details right.

What I need to do, is to add /dev/sdb1 at /home/data.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc9cb5a2-30eb-431e-b51f-8f6301c9e290 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0b04d987-8dc3-494c-be33-5b783a59df96 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Jakob

---

### Post by hadiriazi on 2006-12-28
> **jrohde said:**
> Hi,

I've been searching for a tool to help me in editing fstab, but I haven't found any. Does such a tool exist (for Edgy/Gnome)?

Thanks,

Jakob

Hey there

What sort of things you would like to be able to do in the GUI? I'm  a developer and I could write an app for that, and love to write something that every one in the community could use. So please identify what sort of stuff you would like in the GUI and I'll be glad to work on it.

Thanks

---

### Post by bulldog on 2006-12-28
Maybe is this of some assistance for TS,

[http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572](http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572)

---

### Post by hadiriazi on 2006-12-28
> **bulldog said:**
> Maybe is this of some assistance for TS,

[http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572](http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572)

Thanks for the link, seems very useful.
You think I should start on that app?

---

### Post by dannyboy79 on 2006-12-28
anytime you don't know how to do something or are unsure of the syntax or whatever it always helpful to check out the man pages (manual) so from a terminal you would type man fstab and it will tell you exactly what all the different fields mean. 

and to the developer who asked if he should create a gui for modifying fstab. Why not, if you have the time then do it. You can be sure that newbies everywhere will use it. That was something I was going to do in Python myself as my first program/gui. If python can even do guis? I don't know how to program but am trying to learn.

---

### Post by bulldog on 2006-12-28
> **hadiriazi said:**
> Thanks for the link, seems very useful.
You think I should start on that app?

Well,if you have the time,give it a go :D 

But I think there should be a more useful thing to make,fstab is only for the mounting part,and not to many users will have to deal with it.
A simple text editor like gedit or nano can do the trick,if you have to alter it for some reason.

If you want to make an application for the users,start a Poll and let them give you ideas in what to make.

---

### Post by dannyboy79 on 2006-12-28
> **bulldog said:**
> Well,if you have the time,give it a go :D 

But I think there should be a more useful thing to make,fstab is only for the mounting part,and not to many users will have to deal with it.
A simple text editor like gedit or nano can do the trick,if you have to alter it for some reason.

If you want to make an application for the users,start a Poll and let them give you ideas in what to make.

what I did when I installed ubuntu was unattach all my hard drives (except one obviously) due to not wanting to accidentally delete any data. then when I had it installed I rehooked the hard drives and was very intimidated when I opened fstab not to mention it took me a couple hours to figure out what I had to do to begin with so a program to do this would be excellent for newbies!

---

### Post by fragos on 2006-12-28
You can change fstab by using gparted which you'll need to install with Synaptic.  You don't have to change partition size or reformat to use gparted.  You can just change the mount point directory name and fstab will be fixed for you.

---

### Post by po0f on 2006-12-28
[EDIT]

Nevermind...

---

