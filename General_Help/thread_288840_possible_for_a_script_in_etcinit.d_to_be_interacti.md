---
title: "possible for a script in /etc/init.d to be interactive?"
date: 2006-10-30
forum: General Help
---

### Post by zeus77 on 2006-10-30
There's a script that I would like to run during boot (near the end of the boot sequence), but the script is a little unusual in that it asks for a password.  To get it to load at boot, I've tried putting this script in /etc/init.d, but the boot sequence never pauses to ask for the password during boot -- it just skips over it, and in /var/log/boot it says "invalid password".  

Is it possible to have any user interaction in /etc/init.d scripts during bootup?

Is there some other place (other than /etc/init.d) where I could put an interactive script that I would like to run during bootup?

Thanks.

---

### Post by zeus77 on 2007-03-08
nobody knows the answer, eh?

---

### Post by po0f on 2007-03-08
zeus77,

You could have the script read the password from a USB thumb drive.  If the thumb drive is plugged in, the service starts; if not, no go.  Or just from any file on the computer, just make sure only root can read it (`sudo chmod 600 /root/password_file` or whatever).

---

