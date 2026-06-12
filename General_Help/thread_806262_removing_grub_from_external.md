---
title: "removing grub from external?"
date: 2008-05-24
forum: General Help
---

### Post by jellylogix on 2008-05-24
How can i remove grub from my external, and also remove any reference to it. When i boot up my computer with my external drive plugged into my computer, it reads the external and sees that "grub is installed" or something but can't load due to "error 17". So what I'm asking is does anybody know how I can remove grub from this drive, and anything that this computer may be finding related to grub (which i thought i removed).

Thanks ahead of time :P

---

### Post by meierfra. on 2008-05-24
Can you change the boot order in your bios? If yes, make sure that internal drive comes before the external drive.

If this did not work and you still have ubuntu on your computer, open a terminal in ubuntu (applications->accessories->terminal)

and post the output of

```
sudo fdisk -l
```
(l is a lowercase L)

---

### Post by jellylogix on 2008-05-24
haha man I'm surprised I didn't think of that! I must be sleepy or something. Thanks for the BIOS tip!

Ryan

---

