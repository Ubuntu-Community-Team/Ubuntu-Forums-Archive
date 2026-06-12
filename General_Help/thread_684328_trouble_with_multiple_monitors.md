---
title: "trouble with multiple monitors"
date: 2008-02-01
forum: General Help
---

### Post by ntrgc89 on 2008-02-01
I've been having strange issues with the display on my external monitor.

These didn't start recently, they were there even when I was running Ubuntu off the live CD (but at that point I thought they would be over after an install).

What I have set-up is a thinkpad T41 with a samsung syncmaster 940BF hooked up to the analog-out port. In Windows XP the setpup worked flawlessly: the laptop monitor was off (I keep my laptop in the keyboard slider shelf so the lid is always closed anyway) and everything was being displayed on the samsung, which has a higher resolution,

In Ubuntu, the laptop monitor is on by default, and it displays onto the external monitor, which is operating at native resolution (latop is 1024x768 and samsung is 1280x1024)

So what happens is that the taskbar, instead of being at the bottom of the screen, is about 25% up from the bottom of the screen and only goes about 75% of the way across.

All the extra space to the right and below the taskbar is available for programs, but it's friggin' annoying as hell with the taskbar lying where it is.

I've tried fixing it in Screen & Graphics with no luck, it tells me to log off to effect changes, but it never saves the settings.

By the way, the video card is:

32MB ATI Mobility Radeon 7500

The image below shows what displays on the samsung. The laptop monitor doesn't display anything below or to the right of the taskbar, it looks just fine.

[[IMG]http://img217.imageshack.us/img217/6980/capture1pe2.th.png[/IMG]](http://img217.imageshack.us/my.php?image=capture1pe2.png)

---

### Post by lian1238 on 2008-02-01
Try this:
```
killall gnome-panel
```
(need to put sudo before it?)

---

### Post by ntrgc89 on 2008-02-01
No, I don't want to remove the panels!!!

I want the setup to be like I had in XP, everything displayed on the external and the laptop monitor turned off.

To restate the problem, I am having issues with using an external monitor and Ubuntu doesn't save the changes I make in the Screen & Graphics prompt. It can't detect the external monitor, and I think it has some issues with the video card. 

But thanks for trying to help, and no, you don't need sudo in front of it.

---

### Post by ntrgc89 on 2008-02-01
OK, well, after trying so many different things that I'm not even sure which action had which effect, I'm in a different situation.

What I remeber doing correctly was disabled the fglrx drivers, those simple work poorly with ATI cards it seems. At that point the resolution was higher on the external and I could switch from the laptop monitor to the external using Fn+F7 like I normally do.

So I tried to raise the resolution on my external monitor to it's native one, but then everything fell apart. I'm now forced to run in low graphics mode and no matter what I do, Screen&Graphics refuses to save any changes I make to the set of drivers running the card, which is now set at Generic VESA-compliant video cards. I'm going to start a new thread asking for help with that, since the problem is slightly different than what I had originally posted.

---

