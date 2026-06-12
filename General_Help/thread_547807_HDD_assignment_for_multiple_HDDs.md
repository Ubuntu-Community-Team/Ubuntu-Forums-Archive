---
title: "HDD assignment for multiple HDDs"
date: 2007-09-10
forum: General Help
---

### Post by jdogzilla on 2007-09-10
Hello, I have 1 SATA and one IDE HDD.  Ubuntu is on the SATA drive, and the IDE drive is only used for data.  The problem I have is that whenever I make any modifications to the BIOS, grub breaks as it thinks that the IDE HDD is the primary drive.  To remedy this, I need to unplug the IDE drive, boot with only the SATA drive, and then plug the IDE drive back, and reboot back into the system. 

Is there anything I can do so that updating the BIOS will not require me to do this.  Should I set the pins on the IDE HDD to be secondary instead of master (currently they are set to master)?  Or should I just set the IDE HDD as a secondary IDE drive in the BIOS?  

Thanks

---

### Post by bodhi.zazen on 2007-09-10
Try setting the pins to cable select (which seems to fail for me) or slave (IDE)

set the pins for the SATA to master

HTH

---

