---
title: "Reinstalled Windows Partition, Won't Boot Ubuntu"
date: 2007-06-15
forum: General Help
---

### Post by rolfotto on 2007-06-15
My friend has a dual-boot Windows/Ubuntu.  His windows install got completely infested, so he just reinstalled Windows over that partition.  But Windows now starts up automatically (Ubuntu was the default choice before with grub giving you five seconds to choose) from the beginning.  We see with the live disk the Ubuntu partitions still exist, how do we fix this without reinsalling Ubuntu and swiping his data?

---

### Post by airblade on 2007-06-15
You can use the rescue option on the live cd.

Search in this forum; this question has been asked before.
Example: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by linzta on 2007-06-15
> **rolfotto said:**
> My friend has a dual-boot Windows/Ubuntu.  His windows install got completely infested, so he just reinstalled Windows over that partition.  But Windows now starts up automatically (Ubuntu was the default choice before with grub giving you five seconds to choose) from the beginning.  We see with the live disk the Ubuntu partitions still exist, how do we fix this without reinsalling Ubuntu and swiping his data?

Windows boot loader (NTLDR) for NT based systems may have over taken GRUB or LILO as your boot loader.  You could try adding entries to boot.ini and see if that works.  

oreilly has a good article on how to add entires to it and what not: 
[http://www.oreillynet.com/pub/h/2337](http://www.oreillynet.com/pub/h/2337)

Best of luck!

---

### Post by jasonlfunk on 2007-06-15
You can also try making a SuperGRUB CD (if you were using GRUB) and recovering with that. 
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

