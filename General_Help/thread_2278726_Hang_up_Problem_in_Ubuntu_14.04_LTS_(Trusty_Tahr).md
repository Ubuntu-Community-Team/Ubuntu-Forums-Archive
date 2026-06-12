---
title: "Hang up Problem in Ubuntu 14.04 LTS (Trusty Tahr)"
date: 2015-05-18
forum: General Help
---

### Post by ventarraja on 2015-05-18
Hello, Im new with this forum, pls guys can you help me with this problem, when there is a call, Im using a jabra and plantronics USB headset sometimes they hang up and need to reboot the system. When im using analog headset any calls i did are ok. Im using desktop computer, are there any missing of my installation?, pls help Thank You so much

---

### Post by coffeecat on 2015-05-18
Not a Forum Feedback & Help thread.

*Thread moved to **General Help**.*

---

### Post by ventarraja on 2015-05-19
[COLOR=#000000]Hello, Im new with this forum, pls guys can you help me with this problem, when there is a call, Im using a jabra and plantronics USB headset sometimes they hang up and need to reboot the system. When im using analog headset any calls i did are ok. Im using desktop computer, are there any missing of my installation?, pls help Thank You so much[/COLOR]

---

### Post by dino99 on 2015-05-19
your best friends are logs, to find usefull warnings/errors to dig around the issue
mainly xorg.0.log into your /home; and into /var/log/dmesg . You can use the file manager (aka nautilus on the ubuntu installation) to find them

and please post the output of:
> sudo blkid

and tell us which graphic card/chipset is used, and which driver is installed

---

### Post by coffeecat on 2015-05-19
Threads merged. Please do not post duplicate threads - this dilutes the community's ability to help. You can always bump a thread if you do not receive a reply within a few hours.

---

### Post by ventarraja on 2015-05-19
> **dino99 said:**
> your best friends are logs, to find usefull warnings/errors to dig around the issue
mainly xorg.0.log into your /home; and into /var/log/dmesg . You can use the file manager (aka nautilus on the ubuntu installation) to find them

and please post the output of:


and tell us which graphic card/chipset is used, and which driver is installed

here is the output sir of [I]sudo blkid
[/I]/dev/sda1: LABEL="System Reserved" UUID="486A48E26A48CE7E" TYPE="ntfs" 
/dev/sda2: UUID="9666C6A766C68787" TYPE="ntfs" 
/dev/sda5: UUID="69afea7e-7f5f-4093-ab74-62d072468079" TYPE="ext4" 
/dev/sda6: UUID="6a2d2c7e-3af2-4fca-8351-b056d8025c0c" TYPE="swap"

---

