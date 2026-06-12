---
title: "windows install for games"
date: 2006-10-27
forum: General Help
---

### Post by feest on 2006-10-27
hi, i want to install windows next to linux and i succesfully created a ntfs partition but i have a couple of questions...

- when i install windows, will linux still boot first?
- will it damage my linux install?
- other things that are dangerous to my linux install?

please help

Sven van de Scheur

---

### Post by roberine on 2006-10-27
> **feest said:**
> hi, i want to install windows next to linux and i succesfully created a ntfs partition but i have a couple of questions...

- when i install windows, will linux still boot first?
        - Only windows will boot. 
- will it damage my linux install?
        - No
- other things that are dangerous to my linux install?
        - After installing windows you should boot from your
          ubuntu live cd and then re-install GRUB
          After this you should have a dual-boot system

please help

Sven van de Scheur

- Herbert

---

### Post by Dr. Nick on 2006-10-27
- Windows will boot first and you will have to repair grub to boot linux at all

Look [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28restore%29%7C%28grub%29")

- it will only truly damage linux if you play with the partitining options in the windows install and erase the partitions

---

