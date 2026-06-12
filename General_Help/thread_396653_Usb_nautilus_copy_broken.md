---
title: "Usb nautilus copy broken"
date: 2007-03-29
forum: General Help
---

### Post by JcZndeR on 2007-03-29
I can't seem to copy things on to anything connected with a usb anymore with nautilus, so could someone please tell me how you copy entire directories with the command line or somehow fix the usb problem im having.
its only with nautilus, if i copy someone on to a flash drive or an external hdd then it looks like it copied but when you remove and plug back in, its not there....
i need to backup up my entire home so copying files one by one is not an option.. im formatting my computer and in a bit of a hurry
thanks :)

---

### Post by neoaddict on 2007-03-29
Did you right-click your flash drive on your Desktop and select Unmount?

---

### Post by JcZndeR on 2007-03-29
hmm.. i dont see an unmount
im using an external drive right now...
and i dont think i had to do that before..
its worked once upon a time

---

### Post by neoaddict on 2007-03-29
> **JcZndeR said:**
> hmm.. i dont see an unmount
im using an external drive right now...
and i dont think i had to do that before..
its worked once upon a time

But the icon is on the desktop, and the unmount option when you right-click is greyed out or something?

If not, what is in the menu?  :)

---

### Post by JcZndeR on 2007-03-29
hmm...
the normal ones
open
browse
scripts
cut
copy
make link
rename
move to wastebasket
stretch icon
restore icon size
properties
eject

---

### Post by yabbadabbadont on 2007-03-29
Eject is the option you want.

---

### Post by JcZndeR on 2007-03-30
ohh... thx
but how do i send it after i unmount?

---

### Post by nchase on 2007-03-30
Correct me if I'm wrong, but I think what he's saying is send the files, then unmount/eject. 

It seems that with Ubuntu Linux, you need to "eject" removable media for the files to actually be written to it.

---

### Post by hikaricore on 2007-03-30
> **nchase said:**
> It seems that with Ubuntu Linux, you need to "eject" removable media for the files to actually be written to it.


That's correct.

USB devices which don't have an actual drive in them such as, flash drives and thumb drives (and whatever the hell else they're called these day) have to be "Ejected" to have the files actually written to them.  
External hard drives usually write directly, but should also be "Ejected" just in case to avoid data loss.

So as a general rule order of events go like this:  save/copy files to usb drive -> eject -> complete

I believe it is possible (read a howto somewhere in the forum) to write directly to the flash device.  But this process writes very slowly and isn't always reliable.

---

### Post by yabbadabbadont on 2007-03-30
The files will be written to the drive without ejecting it, eventually.  They sit in the filesystem cache and get flushed to disk every so often.  All the eject command does is to properly umount the drive, which forces a flush of the filesystem cache, so that it is safe to remove it.  If you want to force the data to the drive, but don't intend to remove it, just open a terminal window and run the "sync" command.  Once that completes, the data should be safely on the drive.  You still need to use the eject command before removing USB media though, as it properly umounts the drive.  If you don't, you risk data corruption on the drive even if you have used the sync command first.

---

### Post by JcZndeR on 2007-04-01
oh. lols
thank you
because i was sure it worked before
anyhow, the command line seems to write things immediately
problem solved, thx again

---

