---
title: "Bad to operate in recovery mode?"
date: 2008-01-22
forum: General Help
---

### Post by Fittersman on 2008-01-22
for some reason my nvidia driver i installed only seems to work in recovery mode (after i type in 'telinit 3' in console). Is it bad to run in this run level? or is it ok? If it is ok, is there anyway to make the normal mode run like recovery mode + telinit 3? Or is it possible to make the driver work in normal mode?

I already tried envy, but that just made things worse... Ubuntu always wants to run in "low graphics mode" now, it never just shuts down the x server, and after i installed and ran envy it tried to run in low graphics mode, but the screens top right corner was in the center of the screen instead of being in the top right corner, and i couldnt move the mouse anywhere out of the bottom left corner because of this...

so... anyway to make my nvidia driver work properly when it is supposed to?

---

### Post by bodhi.zazen on 2008-01-22
Well it is less then optimal as recovery mode = logged in as root.

"recovery mode" is run level 1, so when you telinit 3 you change to run level 3.

2 is default, and 2 = 3 = 4 = 5 with a default Ubuntu install.

I suppose you could telinit 3, start GDM, and log in as your normal user. Don't forget to log out as root.

It is sloppy.

What video card are you using and what did you do to install the nvidia driver ? Did you remove nvidia-glx and nvidia-glx-new ?

---

### Post by Fittersman on 2008-01-22
i log in as my normal user after i "telinit 3" and im using an nvidia 8600M GS video card

UPDATE: I just restarted my computer and went back into recovery mode then did "telinit 3", but it seems to have the same problem as if i started in the normal mode. So i reinstalled the driver in run level 1 (even though it is not recommended, it seems to work) then did "telinit 3" and its working again. Something is happening to it during the reboot.

---

### Post by bodhi.zazen on 2008-01-23
The only time I have run into this problem is when I had nvidia-glx installed.

Try removing nvidia-glx and re-install the nvidia driver one last time (I hope).

---

### Post by Fittersman on 2008-01-23
i just ran a search in synaptic for "nvidia-glx" and it found it, but it is not installed, any other ideas? should i try installing it maybe?

---

### Post by bodhi.zazen on 2008-01-23
no, don't install it, it conflicts with the nvidia driver.

try looking to see if you have nvidia-glx-new

If so that is a little harder to remove.

---

### Post by Fittersman on 2008-01-23
no, that isnt installed either. (that being nvidia-glx-new)

---

### Post by Fittersman on 2008-01-25
its all sorted out now, a new envy was released on the 24th and that fixed the problem.

---

