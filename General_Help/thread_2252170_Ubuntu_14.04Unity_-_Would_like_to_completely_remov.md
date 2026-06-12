---
title: "Ubuntu 14.04/Unity - Would like to completely remove &quot;Places&quot; from Nautilus"
date: 2014-11-09
forum: General Help
---

### Post by ClientAlive on 2014-11-09
Googling around I see there is a way to modify the Places section in Nautilus file manager but I don't see anything on removing it altogether. Is there some way to completely remove Places from showing up in Nautilus?

Thanks in advance for any help.

Sincerely,
Jake

---

### Post by cariboo on 2014-11-11
I found this answer on Ask Ubuntu:

> [LIST]
[*]edit the file at  ~/.config/user-dirs.dirs
[*]save a backup copy in the same folder under a recognizably altered name
[*]edit our target file
[*]delete the unwanted lines
[*]save the modified file
[*]edit /etc/xdg/user-dirs.defaults
[*]cd /etc/xdg/
[*]sudo cp user-dirs.defaults user-dirs.defaults.orig # backup copy
[*]sudo gedit user-dirs.default
[*]delete the offending lines
[*]save the modified file
[*]reboot
[/LIST]


You can check out the original post [here]("http://askubuntu.com/questions/264280/how-to-remove-items-from-places-sidebar-in-nautilus-3-6").

---

### Post by mc4man on 2014-11-11
Re; that ask ubuntu post - 
sudo gedit is no longer advised, use sudo -H gedit
The command that was posted also used user-dirs.default, it's user-dirs.defaults
(fixed on AU

---

