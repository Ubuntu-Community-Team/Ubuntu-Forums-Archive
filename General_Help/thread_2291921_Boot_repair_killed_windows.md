---
title: "Boot repair killed windows"
date: 2015-08-23
forum: General Help
---

### Post by aaron105 on 2015-08-23
So as the title says I was trying to use ubuntu boot repair to try and fix my ubuntu desktop since the fglrx driver broke it but that's for another post. Anyways now my windows drive isn't even viewed as a bootable drive. When I use the live CD to view the drives connected its still intact at least from what it looks like but nonetheless

---

### Post by yancek on 2015-08-24
The boot repair software has an option to Create BootInfo Summary.  If you can't resolve your problem, it is best to run boot repair with that option selected and post the output here so someone else can view it and possibly give you a suggestion.  You haven't posted any information on your drives/partitions so not much to do.

---

### Post by Bucky Ball on 2015-08-24
For future reference, Boot Repair has nothing to do with graphics or graphics issues. It is for boot problems and sounds like you may have tried to fix something that wasn't broken (I presume you're computer was booting okay prior to installing flgrx?). :)

Please post the bootinfo, as suggested by yancek.

---

### Post by brad-bogar on 2015-08-25
Without further information you might try a simple grub fix. Open a terminal and type: [COLOR=#474534][FONT=Helvetica Neue]sudo update-grub

[/FONT][/COLOR]

---

