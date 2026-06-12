---
title: "system&gt;administration&gt;disks.....?"
date: 2007-03-26
forum: General Help
---

### Post by thedarkharlequin on 2007-03-26
I just installed ubuntu 6.10 on my dell laptop and so far most everything has worked correctly except...  
On trying to get my windows partition to be viewable in linux, following the directions in the guide as stated here:
> Make Windows partitions available from Ubuntu

Windows partitions should be automatically available from any Ubuntu system. If they are not, you can make them available using the Disks Manager.

   1.

      Open System->Administration->Disks .
   2.

      Select the correct hard disk, and click Partitions.
   3.

      Select the relevant partition, and click Enable.
   4.

      To unmount the partition, click Disable.



EXCEPT


system>administration>disks 
does not exist in my toolbar......

I was able to mount the partition through terminal, but it's only accessible by the root user.


so my 2 questions are:

what would cause the "disks" utility to be missing?

and

how do I make a mounted partition accessible to all users?

---

### Post by prion on 2007-03-26
I'm having that identical problem on a Dell XPS desktop.  The volume is mounted and visible on the desktop, but I can't give myself permission to view it.

_prion

---

### Post by zvacet on 2007-03-26
I´m not quite sure,but I belive that is tool from Dapper and not exist in Edgy.

---

### Post by thedarkharlequin on 2007-03-26
well if that tool is not available in edgy it should be removed from the 6.10 online manual.

regardless, I figured out what I was doing wrong in setting up my fstab to mount on boot, so now it mounts at startup and is accessible by all users.

side note curiosity, is there anyway to open up a root file manager under another users account.  I know I could do that in knoppix, but it was already a pull down option so I don't know what I would do to recreate the effect in ubuntu.

---

### Post by prion on 2007-03-26
Could you post the changes you made to your fstab?  I'm still having some trouble accessing the volume.  Thanks!

---

### Post by dcstar on 2007-03-26
> **thedarkharlequin said:**
> well if that tool is not available in edgy it should be removed from the 6.10 online manual.
........

The **pysdm** package gives similar functionality in Edgy.

Look for "Storage Device Manager" in the admin menu once you install it.

---

### Post by thedarkharlequin on 2007-03-26
as far as my changes to fstab, the only problem I was running into was my own incompetence and inattention to detail.  or shortly put, typos.  but my addition to fstab was
> 
/dev/hdc1   /media/windows    ntfs   umask=0222   0   0


and once I had that saved "correctly" and a reboot it worked fine.

as far as just a standard "mount" through terminal, I never did figure that out.  It has something to do with the "  -o  " switch with a "  ,users  " option, but I could never figure out the proper way to input it.  I R Noob.

dcstar:
thanks very much for the reference to pysdm.  that was pretty much exactly what I would have wanted.

prion:
you might want to try pysdm as well, it might at least give you an idea of where to start on your problem. if nothing else you should be able to mount your file system to where you can access it, even if it's not done automatically at boot time.

---

