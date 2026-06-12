---
title: "Power off this disk - data integrity"
date: 2020-12-05
forum: General Help
---

### Post by greg2lapa on 2020-12-05
When I connect a thumb (flash) drive to my computer, it shows up in the Nautilus/Files app with a little eject button next to it. When I click the eject button, a notice appears saying it is safe to pull out the thumb drive. But even after this safe to pull out notice appears, some of my thumb drives still show a solid light indicating that the drive is receiving power. If I open the "Disks" app and select the entry for the thumb drive, there is a Power-Icon displayed that says this when I hover the mouse over it: "Power off this disk".

When I click "Power off this disk" the glowing light on the thumb drive disappears and the thumb drive no longer appears in the "Disks" list. 

Should I ALWAYS "power off this disk" before pulling out a thumb drive? Are there some instances where I should "power off this disk" before pulling the thumb drive but most of the time it's not necessary?

I want to avoid any chance of date corruption or loss before pulling out the thumb drive. [I use it for backups].

What is the point/function of "Power off this disk" if it is safe to pull out the drive after clicking the "eject" button?

---

### Post by GhX6GZMB on 2020-12-05
The "Eject" function ensures that any data remaining in buffers are finally written to your media, meaning you can safely remove it without data loss. The power off function is redundant and very unusual. It seems to be a special "Nautilus-user-confusion" function. I've not seen it in other file managers.

---

### Post by greg2lapa on 2020-12-07
> **ml9104 said:**
> The "Eject" function ensures that any data remaining in buffers are finally written to your media, meaning you can safely remove it without data loss. The power off function is redundant and very unusual. It seems to be a special "Nautilus-user-confusion" function. I've not seen it in other file managers.

Can any possible "harm" occur by not powering off before pulling the device out? Does it matter if it's a mechanical hard drive? 

Or is using Disks to power off the same effect as pulling the device and no harm can result no matter the situation?

---

### Post by CelticWarrior on 2020-12-07
> **greg2lapa said:**
> Can any possible "harm" occur by not powering off before pulling the device out? Does it matter if it's a mechanical hard drive? 


Yes, data corruption.

No, mechanical hard drive, solid state or flash is no different in this case. However, although theoretically it should matter much, it's conceivable that the mechanical parts of the HDD may suffer some negative impact alongside with data corruption that may shorten their lifespans.

---

