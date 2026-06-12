---
title: "Help with GRUB"
date: 2008-02-21
forum: General Help
---

### Post by Neo Napster on 2008-02-21
Hi all,

 I've an HP Pavilion 6040 notebook. It came loaded with Windows Vista. I installed Ubuntu 7.04 (Feisty Fawn) to dual boot with Vista. Everything was fine untill I resized the partition of Vista using GPart. From then Vista stopped working. I tried deleting all the partitions and installing with the Recovery CD which came along with the system. It doesnt work. I tried installing Windows XP Pro, it is not detecting my HDD. But when I try installing Ubuntu, it is detecting my HDD. Now I deleted every partion on my HDD. Still GRUB is loading and Windows is not detecting HDD. Please help me fix this.

Thanks in advance.

---

### Post by SpaceTeddy on 2008-02-21
i really don't know much about windows installations (haven't done them for years) but i know that the difference in windows and linux for detecting the HD's is, that windows trusts the BIOS, while linux scans by itself. 

I would *guess* that your copy of windows has no support for sata HD's, and that you need some driver to make the windows setup detect it. Or you have a "HD compatibility mode" that you can turn on in your BIOS. maybe that helps too... 

otherwise... i have no idea :(

---

### Post by Neo Napster on 2008-02-28
Thanks Space Teddy!!! I'll check that out.

---

