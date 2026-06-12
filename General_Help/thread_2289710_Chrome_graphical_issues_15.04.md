---
title: "Chrome graphical issues 15.04"
date: 2015-08-06
forum: General Help
---

### Post by shyshy2 on 2015-08-06
New user, recently set up my old Alienware M15x (specs : [http://www.pcworld.com/product/310960/alienware-m15x-notebook.html](http://www.pcworld.com/product/310960/alienware-m15x-notebook.html)) to dual boot 15.04.

I've been running into some graphical bugs with Chrome (attachments). There's other random glitches that happen also (new tabs have blacked out zones that disappear after moving the mouse). I installed Chrome through the .deb package from the main site. Is this a Unity issue?

This doesn't happen on my older Dell laptop running 14.04.

---

### Post by howefield on 2015-08-06
Which drivers are you using for the graphics card ?

You could try unchecking "Use hardware acceleration when possible" in Chrome settings ?

---

### Post by shyshy2 on 2015-08-06
Disabling hardware acceleration does the trick! What exactly is the song and dance between my GPU and hardware acceleration on Chrome?

I'm not sure what drivers are installed. I'll report back.

---

### Post by howefield on 2015-08-06
> **shyshy2 said:**
> Disabling hardware acceleration does the trick! What exactly is the song and dance between my GPU and hardware acceleration on Chrome?

I'm not sure what drivers are installed. I'll report back.

No worries, if you don't know which drivers, that probably means that you are using the open source ones, you might try Additional Drivers to see if you are offered a proprietary driver for your Nvidia card.

---

