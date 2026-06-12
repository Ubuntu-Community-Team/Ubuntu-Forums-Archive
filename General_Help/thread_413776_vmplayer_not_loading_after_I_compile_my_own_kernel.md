---
title: "vmplayer not loading after I compile my own kernel"
date: 2007-04-19
forum: General Help
---

### Post by Bobtheknight on 2007-04-19
My betters,

I compiled my own kernel specialized to my p4 architecture, after I do that all went well except vmware player.  Here is the error message: 

Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

I need a way to load the kernel module 'vmmon.'  

If I boot from a old "generic" kernel, vmware player loaded fine.

Thanks in advance!

---

### Post by heimo on 2007-04-19
You need to compile vmware kernel module for your kernel. There's some vmware-config.pl (or similar) script you need to run.

---

### Post by Bobtheknight on 2007-04-19
Thanks a lot!  I do think I need to run vmware-config.pl.  However, when I searched my system for it, it's gone!  

it's not in /usr/bin

synaptic doesn't have it either.

What do I do now?

---

### Post by heimo on 2007-04-19
Perhaps try reinstalling vmware?

---

### Post by Bobtheknight on 2007-04-19
Error during reinstall:
E: vmware-player: subprocess post-installation script returned error exit status 1

I think it errored when it's trying to start vmware-player up.

BUT the vmware-config.pl exist.  This is what happens when run:

sh: /etc/init.d/vmware: not found
sh: /etc/init.d/vmware: not found
Unable to stop services for VMware Player

Execution aborted.

Edit:  I don't know if this message board tolerate double posting.  So I might as well be careful.  

Vmware player  came back online after I installed linux-i386 from the repository and used it.  This way I get my architecture instead of generic and i have the appropriate kernel headers.
This ends my little journey to custom kernel I guess :D

Perhaps if I do it again I'll do better.

Thanks for everyone that helped.

---

