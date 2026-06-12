---
title: "Password only for sudo"
date: 2015-03-28
forum: General Help
---

### Post by PantherStu on 2015-03-28
Hi all, 

I was wondering if there is any easy way, to make it so Ubuntu stops asking for passwords for everything, including after "Locking" except Sudo.

Thanks

Stu

---

### Post by papibe on 2015-03-28
Hi PantherStu.
> **PantherStu said:**
> ... to make it so Ubuntu stops asking for passwords for everything ...
Could you make an example?

Your password is asked when running sudo on the command line, and in the GUI when an admin task is necessary. Are you being asked on more occasions than that?

Regards.

---

### Post by PantherStu on 2015-03-28
Yes I also get asked when the computer locks itself because of time,  so after hibernation and suspend, I don't get asked on startup because of auto-login.

---

### Post by papibe on 2015-03-28
Got it.

Open 'System Settings', there open 'Brightness and Lock', and then turn off the **Lock** option.

Hope it heps. Let us know if that works as you expected.
Regards.

---

### Post by PantherStu on 2015-03-28
I don't have a System settings (Using Ubuntu Gnome)and in settings, the closest thing I get is Power settings, which doesn't have a lock option.

---

### Post by papibe on 2015-03-28
Sorry I missed that.

Try this:
> If you go into the "Activates" then type "settings" click on the icon that has a spanner and a screwdriver and says "Settings". When it has opened, click on the the icon that looks like a lock dial and says "Privacy". Now click on the item that says "Screen Lock" then click on the toggle switch next the text that says "Automatic Screen Lock". Press the button that says Close, and now the item that says "Screen Lock" should have "Off" next to it.
(reference here: [How do I disable the GNOME Lock Screen?]("https://ask.fedoraproject.org/en/question/36256/how-do-i-disable-the-gnome-lock-screen/"))

Let us know if that finally avoid the locking of the screen.
Regards.

---

### Post by PantherStu on 2015-03-30
Nope, still locking,  not sure what to do now.

---

### Post by stoneage on 2015-03-30
I have Ubuntu Gnome 14.04. 

Click on Activities and search for Brightness and Lock, or click on the power button top right and select the 'tools' button, then Brightness and lock.

[ATTACH=CONFIG]260973[/ATTACH]   [ATTACH=CONFIG]260972[/ATTACH]   [ATTACH=CONFIG]260971[/ATTACH]

You can then turn off the lock screen option and/or disable the requirement to provide a password on awake from suspend.

[ATTACH=CONFIG]260970[/ATTACH]

---

