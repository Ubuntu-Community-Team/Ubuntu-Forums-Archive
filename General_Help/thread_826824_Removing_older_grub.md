---
title: "Removing older grub"
date: 2008-06-12
forum: General Help
---

### Post by reb68 on 2008-06-12
I have been upgrading whenever notified and like to stay up to date. BUT I now have in Grub (I have Linux on one drive and Windows on another, only because I need Windows to track my sugar) ver. 2.6.22-14 to 2.6.24-18. Not counting Windows I have 10 listings in Grub. The file and the recovery file. How can I safely remove these. 
Thank You.:confused:

---

### Post by kpkeerthi on 2008-06-12
1. Open System -> Admin -> Synaptic
2. Search for **linux-image**. This should list all the kernels installed on your system with a check box in green.  
3. Select the kernels (highlighed in green) you no longer need and Mark for Complete Removal.
4. Click Apply.
Synaptic automatically updates your GRUB with the changes.

---

### Post by reb68 on 2008-06-12
Thank You. I appreciate the quick response and help. I just noticed where on the left it counts Thank yous. I have alway said thank you in the original message but that misses the counter. Again I appreciate all the help I have got from the Forums.

---

### Post by meierfra. on 2008-06-12
> have alway said thank you in the original message but that misses the counter. 

For an official thank you:   Click on the blue ribbon with the gold star  on the bottom right corner of a post.

For more information on kernel updates: Click on "drs305" in my signature

---

### Post by drs305 on 2008-06-12
I recommend using StartUp-Manager to reduce the number of kernels viewed on the startup boot menu. StartUp-Manager has a lot of other options which you can safely modify. The link below discusses these options as well as how to manually edit menu.lst (if you must ;-) ).

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

