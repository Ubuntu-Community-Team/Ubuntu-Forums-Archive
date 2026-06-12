---
title: "No wireless, no volume control in 8.04, 8.04.1 with Thinkpad R40"
date: 2008-07-06
forum: General Help
---

### Post by JEBB on 2008-07-06
IBM Thinkpad R40:  It works fine with Ubuntu 7.10 but with 8.04 and 8.04.1 the wireless card is not recognized nor is the volume control.  How can the programmers let this happen?  Thinkpads are among the most popular computers out there.  

Should I put this computer away and wait for 8.10?  I certainly am glad it isn't my only computer.

---

### Post by Quickdood on 2008-07-06
I am having the same problem with my Thinkpad T42, I can't map my "access ibm" button or my volume controls.  Been searching for a bit but haven't found a fix yet.  If you find one please post it here, I will do the same.

---

### Post by ajlewis2 on 2008-07-06
This happened to me with this wifi: Intel Corporation PRO/Wireless 3945ABG

Check if you have that one.  If so, you need to blacklist the old module and put the new one in /etc/modules:

At the bottom of /etc/modprobe.d/blacklist, add this:
blacklist ipw3945

At the bottom of /etc/modules add this:

iwl3945

I had the sound problem too.  I had to go into the mixer and turn on Front.  I have no idea what that was about.  I think that was all I did.

Anita

---

### Post by ukripper on 2008-07-06
> **JEBB said:**
> IBM Thinkpad R40:  It works fine with Ubuntu 7.10 but with 8.04 and 8.04.1 the wireless card is not recognized nor is the volume control.  How can the programmers let this happen?  Thinkpads are among the most popular computers out there.  

Should I put this computer away and wait for 8.10?  I certainly am glad it isn't my only computer.

Switch back to 7.10. updates support is till april 2009 for gutsy (7.10)!

---

### Post by Sef on 2008-07-06
Moved to General Help.

---

### Post by icheyne on 2008-07-22
One of my friends has this problem too.

---

### Post by pmlxuser on 2008-07-22
> **JEBB said:**
> IBM Thinkpad R40:  nor is the volume control.  How can the programmers let this happen?  

I know you can associate certain key with certain function using the
menu> system> preferences> keyboard short cuts

You specify there Volume up :(some key) the same for volume down, start email program etc.

> 
Thinkpads are among the most popular computers out there.  

I can't comment, the last thinkpad I had was not that cool now i prefer Acer (just personal preference & may be because its cheaper than Think pads :) )

---

