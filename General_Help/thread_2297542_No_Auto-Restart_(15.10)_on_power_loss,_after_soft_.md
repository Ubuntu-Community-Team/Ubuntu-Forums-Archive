---
title: "No Auto-Restart (15.10) on power loss, after soft shutdown via 'apcupsd'"
date: 2015-10-04
forum: General Help
---

### Post by jim124 on 2015-10-04
Hello Ubuntu community -
  
I've searched the forums, and scoured the internet, without  resolution to this issue.  I'm running Ubuntu 15.10 (formerly 14) on an  Intel NUC (5i), connected to a Back-UPS 550 via USB cable, and can  confirm the following:

  
[LIST]
[*]apcupsd is installed and working 
[*]BIOS has been set to "Always Resume" in the Power Loss setting 
[*]Basic configuration file exists and appears correct 
[*]Restart-on-power functionality works correctly when *not* using the UPS -- if I pull the plug on the NUC and then reconnect, the unit powers on. 
[/LIST]
  
Shutdown appears to be working correctly in my tests when I pull the  plug on the UPS, unfortunately the unit stays off when power is  restored.

  
It's as if the apcupsd shutdown behavior is causing a normal shutdown  in Ubuntu, instead of indicating to the hardware that an emergency  shutdown took place -- when power is restored to the UPS, the unit  doesn't immediately power-on like it does when not using the ups.

  
What am I missing here?  I've covered a lot of ground online, including: [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

  
Any help is appreciated, and thanks in advance -

---

