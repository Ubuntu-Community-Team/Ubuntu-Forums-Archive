---
title: "Can't find &lt;computername&gt; internet connection"
date: 2006-11-06
forum: General Help
---

### Post by doobit on 2006-11-06
I've been getting an error in a dialog box that pops up right after the loggin screen in Xubuntu that says "can't make an internet connection to <mycomputername> XFce may not work correctly without this. You may be able to add <mycomputername> to /etc/hosts to fix this problem. Then there is a "try again" button and a "continue anyway" button. I tried adding it to /etc/hosts but it didn't make any difference. Xfce seems to be working fine if I hit the "continue anyway" button and I still have internet, so I really don't know what this error means. I've tried other things like disconnecting Samba, and adding DHCP to my firewall settings, but the error box continues to pop up. Ot's just an annoyance, but doesn't really seem to change the function of anything.
This is with Xubuntu 6.10.

---

### Post by doobit on 2006-11-06
Anybody else ever see this problem??

---

### Post by doobit on 2006-11-06
bump !

---

### Post by doobit on 2006-11-06
OK, nevermind... I fixed it.
I added the hostname of my computer in etc/hosts with the IP the same as localhost and the message went away.

---

