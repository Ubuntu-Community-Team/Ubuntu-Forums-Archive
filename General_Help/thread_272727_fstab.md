---
title: "fstab?"
date: 2006-10-06
forum: General Help
---

### Post by lemonsCC on 2006-10-06
I am trying to make a partition on my HD mount as "shared" currently it mounts and it is called "_PNG"  I tried creating a new directory in /media and pointed fstab to it, unmounted and remounted and it is still called "_PNG."  What am I doing wrong?

---

### Post by CatKiller on 2006-10-06
I think that's to do with the volume label of the disk. I don't know how to change it though.

---

### Post by lemonsCC on 2006-10-06
If I am not completely insane...Windows (this is a dual boot box) can change that volume label.  Would this carry over to Ubuntu?


Ahh hell, i'll just try it.  Cant be too bad?

---

### Post by CatKiller on 2006-10-06
I'm quite interested in the results. Don't forget to post back.

---

### Post by lemonsCC on 2006-10-06
It works.  The _PNG was some crazy windows thing.  Go into windows as an admin and make the label of the drive whatever you so desire.  Reboot in Ubuntu and it will be called that.  Much better than seeing "hda5" or "_PNG"!

---

### Post by CatKiller on 2006-10-06
Excellent. I'm sure there is a way to do it under Linux, but I couldn't make gparted make a label for a FAT partition a while ago. Booting into Windows to do it seems quite quick and painless. Glad it worked for you.

I've not had a problem with it, since I don't mount partitions in /media, and so I don't get icons on the desktop. I wonder if changing the name of the icon is possible, and whether **that** would use the right command to change the volume label by Nautilus voodoo? Doesn't matter for you now, though, just a thought experiment.

Thanks for letting me know.

---

### Post by lemonsCC on 2006-10-06
The mounting in media makes it 100x easier for the other users and its only 1 extra icon so its not too much clutter.

I cant change the name in nautilus...what is voodoo?

---

### Post by CatKiller on 2006-10-06
> **lemonsCC said:**
> The mounting in media makes it 100x easier for the other users and its only 1 extra icon so its not too much clutter.

Absolutely. I think it's a great feature. I just don't want the icons on **my** desktop, so I've never had to worry about the labels being ugly.

> I cant change the name in nautilus...what is voodoo?

Voodoo - Magical practice considered to be a form of black magic but also is considered a religion to some.

---

### Post by lemonsCC on 2006-10-06
> **CatKiller said:**
> Voodoo - Magical practice considered to be a form of black magic but also is considered a religion to some.

ROFL  I thought you were talking about a script or add on!  :D

---

### Post by strabes on 2006-11-03
what are the advantages of mounting something in /media as opposed to /mnt ??

---

### Post by CatKiller on 2006-11-03
> **strabes said:**
> what are the advantages of mounting something in /media as opposed to /mnt ??

You get an icon on the desktop.

I think that's about it.

Conversely, for me, **not** having an icon on the desktop is an advantage of not mounting in /media.

---

### Post by strabes on 2006-11-03
Oh ok thanks for the quick reply. I would agree with you on that one because I don't like having any icons on my desktop. I didn't realize that /mnt wouldn't put an icon on the desktop so that's good to know.

---

### Post by lemonsCC on 2006-11-04
The users on this computer are icon lovers.  Personally I like the dock of OS X and could store JUST ABOUT everything there.  With Spotlight I usually search for many things, its quicker than opening my home folder and wading through folders...

---

