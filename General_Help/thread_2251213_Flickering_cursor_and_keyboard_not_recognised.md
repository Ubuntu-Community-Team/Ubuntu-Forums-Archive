---
title: "Flickering cursor and keyboard not recognised"
date: 2014-11-02
forum: General Help
---

### Post by Bhakti108 on 2014-11-02
I have two issues with Ubuntu 14.04 that i could do with some help with. 

The first is the flickering cursor. I know the problem but not the permeanent fix. The problem is that my system is seeing two displays, the Dell monitor and an Unknown monitor that doesn't exist. This results in the cursor flickering and disappearing randomly. The fix is to turn off the uknown monitor from system settings, but it only does that for the current session.  The question is -- how do I turn it off permanently?

The second is weird I have an logitech wireless keyboard. Probably 7 out of 10 times I boot, it is not recognised or initialised at the login screen. I have to do a restart or a full reboot a number of times and then it works. It is not batteries I have changed them, it is not the connector USB I have put that in differetn slots. 

Does anyone know the cause and fix please?

Thanks

---

### Post by QIII on 2014-11-12
Hello!

For the keyboard, we really need to rule out a hardware fault before moving on.  Can you test it on another machine and let us know what you find?

As for the display issue, could you give us some detailed information about your machine's hardware?  What is the graphics adapter?  Are you running a proprietary driver?  Does this file exist:  /etc/X11/xorg.conf?  (It should not by default, but may if you have installed a proprietary driver.)

Cheers!

---

### Post by Bhakti108 on 2014-12-08
Sorry to have taken so long to reply, I sort of forgot I had posted for help. 

No to the /etc/X11 file
Graphics card is  NVIDIA GK106GL [Quadro K4000] (rev a1)
I am using Nouveau driver 

I tried using the NVIDIA one but couldn't get the correct resolution to display.

My monitor is a Dell Ultra Sharp 27" 

The flickering seems to have improved after I installed the NVIDIA driver and then uninstalled it. I was able to select the ghost monitor, turn it off and it has stayed turned off. But the boot issue continues.

Thanks

---

