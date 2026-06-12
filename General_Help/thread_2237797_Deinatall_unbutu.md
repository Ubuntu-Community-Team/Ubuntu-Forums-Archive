---
title: "Deinatall unbutu"
date: 2014-08-04
forum: General Help
---

### Post by roroconsult on 2014-08-04
I have   linux 14-04 and i wouldlike  deinstall  and put   windows XP    .

I have recovery CD but   doent start correctlly !

Is  a sotfware availble to deinstall Unbutu ?

Thanks

---

### Post by Bucky Ball on 2014-08-04
*Thread moved to **General Help**.*

No. No special software required. Boot a Ubuntu Live disk/USB, 'Try Ubuntu' and get to the desktop. Launch Gparted. Delete everything. Shutdown. Boot from XP disk and install. Done.

---

### Post by mooreted on 2014-08-04
If you installed Ubuntu on a computer that has a recovery partition and you have a recovery CD instead of a full Windows XP CD, you probably deleted the recovery partition. You will have to get a full Windows XP CD.

---

### Post by zclock on 2014-08-04
I just wiped my old cp machine, and installed an old version of ubuntu.  Boy am I glad to be back!

Mr. Roroconsult, please sir,  I don't intend to be presumptuous, your choice is your choice.

If I had a wish, I would  wish there were a way to educate the folks out there that there is a better way.  Clean, fast, and cheap and it is only as bloated as I want it to be.  Bye for now, I'm off to find a primer to remind me how easy this can be.  

Even more important to me, once a programmer always a programmer.

Sincerely happy to be back,
and Thank You all for still being here.
):P -Z

---

### Post by coldraven on 2014-08-04
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

No. No special software required. Boot a Ubuntu Live disk/USB, 'Try Ubuntu' and get to the desktop. Launch Gparted. Delete everything. Shutdown. Boot from XP disk and install. Done.

When Bucky Ball said delete everything he probably meant "delete the partition".
So boot from the Ubuntu live CD or USB that you used to install Ubuntu originally.

Then run Gparted, select the drive, then the select partition, right click and choose delete.
The drive should then be seen as "Unallocated space". Remember that for Gparted to finish the job you must click on "Apply" at the top of the window.
After that there is no going back so make sure you know what you're doing and have copied anything important off of the drive.

If you then boot with XP it will see a blank disc and install OK.
This will only work if you have the original XP restore disc for your machine and not one that you borrowed from a friend.

---

### Post by Bucky Ball on 2014-08-04
> **coldraven said:**
> When Bucky Ball said delete everything he probably meant "delete the partition".


+1. ;)

Delete the Ubuntu partition (and any others you don't want).

---

