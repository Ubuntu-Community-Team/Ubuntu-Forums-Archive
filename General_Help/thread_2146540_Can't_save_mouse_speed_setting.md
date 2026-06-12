---
title: "Can't save mouse speed setting"
date: 2013-05-18
forum: General Help
---

### Post by ThePhysician on 2013-05-18
Under System Settings > Mouse & Touchpad there's no button to save my settings O.o

Using 13.04 64 Bit

Whaaaat?

I need my mouse to go slower...

---

### Post by pqwoerituytrueiwoq on 2013-05-18
changes are applied then you drop the slider, at least that is the case in xubuntu

---

### Post by ThePhysician on 2013-05-18
Yeah I'm having no such luck. I slide it down to 25% from 75%, try going back, or exiting, or hitting enter, go back into mouse and trackpad settings and it's at 75%. =(

---

### Post by ThePhysician on 2013-05-19
Anyone? My mouse is unusable this fast.

---

### Post by anoldone on 2013-05-19
```
man xinput
```

---

### Post by ThePhysician on 2013-05-22
Okay and none of those options look like mouse speed?

Anyone on why the standard settings menu is broken? Broke for just me or anyone else?

---

### Post by JolyonB on 2013-05-23
I have this problem too. By default, it looks like the slider is at 50% or so. When I drag it down to 25%, my pointer speed slows. However, when I close the window and reopen it, it's back at 50%. I don't know why it isn't saving, but it's very annoying!

---

### Post by anoldone on 2013-05-23
> **ThePhysician said:**
> Okay and none of those options look like mouse speed?(...)
Mouse isn't the solely input device you're using. Dig deeper, I'll start you off:
```
xinput --list
```

---

