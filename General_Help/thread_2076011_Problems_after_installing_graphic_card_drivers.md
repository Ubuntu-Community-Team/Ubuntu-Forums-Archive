---
title: "Problems after installing graphic card drivers"
date: 2012-10-25
forum: General Help
---

### Post by Andy1957 on 2012-10-25
Hello there

I installed 12.10 a few days ago and everything has been fine until I downloaded the Nvidia drivers from the software centre. Now, whenever I boot into Ubuntu, I've lost the side bar and the top menu bar and the screen resolution is much lower than it was (everything looks much bigger on the screen). Thinking I had probably corrupted the graphic card drivers, I reinstalled Ubuntu (selecting option 1 -  not to overwrite the settings) but unfortunately, this hasn't made any difference.

My graphics card is a Nvidia GeForce 6150se nforce 430. I'm guessing I need to enter something via Terminal (which I can access via CTRL/ALT/T) but I've no idea what I'm afraid.

I'd be grateful for any help.

Thanks

---

### Post by danielbauwens on 2012-10-25
Is it possible your screen settings are messed up?

If you go to:

```
System Settings > Screen
``` 

You can edit the screen size.
It might be your screen resolution is smaller then your actual screen which make the side and top bars invisible.

---

### Post by garginis on 2012-10-25
You've lost sidebar and topbar because compiz doesn't work.It's probably because you've installed drivers that are not compatible with ubuntu 12.10. To fix this you should remove your current drivers and install open source drivers.To remove your current drivers type this in terminal: 

```
sudo apt-get purge nvidia-current
```

---

### Post by shreepads on 2012-10-25
Did you miss any specific features that caused you to install the NVidia drivers from Software Centre? Do you remember exactly which Nvidia driver you installed, was it nvidia-current?

If so, after removing nvidia-current (as per post above) try the almost-latest stable NVidia drivers for your card:

sudo apt-get install nvidia-experimental-304

---

### Post by Andy1957 on 2012-10-25
> **shreepads said:**
> Did you miss any specific features that caused you to install the NVidia drivers from Software Centre? Do you remember exactly which Nvidia driver you installed, was it nvidia-current?

If so, after removing nvidia-current (as per post above) try the almost-latest stable NVidia drivers for your card:

sudo apt-get install nvidia-experimental-304

No, I just tried to fix something that hadn't broken!! I'm pretty sure it was the current stable version I installed.

I'll try removing the existing drivers and running sudo apt-get install nvidia-experimental-304 this evening.

Thanks for everyone's help.

---

### Post by timgood on 2012-10-25
Try this:

```
sudo apt-get remove nvidia-current
```

Then:

```
sudo apt-get install linux-headers-generic nvidia-current
```

Hope this helps.

---

