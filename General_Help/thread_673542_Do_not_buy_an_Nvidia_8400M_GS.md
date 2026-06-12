---
title: "Do not buy an Nvidia 8400M GS"
date: 2008-01-20
forum: General Help
---

### Post by jobeirne on 2008-01-20
I've had an awful experience with this graphics card. I paid a good sum of money to Dell for an Inspiron 1420 and chipped in the extra for the 8400 dedicated card, wanting to ensure good compiz performance. Ironically enough, I got the opposite. My eeePC (I kid you not) runs compiz more smoothly than this card. I'm not sure if it's a problem at the driver level, but lemme just say there is a problem.

For the love of your wallet, DO NOT buy the 8400M GS card if you want 2D performance. It runs games fine, though.

---

### Post by Bodsda on 2008-01-20
hhmmm,.,. sounds like driver probs,.,. cause my Nvidea 7600 gt runs compiz like a charm. If u go ,. System-->Admin-->Restricted Drivers Manager. does that give u anything for ur card?

---

### Post by jobeirne on 2008-01-22
Yeah, I got the restricted driver for the card, but even with compiz disabled the effects are choppy. This problem persists even in Vista and XP.

---

### Post by BobLand on 2008-01-22
I have the 8400 GS.  I had choppy graphics until I installed the nvidia new drivers in synaptic.  If you are not seeing these drivers then 
```
cat /etc/apt/sources.list|less
```

If your "deb..." files are commented out then the drivers will not appear.  Comment out all the deb files then look back into synaptic.  If not, then reboot.  You should see the nvidia drivers, specifically, ***nvidia_glx_new***.  Select this driver, apply and hit ctrl-alt-backspace.

You should see excellent graphics.

hope this helps,
bobland

---

### Post by DaF101 on 2008-07-21
I would return it, It sounds like there is something wrong with the GPU.

I have the 8400GS in my laptop and it runs great in Compiz and in Vista, infact in Wow it has gone up to 60FPS and averages around 40. Something might be wrong with the card or the driver.

---

