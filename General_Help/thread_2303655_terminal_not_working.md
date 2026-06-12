---
title: "terminal not working"
date: 2015-11-20
forum: General Help
---

### Post by Claude Renaud on 2015-11-20
I just installed ubuntu 15.10 and everything seems to be working, except that the terminal function does not work.
When I click on the terminal icon on the sidebar, it flashes for a few seconds, but no terminal opens.
I also tried from the dashboard, same result...

---

### Post by Hodevah on 2015-11-22
Did you uninstall something and then perhaps your terminal was uninstalled as well and is now showing in the menu, yet not loading up?
can you look inside [B]~/.xsession-errors

[/B]can you perhaps start it from xterm?
is there anything that you recently did/amended etc.. to your **.barshrc** file?
have you looked inside **/var/log/messages** to see if there is anything related to your terminal not starting?
can you reinstall it from your software center?

---

### Post by Andrew_Constantine on 2015-11-22
Try also, ctrl+alt+f1, login with your username and password you use to login under the GUI, 'sudo apt-get install gnome-terminal' let it work then type 'sudo init 6' to restart your machine and see if that solves the issue, if gnome-terminal was removed it will be reinstalled.

You can also test if the icon was messed up somehow by using the keyboard shortcut, ctrl+alt+t or navigate to it from the menu.

---

