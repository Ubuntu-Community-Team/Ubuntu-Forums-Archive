---
title: "compiling kernel module"
date: 2007-05-30
forum: General Help
---

### Post by bch820 on 2007-05-30
Hello,
I am trying to add a module to a kernel and am not sure what the process is. I have the source tar.gz file of a kernel module for a sata_sil3124. I want to replace the open-source module with this one I got from the manufacturer. I am able to compile the source which leaves me with a .ko file, but Im not sure what to do next. 

When I do an insmod, it says it can not find this module which I just compiled.

Thanks for any help.

-Brian

---

### Post by blazercist on 2007-05-30
I'm lazy, I would find the old module, and write down the name and the file path, then I would take the new one and rename it to the same name as the old one and copy it over the old one... it doesn't always work though.... AND BEFORE YOU DO ANYTHING MAKE A BACKUP OF THE OLD MODULE.... when you do "insmod blahblah.ko" make sure you are inside the same directory as the module, if it still complains try it like this "insmod ./blahblah.ko"

---

### Post by az on 2007-05-30
> **bch820 said:**
> Hello,
I am trying to add a module to a kernel and am not sure what the process is. I have the source tar.gz file of a kernel module for a sata_sil3124. I want to replace the open-source module with this one I got from the manufacturer. I am able to compile the source which leaves me with a .ko file, but Im not sure what to do next. 

When I do an insmod, it says it can not find this module which I just compiled.

Thanks for any help.

-Brian

Did you compile the module for the same version (version, arch, revision, ABI, etc...)of the kernel you are running?  The easiest way to do this is to use the linux-headers package.  Just install linux-headers-generic and when you compile your extra module, it should use that by default (instead of a source tree you built yourself).

Also, you have to unload the current driver for the new one to load.  You probably need to blacklist it and then reboot to do that.

---

