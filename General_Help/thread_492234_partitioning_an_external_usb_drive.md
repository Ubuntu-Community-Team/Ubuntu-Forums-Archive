---
title: "partitioning an external usb drive?"
date: 2007-07-04
forum: General Help
---

### Post by tetsura on 2007-07-04
hey,
running ubuntu on my laptop but iv totally run out of space on both my ubuntu and xp partitions so i got a 320gb external usb drive today.
i was wondering if its possible to create directorys on the drive which would be used for my home folder, and another where apps get installed by default, instead of them getting installed to my root partition?

failing this is there a way of partitioning the drive to this effect? id really rather not have to reinstall ubuntu though.

thanks in advance, sorry if none of that makes sense

---

### Post by kidders on 2007-07-05
Hi there,

I wouldn't recommend putting your home directory on a USB device ... you'd have to leave it connected all the time (which would be a waste of money ... internal drives are cheaper), and it would be slow.

If you *really* want to move /home there, it's pretty trivial though. Just boot in single user mode, and go from there.

---

### Post by tetsura on 2007-07-06
thanks for the reply.
hmm ok. i dont think its worth the effort because i can just link to folders on the usb from my home folder.
what about applications though? i found out about them installing in loads of different folders, so i guess that means its impossible to get them to install on the usb?

this is really annoying because i dont want to have to reinstall ubuntu on the usb because i want to be able to run ubuntu without having the usb drive with me all the time. i dont think i have a choice though because my 3.8gb linux partition isn't gonna cut it.. :(

any suggestions? 
thanks

---

### Post by kidders on 2007-07-06
If you want to be able to use your Ubuntu without the USB disk plugged in, then you really shouldn't try to install any apps on it. :-(

It is *possible* to keep Linux on a 3.8GiB partition ... but you'd have to run a pretty tight ship, uninstalling anything you felt you didn't really need, routinely cleaning temporary data & caches, and so on. Out of interest, I just looked at the size of mine ... excluding any personal files & some of my larger things (games, chroot environments, etc.), I'm using nearly 9GiB.


My best suggestions, depending on how much space you need to get back are ...
[LIST]
[*]Uninstall/delete anything you don't want.
[*]Delete Windows XP hehe.
[*]Switch to a Linux distro that leaves a smaller footprint than Ubuntu.
[*]Buy a small internal hard disk. Something around the 80GiB mark should cost next to nothing, these days. Even an extra 20GiB would probably be a big help to you![/LIST]For me, running part of my OS off a USB device would be an absolute last resort. One other possibility (that might give you back a small amount of space) is to investigate whether any of your filesystems have any reserved blocks that you could reallocate to normal use.

By the way, it's worth mentioning (just in case you really do run out of space *altogether*) that Linux reacts **very badly** to having literally no space on its root filesystem. It's something you'll want to avoid allowing to happen.

---

### Post by tetsura on 2007-07-06
internal hard drive isnt really an option cos iv got a laptop.

grr this is well annoying, i bought this hdd thinking it would solve all my problems but now iv realised theres nothing i can move onto it really because i dont want to go without music or apps if i dont have the hdd with me. 

tbh though 90% of the time im using my laptop at home so i guess il just move some stuff anyway, probably the windows apps.
i could resize the ntfs partition then right? and give more space to the linux partition?

cheers

---

### Post by dabl on 2007-07-06
3.8GB is too small for Ubuntu root -- I wouldn't try it with less than 6GB (mine is 10GB).  If you can fix that problem, then here's how to set up your external USB drive as a NTFS formatted drive, for storage of data from either Windows or Ubuntu.

[http://kubuntuforums.net/forums/index.php?topic=3084679.0](http://kubuntuforums.net/forums/index.php?topic=3084679.0)

:popcorn:

---

