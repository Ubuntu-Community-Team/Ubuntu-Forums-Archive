---
title: "Can't launch any apps"
date: 2007-12-09
forum: General Help
---

### Post by ignavia on 2007-12-09
I'm running Gutsy, with no hacks I can think of, on a Latitude C610. As of this evening, I can't launch any apps. I get the "Starting ..." button in the running apps panel, but then it disappears and the app never launches. Clearly, I've not tried to launch every app, but I have tried Firefox, gedit, terminal, calc, and a few others. They all do the same thing.

I've tried rebooting (obviously), but to no avail. 

Please pardon my newbity. I've been running Linux as my main OS, distro-hopping for a few years now, but haven't had to  do much troubleshooting.

Thanks.

---

### Post by santiagoward2000 on 2007-12-09
Can you at least open a console? If you can, try opening something from there, for example, type **firefox**. Let's see if you get any output.

---

### Post by ignavia on 2007-12-09
I forgot that part. Yeah, I can switch to a different console. I can run console apps from there, but firefox, for example, gives me "Cannot open display:" Specifying display 0 or 1 gave me the same error followed by the number.

---

### Post by santiagoward2000 on 2007-12-09
Ah, I meant **gnome-terminal**, not the real terminal. Try pressing Alt+F2 and typing **gnome-terminal**

---

### Post by ignavia on 2007-12-09
Ah. I don't think so. Is that the same as clicking the terminal icon in the apps menu?

If I alt-F2, the run box comes up, but if I type firefox, I get nothing. 

Anything I try is going to take a few minutes, because I'm on the same machine booted into XP. 

Oh, and I can open desktop folders just fine, but I guess that's because Nautilus is already running.

---

### Post by ignavia on 2007-12-09
I'm realizing that seemed like I didn't know what you wanted me to do. I do know, I just don't want to reboot and reboot again when I've done something very similar: I'm pretty sure if I typed gnome-terminal in a run box, nothing would happen.

---

### Post by santiagoward2000 on 2007-12-09
Well, the only thing I can think right now would be logging out and then log in to a **Failsafe terminal**, you can select that under **Sessions**, in the login screen. There you could try opening firefox and see what happens.

---

### Post by ignavia on 2007-12-10
Logging in to a failsafe terminal worked, as did failsafe GNOME. I figured out the problem. Somehow, my hostname got reset to nothing. Set a hostname, reboot, and I'm back in business.

Thanks for your help.

---

### Post by santiagoward2000 on 2007-12-10
> **ignavia said:**
> Logging in to a failsafe terminal worked, as did failsafe GNOME. I figured out the problem. Somehow, my hostname got reset to nothing. Set a hostname, reboot, and I'm back in business.

Thanks for your help.

Well, you're welcome. It's good to hear you could figure it out! :KS

---

