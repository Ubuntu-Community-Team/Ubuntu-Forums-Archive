---
title: "Creating a Dual Boot System"
date: 2006-07-20
forum: General Help
---

### Post by prophecy on 2006-07-20
I'm trying to install Windows as a second OS, already having Ubuntu installed. However, I find that I am unable resize the partition in order to create a new one for Windows. I've tried using parted and gparted, but neither will allow me to resize. I'm assuming this is because I am using the partition to load Ubuntu, but I don't know what to do about it.

Also, I do not know how to manage the boot options for two operating systems. I would prefer Ubuntu to be the defalt system booted, with Windows only booting if I manually select it. Is there a program that will configure this for me? And even if there isn't, I am still worried that I'll have done all this only to have the boot files corrupted and the entire system unusuable, which I'd appreciate advice on preventing. :D 

Thanks,
prophecy

---

### Post by ajgreeny on 2006-07-20
Installing windows after ubuntu is not so easy as the other way round.  Windows insists on being at the start of the disk if I remember correctly.  Also it wil restore the windows MBR so you will then need to reinstall grub again.  There are lots of entries on the forum telling you how to do that so I'll let you do a search to find out how rather than just repeat it all again.

---

