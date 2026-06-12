---
title: "Password?"
date: 2007-11-07
forum: General Help
---

### Post by ramsyanks on 2007-11-07
Hi
i just bought a use laptop with Ubuntu loaded as the OS. However it is asking me for a password to get in to the Applications. The person selling it cant remember. is there a workaround?

---

### Post by geirha on 2007-11-07
It's asking for your user's password most likely. Read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) if you want to know why

---

### Post by aysiu on 2007-11-07
Sure. You can reset the password.

Reboot. If it has a countdown and says *Press Esc to Enter Menu*, then press **Escape**. Otherwise, you should already see the boot menu, with the first menu item highlighted.

Press the **Down** arrow to get to the second menu item, which should have the phrase *Recovery Mode* in it.

After you boot into recovery mode, you will be at a command prompt that looks like DOS (but isn't). Type ```
cd /home
ls
``` This will tell you the username. Let's just say it's *ramsyanks*, for the sake of this example. Then type ```
passwd ramsyanks
``` to change the password for that user. Finally ```
shutdown -r now
``` to reboot the computer.

---

### Post by ramsyanks on 2007-11-07
Sorry for not being clear but the screen is the beige ubuntu screen and is asking for a username then a password. is there a way to get in without rebooting?

thanks

---

### Post by aysiu on 2007-11-07
> **ramsyanks said:**
> Sorry for not being clear but the screen is the beige ubuntu screen and is asking for a username then a password. is there a way to get in without rebooting?

thanks
Not unless you know the password.

The instructions I gave you earlier allow you to change the password to one you know from the current one (which you don't know).

---

