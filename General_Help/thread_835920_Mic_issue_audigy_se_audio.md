---
title: "Mic issue audigy se audio"
date: 2008-06-20
forum: General Help
---

### Post by bane058 on 2008-06-20
I have been trying to figure out for about a week to get my mic to work and have been unsuccessful

This is my motherboard
K8N Diamond Plus
[http://global.msi.com.tw/index.php?func=proddesc&prod_no=232&maincat_no=1](http://global.msi.com.tw/index.php?func=proddesc&prod_no=232&maincat_no=1)

and this is the integrated sound
&#8226; Creative sound Blaster Audigy SE audio
- 24-bit / 96KHz audio quality
- Up to 100db SNR clarity
- 7.1 Channel output supported
- Supports S/PDIF digital interface
- PCI 2.3 Specification compliant

The headset is not USB just your standard analog. 

I was able to get sound to work fine on the os level and also using ventrilo with wine. This is sort of a hobby and i would just like to be pointed in the right direction. 

Thanks

---

### Post by ellgor on 2008-06-21
Hi,
 Try this, open a terminal and type in   alsamixer  press enter, and a blocky window will open with some columns in it, which represent your hardware.
Use the arrow keys to move along to Mic which has a little square at the bottom of the column which, if its on will be green, if its not press m to enable it, also if the volume looks to be low on any of the channels now would be a good time to change them using the up and down keys, hope this is of help.

Regards, Ellgor.

---

