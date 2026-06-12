---
title: "Vmware error"
date: 2005-10-16
forum: General Help
---

### Post by artinla on 2005-10-16
I get the following error trying to install XP in vmware..  Anyone have a suggestion?  I am using vmware 5.0.

"The guest operating system you are running is using the Physical Address Extension (PAE) processor option.  For more information about
Oct 16 09:16:34: vcpu-0| running PAE-enabled guest operating systems, please consult http://www.vmware.com/info?id=28"

Thanks

---

### Post by _26oo_ on 2005-10-16
As you can see in the URL given by VMware you have to edit the VM config file and set paevm to true (you have to add it if the directive does not exist in the config file). I had the same problem some months ago with an AMD64 CPU (in 32 bit mode).

---

### Post by artinla on 2005-10-16
Actually, the directive from vmware never mentions my version at all. 

It says to add the line if running gsx server 2.5, however I am not.  They ought to clarify that directive.

Nonetheless, adding the line did fix the problem so Thanks!

By the way, I am also running an opteron in 32 bit mode.

Art

---

