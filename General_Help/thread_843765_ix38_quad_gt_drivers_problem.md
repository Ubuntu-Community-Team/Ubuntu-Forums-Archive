---
title: "ix38 quad gt drivers problem"
date: 2008-06-28
forum: General Help
---

### Post by rafe123 on 2008-06-28
I just a built a rig with the following parts:

mobo:  Abit ix38 quad gt\
proc:  E8400
mem:   Corsair Dominator pc8500 2x2gb
video: Nvidia Palit 1gb 8800GT
HDD:   (a) new 500gb SATA seagate .11
       (b) old 100gb IDE Maxtor
       (c) old 20gb IDE WD

I installed Ubuntu (my first time using Linux) on the SATA, mounted the IDEs and moved some files from them to the SATA ext3 partition, then unplugged the SATA and wiped and installed Vista on a 25g partition on the 100gb Maxtor IDE drive. 

I installed the Abit ix38 drivers and the Palit 8800gt drivers, and then when I went back into Ubuntu to edit GRUB so it would show Vista as a boot option, Ubuntu no longer recognizes the internet connection (plugged directly into the mobo, which it recognized just fine previously) and no longer sees the ide hard drives. sudo fdisk -l | grep NTFS | awk '{print $1}' gets me absolutely nothing. 

After installing the ix38 drivers, I now see a screen on boot-up from "JMicron", where it seems to be trying to find my IDE drives. It's an annoying screen that slows boot-up (and also now it can't find my 20gb drive, perhaps because it's blank, I'm not sure why). 

My real question is how do I install the drivers from the ix38 cd? Nothing happens when I put the cd in. And will those drivers even help?

---

### Post by rafe123 on 2008-06-28
A little web research revealed that there were problems with the JMicron controllers in the past. Good news is the internet works fine now.

Any idea how I can get the jmb363 supported in Ubuntu?

---

### Post by rafe123 on 2008-06-30
Still looking for assistance on this issue. Again, the problem is getting Ubuntu to recognize my IDE drives. They were recognized in Ubuntu previous ot installing Vista on the IDE. Now they won't show up in Ubuntu.

---

