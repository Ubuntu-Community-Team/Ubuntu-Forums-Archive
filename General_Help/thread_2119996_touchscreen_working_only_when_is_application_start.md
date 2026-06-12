---
title: "touchscreen working only when is application started form terminal"
date: 2013-02-25
forum: General Help
---

### Post by zajca on 2013-02-25
Hi guys, I have problem with xbmcbuntu when it's started from gdm or menu in lxde or any other ways touchscreen is not working. 

But when i run terminal and type xbmc, touchscreen is working.

Any suggestion how to fix this, I really need to autostart xbmc.

Thanks

/edit: To be precise. Cursor is jumping to right down corner of screen.

---

### Post by kclark on 2013-02-25
Not sure why that would cause any issues, one way you might try and work around this is to create a bash script that will start xbmc then add that to your startup applications.

---

### Post by zajca on 2013-02-25
> **kclark said:**
> Not sure why that would cause any issues, one way you might try and work around this is to create a bash script that will start xbmc then add that to your startup applications.

I tried that. 
So far i tried:
create bash script which runs xbmc in terminal and create for this autostart .desktop file (also tried move terminal command to .dekstop file). Always same result with no touch :(
All method ends same. Even desktop shortcut for xbmc with run in terminal option has same result. 

Really only way how to make it work is type it into terminal. So my guess is some Xauthority settings but dont know how to fix it.

---

### Post by kclark on 2013-02-25
Does it dump the core when running not from the terminal?

---

