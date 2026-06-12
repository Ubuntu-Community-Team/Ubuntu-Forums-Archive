---
title: "Any Way to Force a Program to Open Maximized?"
date: 2020-05-02
forum: General Help
---

### Post by rebeltaz on 2020-05-02
Is there any way that I can force a program to open maximized? I built a jukebox running SilverJuke and since that is it's only function, I have it set to start automatically. No matter what state the program is in when it's shut down, though, it insists on opening in a smaller-than-full screen. I tried contacting the author, but didn't get any response. It's open source so I guess theoretically I could modify the code and force it that way, but I would really rather an off the shelf solution if there is such....

---

### Post by erind on 2020-05-03
You can get some results using Desktop Environment's interaction tools such as xdotool, xte, wmctrl. It's not the best solution but given your situation they're better than nothing. There's plenty of examples online on how to use them.

---

### Post by CatKiller on 2020-05-03
I've never used the thing, but a look through the man page suggests that the fullscreen, single-application, mode of operation is called kiosk mode, which can be specified in advance with the **--kiosk** switch.

Most window managers will also allow you to specify rules for how windows are handled when they're created, and there are the lower-level tools that erind has mentioned.

---

### Post by rebeltaz on 2020-05-03
> **erind said:**
> You can get some results using Desktop Environment's interaction tools such as xdotool, xte, wmctrl. It's not the best solution but given your situation they're better than nothing. There's plenty of examples online on how to use them.

> **CatKiller said:**
> I've never used the thing, but a look through the man page suggests that the fullscreen, single-application, mode of operation is called kiosk mode, which can be specified in advance with the **--kiosk** switch.

Most window managers will also allow you to specify rules for how windows are handled when they're created, and there are the lower-level tools that erind has mentioned.

Thank you both. I don't know why I didn't think to look at the man page. Blonde moment, I guess... Thanks again.

---

