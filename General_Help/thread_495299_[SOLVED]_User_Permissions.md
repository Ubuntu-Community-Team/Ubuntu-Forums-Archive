---
title: "[SOLVED] User Permissions"
date: 2007-07-07
forum: General Help
---

### Post by xDaveManx on 2007-07-07
I just set up and older 500mhz PIII with 320 Megs of RAM with Ubuntu for my mother to use.  I set it up with an external modem and got her on dial up (only option) with no problems.  So far it works great, and I set it up with three  accounts; one for me as administrator, one for my mother and one other for guests to use, neither of which have administrator rights. 

I'd like to disable the guest account from being able to access the other accounts' personal home folder directories.  While I've been  using Ubuntu myself for months, I'm still a complete moron when it comes to setting permissions, and I can't figure an easy way to do this.

I suppose that I could (and should) learn how to do this with the command line, but I was hoping there was a quick way to do it through the GUI.

I'm comfortable in the terminal, so that's not a problem, I was just hoping for a graphical solution.

---

### Post by Vajra Vrtti on 2007-07-07
[LIST]
[*]Login to the user account you want to protect.
[*]Locate in Nautilus the folder you want to protect.
[*]Right click it to open the *Properties* window.
[*]Select the *Permissions* tab.
[*]Change the **Others** access to **none.**
[*]Press the *Apply permissions to enclosed files* button.
[/LIST]

---

### Post by xDaveManx on 2007-07-08
Thanks!!!

---

