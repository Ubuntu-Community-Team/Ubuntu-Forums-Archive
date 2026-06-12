---
title: "Change console font size Ubuntu 14.04 minimal cli install?"
date: 2015-12-25
forum: General Help
---

### Post by globetrotterdk on 2015-12-25
I have a laptop with an Ubuntu 14.04 minimal cli install and would like to change the console font size (without changing the resolution). How do I do this?

---

### Post by yetimon_64 on 2015-12-25
With the command "sudo dpkg-reconfigure console-setup". [[COLOR=#0000ff]--Here is a link--[/COLOR]]("http://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console") for a 12.04 guide on askubuntu. It should be an identical procedure on 14.04. To set the changes without rebooting the command "setupcon" will make the change on the spot (note number 5 in the linked instructions). Good luck.

Edit: I just noted the instructions are to set that install back to standard, you will need to try different sizes to see which suit your needs.

---

