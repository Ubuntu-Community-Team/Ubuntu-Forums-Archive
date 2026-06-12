---
title: "Adding programs to boot menu?"
date: 2006-07-01
forum: General Help
---

### Post by CoNfUsIoN on 2006-07-01
I was wondering if anyone could tell me how to add programs to the "boot-menu" or whatever its  can start-up certain programs automatically during boot. I was wondering this becasue I have my gDesktop eye-candy, like cool looking menus and stuff, but I have to open them manually at the moment.

Or even better, is there a way to start up the individual 'desklets' (eye-candy menus) without opening the entire gDesktop program?:-s

---

### Post by reacocard on 2006-07-01
you mean starting programs when you log in? System -> Preferences -> Sessions -> Startup Programs

---

### Post by CoNfUsIoN on 2006-07-02
yup! that did the trick. Yet so simple... I can't wait to learn to use everyhting in linux\\:D/

---

### Post by acercanto on 2006-07-02
Ok, that works for people using Gnome, but what about Enlightenment? I tried the right-click on window and "remember to restart application on login" option, but that doesn't work. I've tried putting it in ~/.xsession and ~/.xinitrc to no avail. I'm also trying to get Firestater to run (which requires root priveliges) and that's not working either. Any ideas?

---

### Post by reacocard on 2006-07-02
for starting a daemon like firestarter, there's /etc/init.d/bootmisc.sh
just append the commands you want to run at the end, right before ":exit 0"

---

