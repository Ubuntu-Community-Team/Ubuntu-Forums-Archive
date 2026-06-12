---
title: "[SOLVED] Vista won't let me shrink partition to desired size"
date: 2007-08-25
forum: General Help
---

### Post by 67GTA on 2007-08-25
I am trying to get my new HP ready for Linux. I have disabled page filing, and turned off system restore, and the vista partitioner still won't let me shrink a 450GB!!!! partition to less than 250GB. I have a total of 500GB. That leaves plenty of room to install other OP's, but it is the principle of the thing now. Did I give up some kind of disk management rights when I agreed to Microsofts EULA? How in the !@#$ do I force Vista to shrink to MY SIZE?

---

### Post by mech7 on 2007-08-25
Acronis Disc Director

> **67GTA said:**
> I am trying to get my new HP ready for Linux. I have disabled page filing, and turned off system restore, and the vista partitioner still won't let me shrink a 450GB!!!! partition to less than 250GB. I have a total of 500GB. That leaves plenty of room to install other OP's, but it is the principle of the thing now. Did I give up some kind of disk management rights when I agreed to Microsofts EULA? How in the !@#$ do I force Vista to shrink to MY SIZE?

---

### Post by Sp4cedOut on 2007-08-25
I shrunk a 160 GB Vista partition to 80/80 GB on an HP laptop using Vista's built in partitioner, didn't have any problem.  Is there an error message that's coming up?

---

### Post by 67GTA on 2007-08-25
It had system files at the end of the partition that I couldn't move. In a fit of RAGE I booted Ubuntu live cd and used gparted to resize it. I didn't care at that point if it survived or not. After a file system check and reboot, it reloaded the hard drive driver and all is well. I had seen many horror stories on the forums about using gparted. Vista was installed when I bought it (not by me). The only reason I keep Windows is for games and HP Photo Essential software. I have seen that I have a lot less control over my PC with Vista than with XP. It had better tread lightly:twisted: I still have my XP DVD.

---

### Post by forrestcupp on 2007-08-25
Don't try to use Vista's partitioner.  Download and use the [Gparted Live CD](http://gparted.sourceforge.net/livecd.php).  Boot to the CD and partition away.

---

### Post by merlinus on 2007-08-25
The large system file at the end of the partition is the virtual paging.  You can set it to zero before defragging, and set it back when finished installing ubuntu.

-merlin

---

