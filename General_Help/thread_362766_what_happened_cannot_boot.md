---
title: "what happened? cannot boot"
date: 2007-02-16
forum: General Help
---

### Post by pleasehelpme on 2007-02-16
I already had Vista installed on 80GB partition, already created 30GB partition for Kubuntu (done this via Vista's parition software).  After install Kubuntu, rebooting laptop loads kubuntu automatically with no option to choose kubuntu or vista!  How do I fix this? I installed kubuntu dapper (downloaded dvd version today)

---

### Post by pleasehelpme on 2007-02-16
I attempted to load up from live cd...then used the partition software built in (qtparted) to format the linux root and swap partitions. Then I rebooted without the cd and of course, I get a grub error message (cannot load, etc) and no option to load vista!

---

### Post by pleasehelpme on 2007-02-16
I ran Vista setup cd and when into instal, deleted / formated the swap and linux partitions. I was unable to delete but only format the 30GB linux partition. I rebooted again and it STILL gave errors! Way to go ubuntu!

error:

grub loading stage1.5
grub loading..please wait
error 22

---

### Post by yabbadabbadont on 2007-02-16
I don't know about Vista, but with Win2000 you would need to boot the install cd and then take the option to boot the recovery console.  Once there you would use the fixmbr and fixboot commands to restore the windows mbr (master boot record).

---

### Post by pleasehelpme on 2007-02-16
Can someone please help me!

---

### Post by yabbadabbadont on 2007-02-16
Did you try using the recovery console (or the Vista equivalent)?

---

