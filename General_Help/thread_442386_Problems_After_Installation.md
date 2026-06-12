---
title: "Problems After Installation"
date: 2007-05-13
forum: General Help
---

### Post by remba on 2007-05-13
hello everyone,

i have installed Ubuntu using wubi many times, with various wubi versions (including prior to 7.04) and have run into problems:
- my wireless network card (DWL-650) isn't recognized, though it was recognized with a "normal" (i.e: without wubi) installation. i was able to use the card's windows drivers to get it to be recoginzed but could not connect to the wireless network.
- my language is hebrew. while i have access to my windows files, all files/folders with hebrew names are not shown and cannot be "mounted", they are simply not there! this has nothing to do with ntfs support since i had it enabled and besides, other file/folders within the same windows partition are shown.

i would aprreciate any help you could give me. i don't think it is nececarily a wubi problem but i would like to know for sure.

thanks

okay, i found out that the kernel used in 7.04 is different than 6.06 where i had no problems. i think i will go back to 6.06 but that would of course mean i'd have to partition everything. i hope it works out one day...

---

### Post by ago on 2007-05-14
> **remba said:**
> - my wireless network card (DWL-650) isn't recognized, though it was recognized with a "normal" (i.e: without wubi) installation.
Are you positive about that? It looks strange to me since we do not really run any code that regards networking so that should behave in the same way as Ubuntu (alternate ISO). That might be due to the different kernel.

>  i was able to use the card's windows drivers to get it to be recoginzed but could not connect to the wireless network.p
Use the general forum for that.

> - my language is hebrew. while i have access to my windows files, all files/folders with hebrew names are not shown and cannot be "mounted", they are simply not there! this has nothing to do with ntfs support since i had it enabled and besides, other file/folders within the same windows partition are shown.
Check whether it is a generic ntfs-3g issue. On a normal installation mount the windows partition using ntfs-3g and see if it works fine. You may also want to use good old ntfs for a comparison.

---

### Post by remba on 2007-05-14
thanks for your reply. i now believe that all my problems are related to the new kernel used in 7.04. the versions i used that had no problems were earlier and not a clean install of 7.04.
that is why i will wait until these issues are solved in feisty before trying again as i do not believe there is a way to use wubi to install 6.06, and i do not wish to partition my machine again.
i guess that if i get my hands on another machine, i would install on the entire drive and use the network (hopefully wireless) to access my windows files.
until then, keep up the good work!

---

