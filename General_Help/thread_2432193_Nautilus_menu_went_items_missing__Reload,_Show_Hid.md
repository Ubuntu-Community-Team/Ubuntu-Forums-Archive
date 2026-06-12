---
title: "Nautilus menu went items missing:  Reload, Show Hidden Files"
date: 2019-11-28
forum: General Help
---

### Post by goodstuff9 on 2019-11-28
Ubuntu 18.04.3, Nautilus 3.26.4.  

Suddenly, for no reason I know of, in the "hamburger" menu in Nautilus, the "reload" option is gone, and the "Show Hidden Files" option is always greyed out.  

If I start Nautilus as root I do not have this problem.  

I also have Caja installed, and the reload and view hidden files works fine in Caja as a regular user.  

I restarted Nautilus, and rebooted my computer, that did not help.  

I have reinstalled Nautilus, that did not help.  

What causes this problem?  

How do I fix this?

---

### Post by Impavidus on 2019-11-29
The problem must be in your home directory.

How do you start Nautilus as root? If done properly, Nautilus will read (and write) some config files in root's home directory. If done improperly, Nautilus will read (and write) some files in your home directory as root, which can cause trouble, but can at the same time mask a problem.

Make sure all files in your home directory (/home/yourusername/) are owned by you.

---

