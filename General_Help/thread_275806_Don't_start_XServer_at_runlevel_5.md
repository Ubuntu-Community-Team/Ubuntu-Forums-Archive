---
title: "Don't start XServer at runlevel 5"
date: 2006-10-11
forum: General Help
---

### Post by ikus060 on 2006-10-11
How to don't load the Xserver at startun ?

---

### Post by kzutter on 2006-10-12
Prevent kdm (kubuntu) or gdm (gnome ubuntu) from starting.
On my Kubuntu Dapper machine, I would use the "System Services" applet in the "System Settings" menu to configure runlevel #5, not allowing kdm to startup on boot. I am sure Gnome has a similiar tool.

---

### Post by ikus060 on 2006-10-12
I didn't found any place to change it in the system menu to change the loading sequence. Can you give more detail ?

Also, I want to know it's will create a problem for VNC if I don't load gdm at startup ?

---

### Post by kzutter on 2006-10-12
System > Administration > Services

I use kubuntu, so I cannot tell you exactly how it works in gnome.

Install Bootup Manager for more control options


Yes, I believe vnc expects an xserver. Why do you want to not run xserver?

---

