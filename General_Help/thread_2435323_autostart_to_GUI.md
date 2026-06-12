---
title: "autostart to GUI"
date: 2020-01-19
forum: General Help
---

### Post by mrspock123 on 2020-01-19
I have GUI installed on my VPS server and I need the server automatically to start my requiring GUI app on root before login. So far nothing works.

---

### Post by TheFu on 2020-01-20
Setup x2go-server on the VPS.  Use the Mate DE or openbox or fvwm or XFCE DE.  Do not use Gnome3 DE.

On your local workstation, setup the x2go-client.

Regardless, you need to have ssh working. Best if setup with ssh-keys.

 DO NOT LOGIN as root. NEVER login remotely as root.

After you get it working, you can tune the performance to be amazing by controlling the compression and telling x2go which amount of bandwidth to use.  For internet stuff, I normally tell it ISDN as the speed.

---

