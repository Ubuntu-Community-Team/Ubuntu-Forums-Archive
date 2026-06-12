---
title: "require password to reboot?"
date: 2008-05-07
forum: General Help
---

### Post by MemoryDump on 2008-05-07
is it possible to require a password prompt before you can reboot the machine from a gdm? Similar to when you want to launch an application which required authentication(sudo).

My kids are sometimes on my machine and I want to prevent them from being able to reboot the machine since I normally connect to my machine remotely.

thanks
-MD

---

### Post by Vadi on 2008-05-07
Not sure if you can make the applet require it, but you can remove the applet and instead make a script on the desktop that requires sudo to reboot.

---

### Post by bingoUV on 2008-05-07
> **MemoryDump said:**
> is it possible to require a password prompt before you can reboot the machine from a gdm? Similar to when you want to launch an application which required authentication(sudo).

My kids are sometimes on my machine and I want to prevent them from being able to reboot the machine since I normally connect to my machine remotely.

thanks
-MD

You could disable reboot/shutdown completely from gdm by unchecking "Show Actions Menu" in gdmsetup.

---

### Post by NilsE on 2008-05-07
Assuming you are on Hardy go into Authorizations under System > Administration  and change the authorization for who can shut down or reboot the system  under power-management. You may need to experiment to find the right combo but it should work.

The other alternative is to figure out the executable for the shutdown dialog and add it to the panel with gksudo.

---

### Post by MemoryDump on 2008-05-07
> **NilsE said:**
> Assuming you are on Hardy go into Authorizations under System > Administration  and change the authorization for who can shut down or reboot the system  under power-management. You may need to experiment to find the right combo but it should work.

I'm trying to do this, however I can't apply any changes as it's "greyed-out". Shouldn't I get a sudo/admin prompt when launching this app? cause I ain't.

---

### Post by Vadi on 2008-05-07
See if there's an "Unlock" button somewhere... it's a new feature that came with PolicyKit *sigh*.

---

### Post by NilsE on 2008-05-07
> **MemoryDump said:**
> I'm trying to do this, however I can't apply any changes as it's "greyed-out". Shouldn't I get a sudo/admin prompt when launching this app? cause I ain't.
After you change one of the 3 lines it should make the modify button available.  When you click on modify it will then prompt you for a password.

---

### Post by MemoryDump on 2008-05-07
> **Vadi said:**
> See if there's an "Unlock" button somewhere... it's a new feature that came with PolicyKit *sigh*.

none that I can see :(

> **NilsE said:**
> After you change one of the 3 lines it should make the modify button available.  When you click on modify it will then prompt you for a password.
nope. nothing happens even after I change a setting and try and click on that change button. It remains greyed-out.

---

### Post by Vadi on 2008-05-07
I was playing around with recordmydesktop and made a small vid for you.

[http://www.mediafire.com/?3l1jsltbzbx](http://www.mediafire.com/?3l1jsltbzbx)

I think the Authorizations tool is exactly what you're looking for. It's great that they included this, it'll definitely help out libraries/schools adopt Ubuntu easier!

---

### Post by MemoryDump on 2008-05-08
I think I just realized why I can't apply any changes. I'm connected remotely using NX (nomachine) and I think they automatically limit certain actions from being performed remotely. DOH!

thxs Vadi for the video! I'm still trying to make it play on my work computer running XP :(

---

### Post by Vadi on 2008-05-08
Haha. Get VLC, it'll run it.

---

