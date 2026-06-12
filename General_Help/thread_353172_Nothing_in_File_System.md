---
title: "Nothing in File System?"
date: 2007-02-04
forum: General Help
---

### Post by helliewm on 2007-02-04
Did a reinstall of Ubuntu on my laptop the other day and there is nothing in my File System. On my Desktop there is loads of files in the File System such as /usr  /lib  /etc  /tmp. Where are all these files?

See screensot:

Helen

---

### Post by Choad on 2007-02-04
freaky

it wouldnt work if they werent there... somewhere...

maybe you dont have permission to even look at the folders?

(try opening a terminal and doing a 
gksudo nautilus
and see if you can see something more)

---

### Post by helliewm on 2007-02-04
Could see anything more see screenshot. But take a look at this Screenshot?



Whats going on here?

Helen

---

### Post by Choad on 2007-02-04
what screenshot?

---

### Post by helliewm on 2007-02-04
See above I just had to edit it.

Sorry about that.

Helen

---

### Post by Choad on 2007-02-04
> **Choad said:**
> what screenshot?
oops there they are. ummm yeah. wierd. soz i cant really help u there :S

---

### Post by helliewm on 2007-02-04
Thanks anyway. Anyone any ideas? I just did a normal install of Ubuntu?

I am the only User.
 
Helen

---

### Post by helliewm on 2007-02-04
I think my Ubuntu DVD disc was corrupt hence why there was nothing in the file system. I tried to install again using OEM and it said some files where corrupt. It then messed up Grub. I could not even get SuperGrub to load via BIOS. The only disc I can get to work is SUSE SLED so I will install that. I will then do a completely fresh install ( erasing the hard disc so its a single boot for Ubuntu) of Ubuntu using a Drapper disc and upgrade to Edgy.

SUSE SLED is amazing if there is ever problem its always the one disc you can do a fresh install with. I don't why. I just keep it for that purpose. It came of the front of Linux magazine. 

A long work around but I fairly sure it will work.

Helen

---

### Post by quirt3 on 2007-02-04
Well, you woundln't have has a GUI, I don't think. It sounds like, now, you need to widpe the drive and start over.................

---

### Post by ubu fubar on 2007-02-04
Helen - my Edgy Nautilus displays / the same as your screenshot; just the home and media folders are shown by default, everything else is hidden. Hit Control + h to show the rest.

The filesystem must exist, else your machine wouldn't even boot. What's the output of the 'ls -a /' command?

---

