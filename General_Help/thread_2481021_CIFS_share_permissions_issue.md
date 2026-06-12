---
title: "CIFS share permissions issue"
date: 2022-11-16
forum: General Help
---

### Post by armegeden on 2022-11-16
Having issues setting Write access when mounting a CIFS mount.  Ubuntu Server/Client.  Details are in the paste:

[https://pastebin.com/1JSdiEmN](https://pastebin.com/1JSdiEmN)


What am I missing?  Did I mess up the smb.conf masks/modes?
I've tried both lines in the CLIENT /etc/fstab

(i created the test files from the console of the SERVER)


Thanks for any help!


Edit: Resolved from another forum by adding [COLOR=#232629][FONT=ui-monospace]file_mode=0775,dir_mode=0775[/FONT][/COLOR] to /etc/fstab argument.

---

