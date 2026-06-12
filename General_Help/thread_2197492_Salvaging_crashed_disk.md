---
title: "Salvaging crashed disk"
date: 2014-01-04
forum: General Help
---

### Post by JWLER on 2014-01-04
I had a dual-boot 12.04/Vista system and my HDD crashed and won't boot anymore  http://ubuntuforums.org/showthread.php?t=2196504 . Using live CD I'm able to mount the partition and copy files. I plan on doing a new 12.04 install on a new HD. What is the best way of mining the old HD to be able to get a new install to closely resemble the old one? 
I will also be getting another HD to make disk image backups onto (clonezilla/dd/déjà-dup), in order to prevent this situation from happening again. Any recommendations on what to use?

---

### Post by jim_deadlock on 2014-01-04
The settings for all your apps are stored in (hidden) dot folders in your /home eg. ~/.config ~/.mozilla etc, so if you simply copy your /home to your new HDD then any software you install will have your old settings.

---

### Post by JWLER on 2014-01-04
Thanks I'll give it a try

---

