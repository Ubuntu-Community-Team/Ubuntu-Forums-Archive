---
title: "Problem with ejecting usb-stick"
date: 2007-04-25
forum: General Help
---

### Post by karl_kashofer on 2007-04-25
Hi !

I am on kubuntu dapper drake, and i have a problem with usb-sticks.

When I copy a lot of data (say 300MB) to my 1GB stick (fat formatted) by just dragging it there with konqueror, and then right-click the usb-stick icon on the desktop and do the safe-remove/eject thing, then remove the stick, the data has NOT been written to the stick. If I plug it back into the same computer or anywhere else the data does not show up on it.

It just seems to me that the safe-remove/eject thing in KDE is not syncing, because if after dragging the stuff to the usb-stick i open a konsole and issue "sync" and safe-remove/eject after that it works fine.

So, am I the only one having this problem ? Its really annoying because if I forget to do the sync in the konsole i walk away without the data. Embarassing....

Thanks, 
Karl

---

### Post by fanatik on 2007-04-25
You'll probably find that it hasn't fully ejected the stick. I don't run kubuntu, but I have a similar issue - I have put it down to being USB 1.1 and that I have to be patient.

If I copy large files to my stick it takes say 10 mins to copy them, but that doesn't mean they have made it there yet! I then run umount in a terminal and the command will hang for another 10-20 mins until the data is fully written, although the stick's icon will disappear from the desktop instantly giving the impression that it has been successfully ejected, when in fact it's still writing. Also I notice that CPU and the load average goes right up - all due to I/O wait.

Maybe this will help you too?

James.

---

### Post by karl_kashofer on 2007-04-25
Hi !

> **fanatik said:**
>  <snip> , although the stick's icon will disappear from the desktop instantly giving the impression that it has been successfully ejected, when in fact it's still writing.<snip>

I see, I will have to check when I come home, but that would make sense indeed.
So its still unmounting and syncing but the icon disappears from the desktop ?

How am I to know when it is safe to remove the stick ?
IMHO it should do the windows thing and display the  "Its now safe to remove drive x" message after successful unmounting.

Wonder why no one else has noticed this, it is very annoying when you are in a hurry, you do the "safe remove" thing and in the end you still have no data on the stick.

How annoying, anyone know if this has already been filed as a bug ?

Thanks,
Karl

---

### Post by fanatik on 2007-05-01
> **karl_kashofer said:**
> 
How am I to know when it is safe to remove the stick ?


I just wait until the prompt returns in the terminal.

As for your other questions/suggestions, sorry I don't know...

---

