---
title: "Select between hard drives"
date: 2021-01-30
forum: General Help
---

### Post by Maxiejoe on 2021-01-30
I have two internal hard drives, one with 16.04 running FireFox  and one with 20.04. running Brave  browser.  How can I switch from one to the other without changing the startup sequence  in BIOS each time I want to switch?   Thanks

---

### Post by tea for one on 2021-01-30
[s]Laptop or Desktop?[/s]

---

### Post by Impavidus on 2021-01-30
Doesn't grub allow you to choose?

---

### Post by Maxiejoe on 2021-01-30
No, I don't get grub at startup, it goes to the first selected in BIOS.

---

### Post by Impavidus on 2021-01-30
Run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Don't run any repair, just create a boot info summary and post the link here. That will show us all details about the configuration of your systems, boot files, grub menu etc.

BTW, do you realise Ubuntu 16.04 only has 3 months of support left?

---

### Post by Maxiejoe on 2021-01-30
(SOLVED)  I was only keeping 16.04 because it runs great and when I upgraded had a lot of problems. Put 20.04 on a new hard drive and it is doing good.  With only 3 months left I should just use 20.04 and transfer the files I want to keep to the new HD and use the old for backup.  Thanks for the help, I would like to grub to work if possible in the future..

---

### Post by CelticWarrior on 2021-01-30
Not nitpicking but if your OS boots then Grub *is *working. It may not be showing the Grub menu but Grub is definitely working.
If in the future you'll be working with only one OS - 20.04 - then the menu not showing is the normal and expected behavior. The suggestion in post #4 was to gather information about your system and try to understand why the Grub menu isn't showing and it should with dual-boot.

---

### Post by Maxiejoe on 2021-01-30
> **CelticWarrior said:**
> Not nitpicking but if your OS boots then Grub *is *working. It may not be showing the Grub menu but Grub is definitely working.
If in the future you'll be working with only one OS - 20.04 - then the menu not showing is the normal and expected behavior. The suggestion in post #4 was to gather information about your system and try to understand why the Grub menu isn't showing and it should with dual-boot.

Thanks Celtic, I have been using 16.04 without problems for years and forgot most everything about Ubuntu.  I think I will just use 20.04 as it is running fine and I don't need two systems.

---

