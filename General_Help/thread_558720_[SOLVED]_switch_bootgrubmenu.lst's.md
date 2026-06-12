---
title: "[SOLVED] switch /boot/grub/menu.lst's"
date: 2007-09-24
forum: General Help
---

### Post by hippomofatumas on 2007-09-24
hi all,

i have two ubuntu partitions, one feisty and one gutsy. The grub boot menu that the comp boots from is on the feisty partition, which i want to format. i got things working in gutsy, dont need it. how do i make the grub boot menu in the gutsy partition the primary one?

thanks

---

### Post by rkillcrazy on 2007-09-24
I'm no Linux guru but I can try to get you started...
```
sudo gedit /boot/grub/menu.lst
```

That command will allow you to edit the OS list.  You should see the following at the top of the page:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default    4   

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

```

The **default num** is usually 0 but this one shows 4 'cause my client boots into Windows more often than not.  Nevertheless, find the number you wish to use and drop it in there.  I'm guessing one of the lines near the bottom of the page will correspond to install you wish to boot into.

If you break it somehow, you may be able to use this [(http://supergrub.forjamari.linex.org/)]("http://supergrub.forjamari.linex.org/") to fix it so you may want to burn a copy before you get too deep into it.

---

### Post by forestpixie on 2007-09-24
I'm not sure if that's what the OP is getting at - after I put gutsy on a seperate partition - I now have 2 menu.lst

the first being the original on the feisty partition - this now has no mention whatsoever of the gutsy installation

the second being the menu written by gutsy - this has both gutsy and feisty on it and this is the one which the pc boots with.

In his case - they are the other way round, but he wants to boot with the menu which doesn't show at the beginning

At least I think that's what he's saying 

and apologies if you're a she :)

Edit - but unfortunately I can't answer question - but will be looking at the answer :)

---

### Post by eggdeng on 2007-09-24
One way would be to use the gparted live CD to change the boot flag from the Feisty to the Gutsy partition. If that works, you should be able to safely delete the Feisty partition. If not, you can always change it back.

---

### Post by bodhi.zazen on 2007-09-24
LOL

You do this with grub.

Boot either feisty or gutsty

In a terminal enter ```
sudo gurb
```

Then at the grub prompt :

root (hdx,y)
setup (hd0)
quit

All you need to know is the gutsy partition in grub speak :twisted:

If you do not know, look here : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Or in gutsy /boot/grub/menu.lst

---

### Post by hippomofatumas on 2007-09-24
thanks bob that worked for me!

i am a guy yeah, so no offense taken. 

Guess that's about it. problem solved, mucho thankso.

---

### Post by logos34 on 2007-09-24
> **hippomofatumas said:**
> thanks bob that worked for me!

i am a guy yeah, so no offense taken. 

Guess that's about it. problem solved, mucho thankso.

mark the thread SOLVED, please.

---

### Post by hippomofatumas on 2007-09-24
what do i do? say solved here?

SOLVED

or something else? i is nooob.

---

### Post by bodhi.zazen on 2007-09-24
> **hippomofatumas said:**
> what do i do? say solved here?

SOLVED

or something else? i is nooob.

LOL ... 

At the top of the thread is a menu "Thread tools"

It is a pull down menu, there is an option to mark as solved.

It helps as others looking to help will know your question has been answered (without having to open and read the thread).

Also others with similar questions might look at the thread as it is marked as solved ;)

---

