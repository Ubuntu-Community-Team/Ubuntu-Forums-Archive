---
title: "Question about mounting hard drive disk so windows can run under vmware."
date: 2007-12-27
forum: General Help
---

### Post by josh.tessin on 2007-12-27
Right now I'm running Ubuntu 7.10 and I have mounted my windows xp slave drive, 
I'm wondering if there's a way to mount the HDD so it can run windows xp into vmware, or some other virtual program that runs on linux. This is so I can use my windows programs.

Thanks!

-Josh

---

### Post by HermanAB on 2007-12-27
VMware Converter?
[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

---

### Post by dcstar on 2007-12-28
> **josh.tessin said:**
> Right now I'm running Ubuntu 7.10 and I have mounted my windows xp slave drive, 
I'm wondering if there's a way to mount the HDD so it can run windows xp into vmware, or some other virtual program that runs on linux. This is so I can use my windows programs.

Thanks!

-Josh

In each vmware virtual machine you can add in physical hard drives connected to the host - either the whole drive or individual partitions, this is in the settings of each vm.

You have to be careful that the host O/S is not using the drive/partition, as there is the potential for corruption as multiple running O/S think that they have exclusive use of the resource (don't ask me how I know this, I'm too embarrassed to reply.....#-o ).

---

