---
title: "Failure to Recover from Suspend - NE71B"
date: 2014-12-09
forum: General Help
---

### Post by mcman56 on 2014-12-09
I have a system that fails to recover from suspend.  A forced shutdown and reboot is required to get going again.  It is possible that the system partially recovers but the monitor does not.  Hitting all buttons and moving the mouse have no effect.  Pressing the power button has no effect until it is held down long enough to force shutdown.  The issue was there with the last LTS Ubuntu version also.  I see various and random methods in the forum to try to correct but am wondering if there is anything specific for this hardware.

   
  I did find this:
  [http://manpages.ubuntu.com/manpages/trusty/man8/pm-action.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/pm-action.8.html)
  Is there a systematic method or do you just sort of stumble though and try each quirk hoping not to create a more serious issue?



  Ubuntu 14.04 LTS - 64 Bit - Gateway NE71B laptop

---

### Post by leunam12 on 2014-12-09
Many times this is due to graphic driver issues. Every time I have had this problem I solved it by installing other graphic drivers. Check to see if there are other drivers available for your graphics card; or if you have proprietary drivers installed remove and install open source ones.

Hope it helps.

---

### Post by mcman56 on 2014-12-09
Can you point me to some directions or a reference for installing other drivers?  I have only done this in windows but don't see anything like control panel here.  I see displays in system settings but don't see how to load other drivers.  Thanks

---

### Post by leunam12 on 2014-12-10
The name of the utility is "Additional Drivers" it used to be a stand-alone application but I think now it's been merged with the "Software and Updates", last tab on the right.

---

### Post by mcman56 on 2014-12-11
The system offered a couple of proprietary drivers.  I tried one and it now works.  Thanks!!

---

### Post by leunam12 on 2014-12-12
Woohoo!!

---

