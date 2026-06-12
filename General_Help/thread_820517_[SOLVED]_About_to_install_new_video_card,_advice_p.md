---
title: "[SOLVED] About to install new video card, advice please!"
date: 2008-06-06
forum: General Help
---

### Post by Triple_X on 2008-06-06
Hello all,

I am making the switch from an ATI x1950 Pro (256MB) to an Nvidia 8800GTS (620MB) today.
My question is, what is the best way to uninstall/install new hardware such as this with Ubuntu? Is it best to simply open EnvyNG and use the uninstall driver option, shut down, replace card, boot up, and reinstall driver using EnvyNG? Anything else need to be removed or changed prior to shutting down?


Thanks!

---

### Post by kpkeerthi on 2008-06-06
> 
Is it best to simply open EnvyNG and use the uninstall driver option, shut down, replace card, boot up, and reinstall driver using EnvyNG?

Perfect. You got it.

---

### Post by pedro_orange on 2008-06-06
I have an Nvidia 8800 series, I would recommend using the Restricted Drivers Manager to install the drivers for you.
I've used Envy before and it's not worked as well as Restricted Drivers did.

I'm not sure about you uninstalling the old drivers, I'm sure you have to do something cause your xserver-xorg.conf will have all the details for the ATI card. However doing a sudo dpkg-reconfigure -phigh xserver-xorg would probably do the trick and sort ur x config file.

---

### Post by Triple_X on 2008-06-06
great, thanks a bunch to both of you!

---

