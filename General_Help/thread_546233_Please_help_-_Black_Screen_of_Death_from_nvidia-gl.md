---
title: "Please help - Black Screen of Death from nvidia-glx"
date: 2007-09-08
forum: General Help
---

### Post by Ranguvar on 2007-09-08
I am at my wits end.

I installed Kubuntu 7.04 Feisty AMD64 a bit ago. Everything worked great until I installed nvidia-glx.

I shutdown X, and saw a prompt for half a second before getting a black screen with a flashing line at the top-left. Now, whenever I boot, I boot, I get this. Recovery mode works, but startx does not (no screens error). sudo nvidia-glx disable said it worked, but did not fix it. X config says I'm using the the nv driver.

One last thing, I did install Beryl at the same time. Don't think that's the problem.

I have a nVidia GeForce FX 5200 AGP card.

Any help at all would be fantastic, thanks.

---

### Post by niki001 on 2007-09-08
try installing youre graphics drivers with the aid of ENVY. Works fine with me.
sudo apt-get install envy

good luck

---

### Post by Ranguvar on 2007-09-08
Would that take care of the current issue too, or only for use after fixing this and getting back on non-accelerated X?

---

### Post by Ranguvar on 2007-09-08
If it's alright, I'll bump this...

Thanks to anyone who tries to help. I just want to get back to square one so I can do things the right way. Rather not reformat.

---

### Post by Crafty Kisses on 2007-09-08
> **Ranguvar said:**
> I am at my wits end.

I installed Kubuntu 7.04 Feisty AMD64 a bit ago. Everything worked great until I installed nvidia-glx.

I shutdown X, and saw a prompt for half a second before getting a black screen with a flashing line at the top-left. Now, whenever I boot, I boot, I get this. Recovery mode works, but startx does not (no screens error). sudo nvidia-glx disable said it worked, but did not fix it. X config says I'm using the the nv driver.

One last thing, I did install Beryl at the same time. Don't think that's the problem.

I have a nVidia GeForce FX 5200 AGP card.

Any help at all would be fantastic, thanks.

You'd probably have to install the legacy drivers for that, and if you still have the black screen after that, you probably want to reconfigure your X server.

---

### Post by Ranguvar on 2007-09-09
Thanks, I was going to try a reconfigure but forgot. X config says I'm back to nv driver already though.

As for the legacy drivers, I thought that was for the GeForce3 and lower only?

---

### Post by Ranguvar on 2007-11-05
Just an update - Installed Gutsy 64bit, and used Envy. Works perfect!

---

