---
title: "kUbuntu kernel upgrade, now 2 kernels"
date: 2007-02-11
forum: General Help
---

### Post by ForceAbuser on 2007-02-11
hi all :)

just a couple of days i got a update reminder that there is a new kernel (2.6.7.11) available 
for me. so i runned adept and updated to the new kernel,

so far so good :)

but now if i boot my laptop i get a 2.6.17.10 AND a 2.6.17.11 kenel in my list :(

i tried both kernels, both work, only on the new kernel my wireless & autostart for dvd's doesnt work anymore :(

this MIGHT have something to do with me fooling around with some extra repos, (wich got me a sweet new 1.2.6 version of nicotine), but those repos where disabled when i updated.

so my guess is to uninstall the old kernel, and reinstall my wireless again. but i have no idea how to uninstall properly.
i tried uninstalling trough adept, but i got a warning in the details box that i wouldnt be able to boot my system anymore :(

any help/thoughts?

---

### Post by nyinge on 2007-02-11
I suppose that you mean you're seeing the 2 kernels in the GRUB menu list.  The old one is still there just in case the new one gives problems; so that you can always boot the old kernel that way.

I think you might need to reinstall your wireless depending on how you've configured it.  I have to reconfigure my wireless every time there's a kernel upgrade.  I'm using ndiswrapper.

It's usually a good idea to keep around at least one previous version of kernel, IMHO.  :)

---

