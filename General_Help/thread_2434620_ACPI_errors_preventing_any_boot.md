---
title: "ACPI errors preventing any boot"
date: 2020-01-08
forum: General Help
---

### Post by noebarth on 2020-01-08
Hello, 

First, I am not an advanced user of Ubuntu, but I can use the commands and I understand the basics :) 
The following are my BIOS info and then the errors I get from > demsg -lerr     (Obtained by booting on USB key).
 [ATTACH=CONFIG]284764[/ATTACH][ATTACH=CONFIG]284765[/ATTACH]

The symptoms are: 
- I can't boot, even in recovery mode.
- I can't use the recovery mode options. 

I have no idea of how to fix this. The problem is affecting my work computer, in which I separated the boot and my personal files on two different partitions (sda1 and 2, respectively). 
I have a lot of packages and softwares manually installed, etc, and I am not sure how a re installation of ubuntu would affect me ... Can someone tell me that? 

Many thanks for your help, 
Noe

---

### Post by CatKiller on 2020-01-08
You appear to be saying that this machine once worked and now doesn't. Is that the case? What happened between those two states?

The error message is requesting a BIOS update. That would probably be a good first step.

---

### Post by noebarth on 2020-01-08
Yes, I just didn't turned it on while away for christmas. Everything was fine before... 
Could you help me with the BIOS update please? My problem is that I am unable to boot, but I have access to other computers and I have a bootable USB key with Ubuntu if that can help. 
Thanks! :)

---

### Post by CatKiller on 2020-01-08
> **noebarth said:**
> Could you help me with the BIOS update please?

Not really; I know nothing about your machine. Generally you'd go to your motherboard manufacturer's website, download the update file and save it onto a USB stick, then boot into the BIOS and point the updater at that file.

---

### Post by noebarth on 2020-01-08
Help for others: No need to update the BIOS. In my case, the impossibility to boot was rather due to the `nouveau` NVDIA drivers not functioning properly. 
Check what alternative NVDIA drivers you can use, purge the old ones and install new ones (With the software and packages update program for example). 

I am not sure why the recovery mode was bugged and finally worked but it saved me!

Thanks for your help CatKiller, it's very much appreciated!

---

