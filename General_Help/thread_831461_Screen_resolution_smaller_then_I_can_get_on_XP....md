---
title: "Screen resolution smaller then I can get on XP..."
date: 2008-06-16
forum: General Help
---

### Post by SilverGoldBronze on 2008-06-16
I have Ubuntu and XP dual booting, and I noticed my resolution on Ubuntu will only go up to 1024 x 768, whereas the resolution on XP goes up to 1280 x 1024. Is there any way to fix this?

Additionally, how do I apply themes in Emerald Theme Manager, as I can only view the theme on a list.

---

### Post by cocopuffz on 2008-06-16
it's possible that the correct modelines haven't been added to your xorg.conf file.

Try gksudo displayconfig-gtk .. it should open up a gui for your xorg.conf file. Use autodetect for your monitor. If your model isn't in the list, you can use "plug & play with 1280x1024" from that list. 

Hope that works for you

---

