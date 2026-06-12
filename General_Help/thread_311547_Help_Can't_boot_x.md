---
title: "Help: Can't boot x"
date: 2006-12-03
forum: General Help
---

### Post by Vord on 2006-12-03
Well, I screwed up. I was following a guide to get my mouse buttons working in firefox, and I apparently messed something up. I was asked to to edit /etc/X11/xorg.conf, and ctrl+alt+backspace, when it tried reloading, I got a horrible blue/gray screen saying in big bold letters (paraphrasing, of course) "YOU ****** UP"

All in all, the error message and process of getting it is pretty inconsequential, I just need to know how to acces /etc/X11/xorg.conf on my install from live CD. If someone could please walk me through that, I'd appreciate it so much.

---

### Post by taurus on 2006-12-03
You can boot into recovery mode from GRUB menu and either edit /etc/X11/xorg.conf or reconfigure X again...

```
nano -w /etc/X11/xorg.conf
-or-
dpkg-reconfigure xserver-xorg
```

---

### Post by Vord on 2006-12-03
How do I boot from GRUB menu?

---

### Post by taurus on 2006-12-03
When you first turn on your computer, you will see the GRUB message with a count down!!!  Press Esc before the time is up and you will see the recovery mode as a second option!  Use the down arrow to highlight it and hit Enter to boot from it.

---

### Post by atoponce on 2006-12-03
Are you dual-booting?  It doesn't sound like it.  Right after POST, you will have a couple seconds to hit the 'ESC' button to get into the GRUB menu.  From there, select the recovery option.

---

### Post by Vord on 2006-12-03
Alright, back soon, then.

---

### Post by Vord on 2006-12-03
Alright, went in and edited everything that I needed to, booted right up. Thanks alot :D

---

### Post by atoponce on 2006-12-03
> **Vord said:**
> Alright, went in and edited everything that I needed to, booted right up. Thanks alot :D

No problem.  Glad you got it working! :)

---

### Post by LinuxVox on 2006-12-03
I just tried this option & still can't get xserver to load!

---

### Post by taurus on 2006-12-03
> **LinuxVox said:**
> I just tried this option & still can't get xserver to load!
Try what method, editing /etc/X11/xorg.conf or reconfiguring it with 

```
dpkg-reconfigure xserver-xorg
```

---

