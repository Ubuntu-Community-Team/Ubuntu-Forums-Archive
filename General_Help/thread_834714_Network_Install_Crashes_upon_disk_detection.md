---
title: "Network Install Crashes upon disk detection"
date: 2008-06-19
forum: General Help
---

### Post by kdepa on 2008-06-19
I have a Sun Netra X1, with the PROM upgraded to the latest firmware that I've been trying to install Gutsy on over the network.  Everything seems to work ok until it crashes at "Detecting disks and all other hardware" in the same place every time.  It reaches 5%, says it is "Loading module 'via82cxxx' for 'IDE chipset support'..."  then I get an error that is partially cut off that says 

"eference
[   636.999234] tsk -> {mm,active_mm}->context = 00000000000003b0
[   637.072437] tsk->{mm,active_mm}->pgd = fffff800006ae000"

What could be causing this error?  Unfortunately this is all done over a VT100 console connection, so I do not know of any ways of looking at the alternate consoles to see if there are any revealing clues.

---

### Post by kdepa on 2008-06-20
I have solved the problem - at the "ok" prompt, if I use "boot net ide=nodma"  I do not have an issue.  And actually, I found the mirror for the hardy SPARC port and have had slightly more luck with that - haven't had to append nodma.

---

### Post by kdepa on 2008-06-20
Okay, now I am having a weirder problem.  I am installing Hardy Heron over the network, and everything goes fine until the "Select and Install Software" step completes.  The screen simply blanks, and doesn't do anything.  I am not sure, but I think this may be the part where the installer is supposed to put SILO on the drive.  Are there any workarounds for this?

---

### Post by pacarey on 2008-06-20
I had problems with SILO and installing Hardy on a Ultra 10. It may seem a bit daft, but if you have sorted out your network problem. Try installing gutsy first and see if that works. If it does, then update to hardy from that. 

My post on another topic [http://ubuntuforums.org/showpost.php?p=5003326&postcount=5](http://ubuntuforums.org/showpost.php?p=5003326&postcount=5)

Good luck.

Paul

---

### Post by kdepa on 2008-06-20
That worked!  I actually had to go all the way back to dapper to get the OS to install.  Now to update it to hardy.

Thanks so much!

---

