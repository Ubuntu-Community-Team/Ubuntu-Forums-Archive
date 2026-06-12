---
title: "Issues with fluxbox"
date: 2007-12-06
forum: General Help
---

### Post by spitfire23bc on 2007-12-06
Hi all, I've been using Fluxbox for a little while, and decided to fiddle around with it today, Suddenly Fluxbox seems unable to properly recognise the windows it is painting...

Right click and middle click bring up their respective menus, but left click simply causes them to disappear again.
Left click does nothing over open windows
Right click over open windows brings up the menu
Scroll wheel over open windows changes desktop (should only do so over the desktop)

I *believe* that the only thing I changed between it working and it not was the menu font size... I could be mistaken, however.

Any ideas, please?

Dan

---

### Post by cknight on 2007-12-06
Sounds like you've got some rogue key bindings in your ~/.fluxbox/keys file.  Could you please post the contents of this file?  In the meantime, if you find any entries in your keys file with Mousetop1, Mousetop2 or Mousetop3 (or anything with Mousetop...) please comment those out (put a '#' in front of those lines, or delete those lines all-together), reconfigure fluxbox, and see if you've still got a problem.

---

### Post by quantumcheese on 2007-12-06
I agree with cknight: it sounds like a keys file problem regarding mouse bindings.

By default, left click OnDesktop will clear all menus; however, if you've run the fluxkeys configuration tool, you will need to fix the entry to say

OnDesktop Mouse1top :HideMenus

I have this problem every time I use fluxkeys, which is rare enough that I would forget and not be able to click on anything until figuring it out.

---

### Post by spitfire23bc on 2007-12-06
Ok, altering the keys file worked; thanks very much!

Dan

---

### Post by cknight on 2007-12-06
Aha, so its fluxkeys which has been corrupting the keys file with these Mousetop1, etc. commands.  I've always wondered where they came from.  They cause real issues for fluxbox beginners.  A shame that a tool meant to help those  folk actually hinders them.

---

