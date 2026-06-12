---
title: "LVM problems after Gutsy Studio install"
date: 2007-12-07
forum: General Help
---

### Post by pab10 on 2007-12-07
I'm not sure if it was me or the install process, but on PC with two identical disks I selected use LVM on the alternate install and it only installed one HD as accessible.

when I checked using LVM2 tools I was getting unknown volume problems (for some reason the install had created two volume groups, and in the second volume group VolGroup00 there was a duplicate reference to a physical volume that did not exist...)

to cut a long story short, solution was found via [http://www.linux-noob.com/forums/index.php](http://www.linux-noob.com/forums/index.php) forum 
and involved running

sudo vgreduce --removemissing VolGroup00

That got rid of the extra dud reference and I could then remove volume group...

now puzzling over if there is actually two ways to share volumes over a partition/.mount point using LVM... anyway thats the main problem solved, just reading what seems like a good guide on LVM at

[http://www.howtoforge.com/linux_lvm_p3](http://www.howtoforge.com/linux_lvm_p3)

---

