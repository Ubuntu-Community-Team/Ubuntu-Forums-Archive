---
title: "Acer laptop toasted"
date: 2019-10-17
forum: General Help
---

### Post by user156 on 2019-10-17
Hell. I have an acer aspire laptop. I have been running budgie desktop. I decided to use the katoolin script and now my computer has no gui. Any thoughts on how to reverse the effect on it?

---

### Post by Holger_Gehrke on 2019-10-17
Hell, indeed ...

Have you checked the issue tracker for katoolin at github ([https://github.com/LionSec/katoolin/issues](https://github.com/LionSec/katoolin/issues)) ? From that it seems that the maintainer hasn't been seen for a while (at least two posts mention forks of the project) and there's a post that describe a very similar problem to yours that didn't get even one answer in 6 months ... 

My guess would be that it's probably possible to undo the damage by uninstalling the packages the script installed (look in /var/log/dpkg.log to find out which these are; "grep '[^-]installed' /var/log/dpkg.log" shows installations, "grep 'remove' /var/log/dpkg.log" shows removals), removing the repositories it has added and reinstalling the metapackage for the desktop and possible some others of the removed packages, but since I'm not going to try the script and I'm not on budgie anyway I can't tell for sure.

Holger

---

### Post by mastablasta on 2019-10-18
you can boot to text mode by modifying boot parameters in grub.

more here: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
and here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

when in text mode you can try to resolve your issues using CLI based tools.

---

