---
title: "Cannot lock desktop anymore"
date: 2020-06-03
forum: General Help
---

### Post by manuman76 on 2020-06-03
Hi all, since a couple days I'm not able to lock my desktop anymore.

I'm on 20.04 (upgrade from 18.04) and when I use the lock button the screen just flicker one time, without any message.

I don't know how to debug this... tried xdg-screensaver lock  in the terminal with the same result...

Thanks for the help!

---

### Post by tea for one on 2020-06-03
Yes, it appears to have recently stopped working in Ubuntu 20.04.

The first time you lock the screen, you correctly report that the screen flickers.

However, if you then quickly lock the screen again, it mysteriously works.

It may be related to this bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1880793](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1880793)

---

### Post by tea for one on 2020-06-03
After further investigation:-

Kernel 5.4.0-33    Lock screen misbehaves
Kernel 5.4.0-31    Lock screen is OK

Using Ubuntu 20.04 with Gnome version 3.36.2

---

### Post by tea for one on 2020-06-03
Additional observations:- 

Kernel 5.4.0-33 in a Wayland session - Lock screen OK
Kernel 5.4.0-33 in a Xorg session - Lock screen misbehaves

Kernel 5.4.0-31 in a Wayland session - Lock screen OK
Kernel 5.4.0-33 in a Xorg session - Lock screen OK

@manuman76 - Can you try a Wayland session and see if the lock screen functions OK?

---

### Post by manuman76 on 2020-06-03
So, wait and see... thanks for the info!

---

### Post by manuman76 on 2020-06-03
I confirm, I tested the 4 possibilities and it's exactly as you said... guess i'll use Wayland for the time being.. didn't know about this, is there any cons using it ?

---

### Post by tea for one on 2020-06-04
> **manuman76 said:**
> I confirm, I tested the 4 possibilities and it's exactly as you said... guess i'll use Wayland for the time being.. didn't know about this, is there any cons using it ?

In previous iterations of Ubuntu, applications such as **synaptic** and **gparted** wouldn't open in a Wayland session. but I think that those difficulties have now been resolved.

I have also read that **snap packages** did not behave correctly sometimes, but, as I do not use snaps, I have no clear evidence.

---

### Post by tea for one on 2020-06-04
I've conducted a few more experiments and the lock screen behaviour is unusual.

Currently using a Wayland session.

If all application windows are closed - Lock screen behaves correctly

If any applications have windows open - Lock screen takes you to the log-in screen (and closes the app & sometimes disables gnome-extensions)

---

### Post by manuman76 on 2020-06-04
> **tea for one said:**
> I've conducted a few more experiments and the lock screen behaviour is unusual.

Currently using a Wayland session.

If all application windows are closed - Lock screen behaves correctly

If any applications have windows open - Lock screen takes you to the log-in screen (and closes the app & sometimes disables gnome-extensions)


Experiencing the same here.. after some more testing, the lock button just log me out most of the time. I'm only able to lock the screen via 'xdg-screensaver lock' from terminal.

Also, sometimes I'm also getting the disabled gnome extensions.

---

