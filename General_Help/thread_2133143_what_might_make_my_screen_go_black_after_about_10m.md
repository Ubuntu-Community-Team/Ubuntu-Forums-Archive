---
title: "what might make my screen go black after about 10min"
date: 2013-04-07
forum: General Help
---

### Post by andrewrz on 2013-04-07
Im' running lubuntu (ubuntu version 12.10 amd alt)  and it seems there Is a good amount of redundacy in the screen sleep function. I checked double checked and trippled checked  the gui options: screen saver, powermanager. I have also added some code to my xorg.. 

"Section "ServerFlags"
    Option         "BlankTime" "0"
    Option         "StandbyTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
EndSection"

I checked somthing else on the terminal, forgot the command but I said it was disabled.
even just giving me a list of everything that pretains to screen sleeping would help me out greatly.

smplayer thankfuly is able to overides this, but it's a pain watching hulu or youtube, and just in genral.
thankyou

---

### Post by matt_symes on 2013-04-07
Hi

Is your problem dpms settings ?

From the terminal...

```
xset -dpms
```

or

```
xset dpms force off
```

Try it then watch a video. Does it still blank the screen ?

I'm not sure if that will persist after a reboot. so it may have to be made permanent.

Kind regards

---

### Post by mike555 on 2013-04-07
You might want to install " Caffeine ", it will stop the screen from blanking.

---

### Post by vasa1 on 2013-04-07
> **mike555 said:**
> You might want to install " Caffeine ", it will stop the screen from blanking.
More on Caffeine here: [http://askubuntu.com/a/80700/25656](http://askubuntu.com/a/80700/25656)
And you may want to look at this as well: [http://askubuntu.com/a/246551/25656](http://askubuntu.com/a/246551/25656)

---

### Post by andrewrz on 2013-04-08
thanks, caffine works great!

---

