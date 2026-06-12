---
title: "NoVNC"
date: 2023-01-13
forum: General Help
---

### Post by ohiodissident on 2023-01-13
Has anyone used noVNC on Ubuntu Server?  I'm trying to get it working on an Ubuntu instance that's on Google Cloud but havent been able to get it to work.  I fire up the VM, install a desktop (using apt-get install ubuntu-desktop), install and setup tightvnc, install noVNC (and it's prerequisites, websockify and such), opened the ports in the firewall, and still nothing... 
What am I missing?  Anyone have a good guide on how to do this on google cloud?

---

### Post by TheFu on 2023-01-14
Remote desktops don't like Gnome as the DE. I'd fully remove the ubuntu-desktop and install a ligher DE, say Mate or XFCE, then try again.   Gnome3 and Gnome4 DEs generally aren't supported for any remote desktops, unless you use gnome provided tools and recent versions of both the server and the client Ubuntu/Gnome workstations.

Or, if you want a better, more efficient, more secure, remote desktop, use x2go instead.  IMHO, VNC should have died like plain FTP and telnet due to poor security.  If you aren't using pki with keys for authentication, you are doing internet connections all wrong.

---

### Post by ohiodissident on 2023-01-14
I can try a lighter DE but I don't think that's the problem here.  When I try to open the page in a browser, it just says not found.  I'm running novnc and it says the URL is https://<MyIP>:6080/vnc.html

---

### Post by TheFu on 2023-01-14
[https://mrd0x.com/bypass-2fa-using-novnc/](https://mrd0x.com/bypass-2fa-using-novnc/) has a setup to get noVNC working and some caveats.

---

