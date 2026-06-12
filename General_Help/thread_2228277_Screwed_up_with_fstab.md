---
title: "Screwed up with fstab"
date: 2014-06-06
forum: General Help
---

### Post by jgw on 2014-06-06
I was trying to get another hard drive to mount at startup.  I, obviously, screwed up when I edited the fstab file.  I do have a backup but cannot copy that to the original because its all read only when one is in manual recovery so there is no way to edit or replace the offending file (as far as I know (which isn't a whole lot))  Anyway, I then found a boot repair disk which I duly downloaded and burned.  I booted off that and got a bunch of options although what I was really hoping for was a way to get to that fstab file and replace it with the one that worked.  Due to my confusion I pressed enter.  When I did that the drive duly whirred for a bit and then stopped, for quite a while, and then whirred some more and then stopped, again for a while.  This happened a couple of other times so I got out of that thing and am writing this whilst I download the iso file again (my thought is that perhaps the download was bad).

Forgot - I am running with 14.04 and, I think, the repair disk is at 13.??

Anybody got any thoughts on this one?

Thank you.........

---

### Post by sudodus on 2014-06-06
You have probably got a CD/DVD/USB Ubuntu install disk/pendrive. You can boot from it, mount the root partition on the internal drive and do the copying and editing necessary from that drive. That way you will have a well-known environment (the live session is quite similar to the installed system).

Mount it like this or similar (depending on where you installed your Ubuntu)

```
sudo mount /dev/sda1 /mnt
```

---

### Post by jgw on 2014-06-06
thank you!!  I will give it a shot.....

---

### Post by jgw on 2014-06-06
I still can't edit or delete the file as it remains read-only  I tried gksu but that is not installed and live can't find it.

---

### Post by jgw on 2014-06-06
I got it fixed!  Here is what I did.  I setup a super user password (sudo passwd root) and then I was able to deal with the offending file.  thanks again for the help!!

---

### Post by ajgreeny on 2014-06-06
In the live session try using ```
sudo nano /mnt/sda1/etc/fstab
```changing the /mnt/sda1/etc/fstab to wherever your installed system is mounted.  That will open the file in the command-line text editor called nano with root privileges.

Now using the cursor keys you can navigate to the erroneous line or lines in fstab, edit them back to what is needed, then press Ctrl+X to exit the file and finally Enter to save it.

EDIT:
I'm glad you got it fixed.  I hope you set a root password only in the live session, not an installed system.

---

### Post by jgw on 2014-06-06
Yep, only the live session (only place I really needed it <G>)  thanks!

---

