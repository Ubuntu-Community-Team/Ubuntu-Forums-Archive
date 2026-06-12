---
title: "Booting windows messed up grub menu"
date: 2008-06-10
forum: General Help
---

### Post by destructaball on 2008-06-10
Hi I'm not the most technalogically minded person in the world so please go easy on me. I think I have reset my GRUB menu I cant boot windows xp any more. Windows is in HD (0,1) (what I could glean from the tutorials) what should i type into the grub thing and how do I get there?

---

### Post by VMC on 2008-06-10
> **destructaball said:**
> Hi I'm not the most technalogically minded person in the world so please go easy on me. I think I have reset my GRUB menu I cant boot windows xp any more. Windows is in HD (0,1) (what I could glean from the tutorials) what should i type into the grub thing and how do I get there?

We need to see to things. Open up a Terminal and type the following and display the output back here:

Applications > Accessories > Terminal

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

