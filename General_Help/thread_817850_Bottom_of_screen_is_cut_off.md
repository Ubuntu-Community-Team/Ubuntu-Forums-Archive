---
title: "Bottom of screen is cut off"
date: 2008-06-04
forum: General Help
---

### Post by sparkguitar05 on 2008-06-04
Screenshots posted.  How do I fix this?  I can still click in the orange area, I just can't see anything.

I'm using Ubuntu Hardy with an ATI Radeon x300.  (In case anyone is confused, I'm using Fedora wallpaper because they don't use an ugly brown.)

---

### Post by iaculallad on 2008-06-04
Try to adjust your screen to a lower resolution (click apply) then adjust it again using your previous resolution. Hope that could work.

System->Preferences->Screen Resolution

---

### Post by sparkguitar05 on 2008-06-04
Tried it.  Didn't work.

---

### Post by iaculallad on 2008-06-04
What about "refreshing" your desktop.

On your terminal:
```
killall nautilus
```

---

### Post by sparkguitar05 on 2008-06-04
> **iaculallad said:**
> What about "refreshing" your desktop.

On your terminal:
```
killall nautilus
```

Didn't help me.  All it did was open up my home folder. :(

---

### Post by iaculallad on 2008-06-04
Right click on your desktop, click "Change Desktop Background" . Select the "Background" tab, and on the "Style" select "zoom".

---

### Post by sparkguitar05 on 2008-06-04
It's not a problem with the desktop background.  My panels are cut off and my programs are cut off.  My system functions exactly like it would if someone took an orange-brownish strip of paper and glued it to the bottom of my monitor.

---

### Post by iaculallad on 2008-06-04
> **sparkguitar05 said:**
> It's not a problem with the desktop background.  My panels are cut off and my programs are cut off.  My system functions exactly like it would if someone took an orange-brownish strip of paper and glued it to the bottom of my monitor.

Try restoring panel first (Default) if it could resolve panel issue:
```

sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/panel
sudo pkill gnome-panel
```

---

### Post by sparkguitar05 on 2008-06-04
The panels DO work.  I know exactly where the show desktop button is on my bottom panel, and when I click that it brings me to my desktop.  If I click various spots at the bottom of my screen the windows will change.  Like I said, it's as if there is a piece of paper glued to the bottom of my monitor.

I've been fooling around with video card drivers, so I'm pretty sure that's where the problem lies.

If I change to a different resolution everything works fine.  Unfortunately, I simply can't work at a resolution other than 1280x1024.  It's worked fine for months and I know there has to be a way to get it to work again.

---

### Post by iaculallad on 2008-06-04
I've run out of suggestions, let's try to wait for other forum members to post their ideas :confused:

---

### Post by sparkguitar05 on 2008-06-04
Thanks for trying to help.  I really appreciate it.

Anyone else have some ideas?

---

### Post by Hotaka on 2008-06-14
I'm also suffering from this exact problem.

I can provide screens if needed.

Can anyone help? Thank you.

Edit: I'm using an ATI 9700 Pro with the latest drivers

---

### Post by jrpfrecklestoo on 2010-04-11
Also having the same exact problem only on mine the system will not allow me to change resolutions. I don't remember doing anything that would trigger this. I am dual-booting ubuntu with vista and one day logged into my ubuntu partition and it was like it is now (exactly as the OP's screens). Can anyone suggest anything else?

---

### Post by jrpfrecklestoo on 2010-04-11
Update: I fixed this problem by plugging in my monitor into the other dvi-out on my video card. Don't know if that would work for anyone else or why exactly it worked for me but it did. Could be because I went from dual screening my 32" HDTV and this monitor to just this one monitor. I am clueless but glad it worked. Maybe this will help others.

---

