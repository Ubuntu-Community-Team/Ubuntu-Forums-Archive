---
title: "Remote Desktop in Ubuntu 12.10"
date: 2012-11-11
forum: General Help
---

### Post by alwayscarmen on 2012-11-11
How do you enable remote desktop in Ubuntu 12.10 so that I can remotely connect to my machine over the intranet?

I did install Gnome Classic and did a search for remote desktop but nothing comes up.

Thank you

---

### Post by Lars Noodén on 2012-11-11
One way is to use [VNC](https://help.ubuntu.com/community/VNC/Servers).  However, in order to make the connection safe, it has to be [tunneled over SSH](https://help.ubuntu.com/community/VNC).

---

### Post by alwayscarmen on 2012-11-11
Thanks for your response, but how do you enable it in 12.10 so that it can accept incoming connections?

I'm still using 10.04 LTS, and there was an option Remote Desktop Preferences.  Within here, you would just put a tick in "allow other users to view your desktop".

I'm trying to find where this setting is in 12.10

Thank you

---

### Post by abecrab on 2012-12-26
Run "vino" or "Desktop Sharing" and you get a dialog box to make those settings.

---

### Post by diskmaster23 on 2012-12-26
I have also been a big fan of NoMachine's NX. Give's you SSH Desktop sharing capability. Decent throughput too. [http://www.nomachine.com/](http://www.nomachine.com/)
Although, it might not be what you are looking for. Check it out anyways.

---

