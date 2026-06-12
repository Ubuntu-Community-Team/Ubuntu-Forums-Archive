---
title: "multiboot problem"
date: 2005-04-22
forum: General Help
---

### Post by cunla on 2005-04-22
Hi,
I have installed ubuntu and I am having problems with grub..

I have Windows XP on the list, however, it doesnt seem to load,
I was very careful not to delete anything...

I believe the problem is that my ntldr file is on (hd0,0), however, my windows directory is at a different drive, how can I tell GRUB to "mount"/start both on boot?

Thanks,

---

### Post by lorap on 2005-04-22
hi!
i've installed ubuntu.even previous version warty, many times having at once microsoft and it. you probably made something wrong when installation process cause grab'd to recognize everything on its own.
something else, i did encountered a problem, it's ubuntu's bug when i tried to install
this way:
hda0->25MB(boot)
hda1->20GB(root)
hda2->256MB(swap)
hda3->256MB(swap)
hda4->ntfs(or fat32)

this way i've many times installed redhat,mandrake and suse having no problems,but i did with ubuntu and debian.
i'll send them this information so they'd fix it.
hope you haven't done all this cause the other configurations work fine.
i think it'd be better for you say install microsoft on c: and linux on d: once you work either with ubuntu or debian.
pesah sameah haver :-)
pavel

---

### Post by cunla on 2005-04-22
[QUOTE=lorap]
pesah sameah haver :-)
pavel[/QUOTE]

To you to my man!

---

