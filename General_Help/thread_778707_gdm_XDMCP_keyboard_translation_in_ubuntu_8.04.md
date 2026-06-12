---
title: "gdm XDMCP keyboard translation in ubuntu 8.04"
date: 2008-05-02
forum: General Help
---

### Post by bweinel on 2008-05-02
Hi all,

I am running Hardy Heron on my machine and ran into an issue with XDMCP keyboard translations. I first enabled XDMCP logins in the /etc/gdm/gdm.conf. On log on, the system displays the remote welcome logon screen and accepts a remote login uid/pw pair with no translation issue. However, once you have successfully logged on and are at the desktop, the keyboard translation goes bad. I checked it both in a terminal window and in openoffice writer. In both places it shows the same incorrect keyboard translation. I noted that xfs was not initially running and tried installing and starting it.. no difference. No error messages are noted in the /var/log/gdm logs. Am I missing another configuration somewhere?

Cheers
Bill

---

### Post by Êisdur on 2008-06-05
Just to mention that I am facing the same problem under Ubuntu 8.04.

---

