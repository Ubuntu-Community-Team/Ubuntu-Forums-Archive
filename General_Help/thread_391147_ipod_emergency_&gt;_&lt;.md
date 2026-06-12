---
title: "ipod emergency &gt;_&lt;"
date: 2007-03-22
forum: General Help
---

### Post by Mr. Joe on 2007-03-22
i had a wierd problem with my computer and wound up losing everything on my hardrive, including my itunes library.

So now i have an ipod and i dont want to download...er..buy... all my music again and i was wondering if i could transfer all my music in my ipod to amarok.
I haven't used linux or amarok alot so please keep that in mind.

thanx guys :D

---

### Post by Muzik83 on 2007-03-23
Disclaimer: i dont own an ipod

but...

When you plug the ipod into linux, it should show up as a usb memory device, which you can copy everything off of.  Do this first!  The filenames will be all messed up, but should something bad happen with amarok (for example you sync your empty amarok playlist with your ipod and it erases everything on the ipod...windows media player did that with my windows mobile cell phone...grr!), you will at least have a backup of all your tunes!

When you plug it in, it should automount (remember, I dont own an ipod!).  On a command prompt, type fdisk -l, and you should see something like /media/sda1 and the size of your ipod.  If so, try a 

mkdir ~/ipodbackup
cp -R /media/sda1 ~/ipodbackup

it may be something different than sda1, you can try tab completion to figure out what it is:
cp -R /media/<tab><tab>
should list the contents of media... it may be a name like ipod, or it may be a device name like sda1.

Hopefully you understand this a bit

-sean

---

### Post by hammadr89 on 2007-03-23
I dont know how to get the terminal box in here, so just type this into the terminal:

sudo aptitude install gtkpod-aac


This will install gtkpod, and as far as I can see, it's the best ipod manager available..

---

