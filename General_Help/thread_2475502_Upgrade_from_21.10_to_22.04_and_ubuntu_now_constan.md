---
title: "Upgrade from 21.10 to 22.04 and ubuntu now constantly freezes on apps"
date: 2022-05-29
forum: General Help
---

### Post by dodgyville on 2022-05-29
Hi,

I just upgraded from 21.10 to 22.04 and now I have several symptoms I think are related to one problem. This is on a radeon 5700xt and 21.10 was very stable.

* firefox snap freezes system (including mouse) but blocking it and installing apt firefox works.  Can still ssh in remotely.
* spotify snap freezes system (including mouse).
* I use gdm3 in autologin mode but when I disable that, gdm3 will not load (computer sits at blinking cursor on reboot). (Autologin gets me to the desktop)
* Setting EnableWayland to false in gdm3 does not solve the gdm3 problem.

This makes me think there is an underlying issue with xwayland/wayland/xorg (something is missing?) but I don't know enough to debug it. Any suggestions appreciated.

---

### Post by TheFu on 2022-05-31
nvidia GPUs should be using xorg.
I didn't think the migration from 21.10 to 22.04 was offered until 22.04.1 gets released. Thanks for being an alpha tester.

---

### Post by #&amp;thj^% on 2022-05-31
I believe OP is using  radeon 5700xt.
just to help you and us show this please:
```
ps -ef | grep polk
```
I guess while were here also include:
```
ps -ef | grep polk--debug

```

---

### Post by TheFu on 2022-05-31
> **1fallen said:**
> I believe OP is using  radeon 5700xt. 

Wow, Senior moment for me. Seem to be more of those.

---

### Post by #&amp;thj^% on 2022-05-31
> **TheFu said:**
> Wow, Senior moment for me. Seem to be more of those.

I'm right there with you..:)

---

