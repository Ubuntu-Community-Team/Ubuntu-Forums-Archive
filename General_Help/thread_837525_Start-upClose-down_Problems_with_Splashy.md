---
title: "Start-up/Close-down Problems with Splashy"
date: 2008-06-22
forum: General Help
---

### Post by Chris Riley on 2008-06-22
Hi! I run Hardy Heron 8.04 dual boot with WinXP (I'll be getting rid of that when my Lexmark printer gives up the ghost and I can justify buying a printer that is compatible with Linux).

I've recently installed Spalshy using Synaptic, and that uninstalled Ubuntu's Usplash. I now don't know how to put Usplash back on the system!

With Splashy, I'm having to boot 2 or 3 times before it works properly and brings up the GUI. First couple of boots are verbose, and I end up with a terminal log-in, and I am not familiar enough with Ubuntu to know how to get to the GUI from there. After 3 or 4 tries, I get the correct boot up sequence.

The kernel line in menu.lst is correct.

Also (and this is the main problem), I can't turn the computer off from the GUI. When I click on the icon for that process, the computer goes into restart. The only way - using software - to turn off is to then boot into Windoze and use that OS to close down.

The community's advice on curing all or any of these problems would be appreciated.

:confused: Chris

---

### Post by Chris Riley on 2008-06-23
> **Chris Riley said:**
> Hi! I run Hardy Heron 8.04 dual boot with WinXP (I'll be getting rid of that when my Lexmark printer gives up the ghost and I can justify buying a printer that is compatible with Linux).

I've recently installed Spalshy using Synaptic, and that uninstalled Ubuntu's Usplash. I now don't know how to put Usplash back on the system!

With Splashy, I'm having to boot 2 or 3 times before it works properly and brings up the GUI. First couple of boots are verbose, and I end up with a terminal log-in, and I am not familiar enough with Ubuntu to know how to get to the GUI from there. After 3 or 4 tries, I get the correct boot up sequence.

The kernel line in menu.lst is correct.

Also (and this is the main problem), I can't turn the computer off from the GUI. When I click on the icon for that process, the computer goes into restart. The only way - using software - to turn off is to then boot into Windoze and use that OS to close down.

The community's advice on curing all or any of these problems would be appreciated.

:confused: Chris
Solved. I reinstalled Usplash (again using Synaptic). This removed Splashy and reinstated Usplash, since when I have had no problems. Thanks for all the responses.

Chris.

---

### Post by emshains on 2008-06-23
> **Chris Riley said:**
> Solved. I reinstalled Usplash (again using Synaptic). This removed Splashy and reinstated Usplash, since when I have had no problems. Thanks for all the responses.

Chris.

You could have been able to run gnome and X from terminal, and then put them into your usual session, couldnt you ? Im not an expert, so dont count on me if you dont know its true.

---

