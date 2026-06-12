---
title: "acess to HDD attached to wifi/modem"
date: 2014-04-11
forum: General Help
---

### Post by Hodor on 2014-04-11
I'm trying to access a hard drive attached to my wifi modem from ubuntu 12.04.
My windows computers can access it (the modem runs samba) at \\192.168.0.1\User.
Any help much appreciated.

---

### Post by mcduck on 2014-04-11
What happens if you, in the file manager, select Files->Connect To Server and then type "smb://192.168.0.1/User" as the address?

edit: Actually 12.04 should still have a dropdown menu for connection type in that dialog. Just select "Windows Share" there and fill in the details. Once connected you can simply bookmark the location for easy access in the future.

---

### Post by Hodor on 2014-04-11
Brilliant! thanks

---

