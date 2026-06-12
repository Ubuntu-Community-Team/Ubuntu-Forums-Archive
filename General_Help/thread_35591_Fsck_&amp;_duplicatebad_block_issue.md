---
title: "Fsck &amp; duplicate/bad block issue"
date: 2005-05-19
forum: General Help
---

### Post by Cordate on 2005-05-19
My system ran a system check yesterday on its 30th reboot and found and fixed some errors, but then got stuck here:

```
ERROR: Module aec62xx does not exist in proc/modules
ERROR: Module piix dpes not exist in proc/modules
* Mounting a tmpfs over /dev....     [ok]
* Creating initial device nodes....    [ok]
* Setting disc parameters......         [ok]
* Checking root file system...
/ contains a file system with errors, check forced.

Duplicate or bad block in use!
(There are 1 inodes contaning duplicates/ bad blocks.)
file etc/hotplug/usb (inode #622895, mod time Thu Nov 18 16:04)44 2004)
had 1 duplicate block(s), shared with 1 file(s):
     <filesystem metadata>

UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
  (i.e. without -a or -p options)
fsck failed. Please repair maunally and reboot. 
Please note that the root file system is currently mounted read-only. 
To remount it read-write:
 #mount -n -o remount, rw/
```

I'm pretty much a newbie, and web searches didn't reveal much in the way of information about this kind of thing. Where do I go from here??

_____________________

Ok, so after a few days of messing around (and finding clues here and there on the web) I've figured out how to get things working again. For those who might have similar troubles, here's what I did:

**1)**  Boot the pc with the Ubuntu install disk in the hard drive. 
At the install prompt, type "rescue" and hit enter. 
Go through your language and location options and such, choose a partition to mount from (I was shown 3 options but the lower 2 did not work for me- I think they were my CD drives).

**2)**  Once you are in the shell, type "mount" to see what's mounted. My root is /dev/hda1. I don't know if the info at the end indicates errors or not, but mine said 
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
```

**3)**  Type 
```
mount -no remount,rw /dev/hda1
```(substitute dev/hda1 with whatever your problem area seems to be) to mount that partition as read-write. I'm not sure this step is neccesary, but hey, this worked for me. I'm also unsure if this is the exact thing I used. Mess around with the -no (maybe it was just -n) if you can't get this to work.

**4)**  Type ```
umount /dev/hda1
``` to unmount that partition. If you don't do this first, trying the next step will give you a big scary warning message. I chose to heed the warning and my system is up and running again :) 

**5)**  I typed "mount" at this point, and it still looked like /dev/hda1 was still mounted, but  fsck let me run it (the next step) without the warning, so I figured dev/hda1 wasn't really mounted. 

**6)**  Type ```
fsck -rfv dev/hda1
```and fsck will run and check stuff out. It'll ask you questions about if you want it to fix this and that. I said yes, you may know better than I on what to choose in your situation :) 

I only had a few fixes to make- if your system is really messed up, you might want to check fsck's options (type "fsck -h") for ways to automate the repairs. Eventually is will be done doing its thing and you will be ready to exit the shell. I think I did that with CTRL-D. 

**7)**  The home stretch... the shell then gave me some message about being kicked out of the shell- maybe this was because the boot drive was unmounted?- I chose "no" at the prompt and my system went off to reboot, and happily this time *hurrah!* 

Now I feel smarter (a little bit) and have this great reward of a now-functioning computer!

 \\:D/ 

-Cordate

---

### Post by N17R0 on 2005-05-28
Good one, you saved me some time to find out how to fix my dead Kubuntu.   \\:D/

---

### Post by chascon on 2005-05-29
or you could just log as sudo as the check suggested and run fsck on the partition that was identified as bad.
"fsck /target"
then reboot when it is done.

Which is what you should do immediately anyway because the more you use a partition with errors the more damage you cause.

---

### Post by Safyre on 2006-02-11
Hmm, I'm having trouble with this same problem. I don't have a Live CD to boot up with- and I've had this problem before. I vaguely remember a fix that involves changing a line in GRUB to something magical, wonderful and grand that allows me to bypass sudo so I can actually get to run fsck. 
All I need to do is get around entering the root password for maintenance. Despite searching, my fatigue addled mind has not given me the ability to remember what I'm looking for in that magical 'open sesame' of GRUB. 

Help! I have essays and papers hidden in my beloved Ubuntu box- and I need them!

---

