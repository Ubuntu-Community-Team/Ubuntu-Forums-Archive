---
title: "nolapic help please!"
date: 2007-04-20
forum: General Help
---

### Post by FeelTherush1 on 2007-04-20
I am able to run the live cd with the command "nolapic" in the boot options. if i installed while this is in effect then will my system still boot so i can change around some drivers? i need to get my ATI X800 GTO (AGP) card to work. i have a pentium 4, 2.4 GHz, and 1 GB ram...everything except my vid car checks out i think. any help would be great!

---

### Post by Theimon on 2007-04-21
Yes you can, the nolapic boot parameter only counts for the session you're in at that moment.
When you finished your installation and you would like to have the nolapic option at every boot, you can add it in the default options of Grub. The nolapic option won't be added by default as far as I know.

---

