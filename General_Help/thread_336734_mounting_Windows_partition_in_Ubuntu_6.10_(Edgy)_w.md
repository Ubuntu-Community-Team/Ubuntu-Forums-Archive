---
title: "mounting Windows partition in Ubuntu 6.10 (Edgy) with read/write access safe?"
date: 2007-01-12
forum: General Help
---

### Post by presbp on 2007-01-12
I have heard of being able to mount the Windows partition in Ubuntu with read and write access so you can move files between operating systems but I am wondering.. if this is safe and is proven to work.. because I cannot have problems with my Windows files or else it would be a huge problem.  Does this have the ability to mess anything with Windows up?  Also can I lock folders  (C:Windows for instance) so that I don't have write access or will I just be able to lock the folder with a password?  Also if I have a shared folder on the network that I can see from the other computer will I be able to see it in Ubuntu if I mount the Windows partition?  And one final question.. if I install Wine will Wine see the programs on windows that are installed and be able to run them?  Man if Linux worked with all windows games perfectly I would be abandoning Windows.   
Thanks for the help.

---

### Post by netadptr0719 on 2007-01-12
OK, A couple things to address here:
If your Windows is NTFS then you are not going to want to write to it and only read from it. If it is Fat32 then you can read write to it safely, I do it all the time. For mounting them you're going to want to search it most likely on the forums here or Google. Just search for "mount ntfs" or "mount vfat/fat32" and you should get some answers. I've seen mounting done so many ways it is ridiculous.

---

