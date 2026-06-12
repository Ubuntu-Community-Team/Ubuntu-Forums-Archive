---
title: "What do These Words Mean at Boot UP?"
date: 2017-05-25
forum: General Help
---

### Post by happydog500 on 2017-05-25
After over a year of trying, we had to come to the conclusion that ubuntu just won't work with my computer. We tried everything. It's well documented we can't get Linux to boot up with DVI-0 as default, and VGA-0 as secondary (with ubuntu MATE, not at all) on this computer.

 I was booting up the live DVD (Ubuntu MATE 16.04), and clicked "esc". I saw this at boot up;
  
  ```
[    7.855293]  [drm:radeon_dp_link_train [radeon] *ERROR* channel eq failed: 5 tires
[    7.855293]  [drm:radeon_dp_link_train [radeon] *ERROR* channel eq failed
[  12.877928]   [drm:atom_op_jump [radeon] *ERROR* atombios stuck in loop for more then 5seconds aborting
[  12.878012]   [drm:atom_execute_table_locked [radeon] *ERROR* atombios stuck excuting E262 (len 2585, WS 4, PS 4) @ 0xE94C 
```


  I searched older threads and could only find people saying this is telling you it won't work. 

  What does this mean? Does this tell us anything as to *why* the video doesn't work right? And as a last ditch effort before I have to give up to get Ubuntu to work, does this give us a specific thing to do? 

 Thank you, 
Chris.

---

### Post by oldos2er on 2017-05-25
Can you tell us the exact make/model of your video card?

---

### Post by happydog500 on 2017-05-25
> **oldos2er said:**
> Can you tell us the exact make/model of your video card?

 Radeon HD 6410D

  Been checking around more since I discovered the words. Absolutely will not work with Linux. Something like (my way of explaining it) Linux reeds the BIOS as both monitors, kind of like one, and not one and the other. 

 Makes sense, since Linux can't distinguish between what monitor to use. Some distros when I use xrandr info and put DVI as default, it will switch to VGA. Others the icons will go on DVI and the pannel will go on VGA. The limitations of the O.S. can not see the monitors as different with this hardware. 

   First discovered in 2012 (can't remember if it was version 12 or 2012), but was suggested it would get fixed later on but didn't.

  What does the words mean besides "you have big problems and it will not work?"  
 
 Thank you, 
 Chris.

---

