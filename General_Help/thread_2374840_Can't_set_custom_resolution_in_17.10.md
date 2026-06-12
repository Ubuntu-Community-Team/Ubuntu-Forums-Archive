---
title: "Can't set custom resolution in 17.10"
date: 2017-10-19
forum: General Help
---

### Post by bojan2 on 2017-10-19
My monitor supports 1280x1024
In previous version i used [this]("https://askubuntu.com/questions/377937/how-to-set-a-custom-resolution") way to set resolution and it worked.
In 17.10 there are two problems with this:
1. After --addmode command my resolution is not shown on the list of available resolution in settings
2. Trying to set custom resolution via command:
```
xrandr --output XWAYLAND0 --mode 1280x1024_60.00

```I get error:
xrandr: Configure crtc 0 failed

My xrandr output:
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
XWAYLAND0 connected (normal left inverted right x axis y axis)
   1024x768      59.92 +
   1280x1024_60.00  59.89

Video card: Intel hd 2000

---

### Post by Autodave on 2017-10-19
What video card do you have? Did you install any drivers for the card and if so, where did you get them from?

---

### Post by bojan2 on 2017-10-19
> **Autodave said:**
> What video card do you have? Did you install any drivers for the card and if so, where did you get them from?
Video card is intel hd 2000
I did not installed drivers, i am using default i915 driver, which was installed by ubuntu on OS install

---

### Post by bojan2 on 2017-10-20
bump

---

### Post by aavuso on 2017-10-21
I went back from Wayland to Xorg, as described at: [https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/) 
And after reboot the previous settings, described in the tutorial you mentioned, worked as usual.

In Ubuntu 17.10, restart your system. At the login screen, under the  password field, you&#8217;ll see a gear icon. Just click on it and you&#8217;ll see  two options here.
[IMG]https://itsfoss.com/wp-content/uploads/2017/10/switch-wayland-xorg.jpeg[/IMG]

    The default Ubuntu means it will be using Wayland while Ubuntu on  Xorg obviously means it will use Xorg. You can select Ubuntu on Xorg to  use Xorg here.

---

### Post by bojan2 on 2017-10-22
> **aavuso said:**
> I went back from Wayland to Xorg, as described at: [https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/) 
And after reboot the previous settings, described in the tutorial you mentioned, worked as usual.

That did it, thank you

---

