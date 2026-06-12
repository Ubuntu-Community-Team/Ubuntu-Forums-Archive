---
title: "How to get Nautilus menu bar running on Xubuntu"
date: 2015-05-02
forum: General Help
---

### Post by Ralph L on 2015-05-02
I installed eiciel on xubuntu to support acls and extended attributes.  It also installed Nautilus and since Nautilus supports eiciel very well, I decided to try it. I launched nautilus from Terminal, but it came up without a menu bar.  I really need a menu bar.  I suppose it was pulled out as part of unity (unity does strange stuff), since under unity the menu bar is pulled away from the app window.  Anybody know how I can get the nautilus menu bar back so that I can run nautilus under xubuntu 14.04 LTS, and support acls????   
I have run nautilus under older xubuntu systems, and it seems to run fine--also had a menu bar.

---

### Post by ajgreeny on 2015-05-02
Is the menubar in your top panel if you put the cursor into it, as with nautilus?

---

### Post by mcduck on 2015-05-02
Which version of Xubuntu (and Nautilus)? The recent versions don't really have much of a separate menu bar, the menus are integrated in the icons found in the right-hand side of the same bar that has navigation and window controls & the breadcrumbs buttons.

---

### Post by Bucky Ball on 2015-05-02
Just a note: Nautilus and Thunar can occasionally make strange bedfellows on Xubuntu. I've had odd problems when both are installed on the same machine using Xubutnu in the past. Haven't used Nautilus for a few years so not sure if that is still the case or has anything to do with your problem. :-k

---

### Post by ajgreeny on 2015-05-02
> **Bucky Ball said:**
> Just a note: Nautilus and Thunar can occasionally make strange bedfellows on Xubuntu. I've had odd problems when both are installed on the same machine using Xubutnu in the past. Haven't used Nautilus for a few years so not sure if that is still the case or has anything to do with your problem. :-k
I think that is because nautilus tries to take over the desktop management from thunar unless you start it with command **nautilus --no-desktop** which forces it to not do so.  If it does manage the desktop you probably lose all configuration you have set-up in Xubuntu.

---

### Post by Ralph L on 2015-05-02
Thanks for all the responses.
1.  No, the menu bar doesn't appear in the top panel, when I move the cursor there.  However, I have relocated the top panel to the bottom, if that makes any difference.
2. Am running Xubuntu 14.04 and Nautilus 3.10.1 was loaded from the normal repositories.
3.  Nautilus doesn't seem to be having any effects on anything else on the desktop.  Whether I run nautilus with --n-desktop or not doesn't seem to make any difference.
4.  Most of the items that used to appear in the menu bar do now appear under the various icons on the upper right of the window.  So maybe mcduck is correct--that nautilus has been redesigned without a menu.  I thought that maybe there was a parameter to set to get the old menu back.  I am used to having a menu bar.

---

### Post by Bucky Ball on 2015-05-02
> **Ralph L said:**
> I thought that maybe there was a parameter to set to get the old menu back.  I am used to having a menu bar.

My original thought, actually. When you open a Nautilus window, there is nothing in 'Preferences' in whichever drop down that is located in? In PCmanFM it is under 'Edit' ...

---

