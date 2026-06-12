---
title: "stop floppy module from loading"
date: 2007-11-03
forum: General Help
---

### Post by Pathfinder_ on 2007-11-03
How do I stop the floppy module from laoding?

I put "blacklist floppy" in /etc/modprobe.d/blacklist.
put '#' in front of the the floppy entry in fstab. 
rebooted and it still loaded. 

I also tried doing ```
sudo rmmod floppy
``` but it says that module is in use. 
Is there a way to remove the floppy module or stop it from loading because i cannot run gparted since it scans for a floppy that isn't there.

EDIT: just looked in /etc/modprobe.d/aliases file and could not find a floppy module there

---

### Post by Pumalite on 2007-11-03
Did you tick off floppy in BIOS?

---

### Post by Pathfinder_ on 2007-11-03
I just tried that and it still loads the floppy module. :(

---

### Post by ajgreeny on 2007-11-03
I'm not sure if this will help this but there is a utility called sysv-rc-conf which you can find in the repos and attached is a text file about using it which you may find useful.  I can't see anything about floppy disks, but haven't got it running so far on this setup, though had it before on versions of ubuntu and used it to get rid of several startup items not needed on my system.  It's a bit like a detailed terminal version of bum, boot-up-manager, and will do a lot more if you want it to, but use it with caution as you could stop services which are essential without realising it.

---

### Post by Pathfinder_ on 2007-11-03
I ran that program and got rid of some extra stuff that was being loaded which sped up my boot time :) However, there was nothing about floppies. :(

---

### Post by ajgreeny on 2007-11-04
Yes, I loaded and ran it again myself and noticed that too.  Sorry I can't help further.

---

