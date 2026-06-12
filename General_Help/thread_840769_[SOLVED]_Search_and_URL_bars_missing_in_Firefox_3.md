---
title: "[SOLVED] Search and URL bars missing in Firefox 3"
date: 2008-06-25
forum: General Help
---

### Post by rainserpent on 2008-06-25
After upgrading to Firefox 3, extensions will not update and the search/ URL bars are gone. I have tried: resetting to defaults, starting in safe mode, moving my profile out of the home folder, uninstalling and reinstalling (completely), switching themes or using default theme, etc.

I am thinking that there is some sort of hidden file somewhere that is not being removed and is interfering with FF3. Firefox 2, which I have had to reinstall, works fine.

I don't know what to do. I am thinking about maybe a clean install of Ubuntu after a full purge of Firefox. Anyone have any ideas?

---

### Post by nanotube on 2008-06-26
> **rainserpent said:**
> After upgrading to Firefox 3, extensions will not update and the search/ URL bars are gone. I have tried: resetting to defaults, starting in safe mode, moving my profile out of the home folder, uninstalling and reinstalling (completely), switching themes or using default theme, etc.

I am thinking that there is some sort of hidden file somewhere that is not being removed and is interfering with FF3. Firefox 2, which I have had to reinstall, works fine.

I don't know what to do. I am thinking about maybe a clean install of Ubuntu after a full purge of Firefox. Anyone have any ideas?

what version of ubuntu are you using, and what method did you use to "upgrade" to ff3?

---

### Post by rainserpent on 2008-06-26
I am using Hardy Heron. I used synaptic for the uninstall/ installs. I fixed this by the way, after working on it for weeks. Here was my solution:

1. Removed my profile from my home folder and placed it in a back-up folder.
2. Removed all versions of Firefox (completely) with synaptic.
3. Gksudo nautilus to open /usr /lib and delete all Firefox files.
4. Installed FF3 with synaptic.
5. Used HTML back-up of bookmarks in back-up folder.

My guess is that there was some rogue file in /usr /lib that took out the bars and kept giving me XUL parsing errors. I guess *remove completely* is a relative term. :confused:

I am so happy now that FF3 is working! :)

---

