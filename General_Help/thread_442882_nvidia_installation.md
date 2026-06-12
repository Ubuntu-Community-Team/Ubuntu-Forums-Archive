---
title: "nvidia installation"
date: 2007-05-13
forum: General Help
---

### Post by prem1er on 2007-05-13
I'm getting the error message "You appear to be running an X server: please exit X before running this install'.  I am logged off and using ctrl+alt+f2 at the login screen.  Doesn't this mean that X windows is closed?

---

### Post by Wim Sturkenboom on 2007-05-14
The window might be closed, but the server is still running in the backgroiund.

---

### Post by prem1er on 2007-05-14
Ok well how to I end it completely

---

### Post by Wim Sturkenboom on 2007-05-14
No Ubuntu at hand, but I would check the pid with *ps* and kill it.

There are some guides for installation of nvidia drivers in the section *multimedia and video*. The one I used for dapper did not mention stopping the X-server (as far as I can remember).

---

### Post by hartz on 2007-05-14
sudo /etc/init.d/gdm stop

---

