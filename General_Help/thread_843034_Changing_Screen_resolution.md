---
title: "Changing Screen resolution"
date: 2008-06-27
forum: General Help
---

### Post by mastrgamr on 2008-06-27
im new to linux (brand brand new) and i installed wubi 8.04 with Ubuntu on it. the my max screen resolution is 1280x800 and the Linux i installed max resolution only goes up to 800x600.. its annoying seeing everything on my screen so big how can i change it to whatever screen resolution i want. (preferably my computer's max resolution)

---

### Post by buntunub on 2008-06-27
K. Need more info here like whats your hardware, etc. However, you can always do the tried and true boot to safe mode and do

```
dpkg-reconfigure xserver-xorg
```

If your hardware supports restricted drivers like Nvidia, then load them and use the nvidia-settings in System>Administration to reconfigure as well. The ubuntu wiki has some excellent guides for all this as well.

---

### Post by mastrgamr on 2008-06-27
> **buntunub said:**
> K. Need more info here like whats your hardware, etc. However, you can always do the tried and true boot to safe mode and do

```

```

If your hardware supports restricted drivers like Nvidia, then load them and use the nvidia-settings in System>Administration to reconfigure as well. The ubuntu wiki has some excellent guides for all this as well.

I dont get what u mean by hardware? i do have nVidea graphics though

and where do i put that stuff like "dpkg-reconfigure xserver-xorg"

---

### Post by hulten on 2008-06-28
> **mastrgamr said:**
> and where do i put that stuff like "dpkg-reconfigure xserver-xorg"

In a console or xterm.  Put "sudo " in front of the command.

You could also try the xrandr utility (run it as a normal user in a xterm).

---

### Post by mastrgamr on 2008-06-28
**_Its fixed now.. nvm the post. i forgot what i did but my nidia drivers are enabled now._**

---

