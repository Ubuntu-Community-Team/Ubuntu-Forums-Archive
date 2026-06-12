---
title: "i need help installing windows xp on kubuntu 7.04"
date: 2007-05-10
forum: General Help
---

### Post by funpop on 2007-05-10
i need to install windows xp on my computer, which got only one harddisk used by kubuntu.

at the moment it got these partitions:
<root>  <swap>  <home, 40 gigabyte free space available>

so i think i have to boot a linux live-cd, use *parted to resize my /home in order to create a disk area, which is not partitioned, where win xp should be installed.

i know the windows installation will destroy the grub, but i dont know if it will ask where to install,
and how to repair the grub again..i dont want to loose data, and dont want to do a backup, which would
be a 10 hour task!

any advice or a link to a guide will be helpful!

michael

---

### Post by mikewhatever on 2007-05-10
Here is how to restore GRUB [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
and here is how to install XP
[http://theeldergeek.com/xp_home_install_-_graphic.htm](http://theeldergeek.com/xp_home_install_-_graphic.htm)
The installer should detect the unallocated space and give you an option to create a new partition there.
Good Luck.

---

### Post by funpop on 2007-05-10
thank you for the links, they are both very well written !

---

