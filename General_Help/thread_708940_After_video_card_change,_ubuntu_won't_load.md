---
title: "After video card change, ubuntu won't load"
date: 2008-02-26
forum: General Help
---

### Post by weasel7711 on 2008-02-26
I recently upgraded my video card to an NVIDIA GeForce 8600. However when I select to boot up linux it just goes to black, then my monitor says there is no signal and I don't hear any startup sound. (im a noob) I can start linux in diagnostic mode (all text) but I don't know enough of what to do in order to fix it. I have the CD and if I boot from the CD it loads fine, but the version on my HDD wont work. Help.

---

### Post by taurus on 2008-02-26
You need to reconfigure your X server again after you changed your video card.  While in the recovery mode, type 

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by weasel7711 on 2008-02-28
I just tried that however it said something about not being able to use -r because of remove or something. Any other way to reconfigure x server?

---

### Post by taurus on 2008-02-28
From my previous post, the first command is to reconfigure your X server in a recovery mode and the second command is to reboot your machine after you have reconfigured X.  

So, are you talking about this command?

```
shutdown -r now
```

---

### Post by weasel7711 on 2008-02-28
I typed in the first line, and it gave me some issue referencing -r and just said there was an error

when I wanted to restart, I typed in the second command

---

### Post by taurus on 2008-02-28
What exactly did you type?

---

### Post by weasel7711 on 2008-02-29
Well, I redid it, however I got a different result, yet still not the desired one. Apparently I thought there was a space in between dpkg and -reconfigure so that is why it gave me that error last time. However this time I typed in exactly how it was written in this thread:
dpkg-reconfigure -phigh xserver-xorg

and all I got was... nothing. The cursor just went to the next line and continued blinking for over a minute until I got impatient and started hitting enter, then I tried to exit or restart and that didnt do anything either. I ended up doing a hard power down since it was only  logging my key strokes and not doing anything when I pressed enter. I'm not sure what to do.

---

