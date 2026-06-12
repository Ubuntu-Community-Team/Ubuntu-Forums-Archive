---
title: "Multiple monitors and window positions."
date: 2021-11-16
forum: General Help
---

### Post by uros-likar on 2021-11-16
I have dual monitor setup (Main + Side) and I noticed some weird behavior with window positioning. At first I didn't care much but now is becoming more and more annoying, because disturbs my workflow. 

One annoyance is that sometimes I get login screen on one monitor, sometimes on other and sometimes on both !?

The main problem is window position. When I start work I open all applications and position them however I need them. If I leave my PC for few minutes monitors are turned off automatically. When I come back to PC all windows are on different positions. Sometimes some window is half on one monitor and half on other, sometimes window switch positions, what I had on the left is on the right and vice versa. And sometimes windows from one monitor are moved to another.

I'm doing something wrong or there is a problem with multiple monitors? Is there a solution?

Thank you

---

### Post by DuckHook on 2021-11-16
I have one computer with a dual monitor setup and it too shifts logon dialogue boxes with each boot. I've found that the reason for this is mouse placement. The logon dialogue box occupies whichever monitor contains the mouse cursor. Moving the mouse around will switch my logon dialogue box. I've never seen it on both though. It's not a big deal for me. Since my interaction with this dialogue box is all keyboard, it doesn't matter which monitor it shows up on.

Shifting window positions are a different matter. I've never experienced that. When you say:> …monitors are turned off automatically…what do you mean by that? Do your monitors actually power down? If so, then it is possible that the Display Server or Window Manager figures that it needs to redraw from scratch on wake up and does so according to some internal logic or settings that you can't access. Try blanking your screen or running a screensaver instead of powering down your monitors. That way, the Display Server is never notified of a lost video signal.

---

### Post by dragonfly41 on 2021-11-16
Without answering the "why" question my suggestion is to have some reset script which brings your windows back to a defined state. One such command is xdotool.

[https://www.systutorials.com/docs/linux/man/1-xdotool/](https://www.systutorials.com/docs/linux/man/1-xdotool/)

But there are other scripts to run. This might be a workaround until you can answer "why?".

---

### Post by uros-likar on 2021-11-16
Well, this is default kubuntu behavior, I didn't changed anything. After around 10 minutes  of inactivity screen on monitors goes blank and ubuntu goes to lock screen. Probably I need to tweak those power settings. I'll try it but still this is annoying. I don't have such problems on windows 10.

---

### Post by DuckHook on 2021-11-16
> **dragonfly41 said:**
> Without answering the "why" question my suggestion is to have some reset script which brings your windows back to a defined state. One such command is xdotool.

[https://www.systutorials.com/docs/linux/man/1-xdotool/](https://www.systutorials.com/docs/linux/man/1-xdotool/)

But there are other scripts to run. This might be a workaround until you can answer "why?".
I've run across this tool in other threads, but have never had occasion to try it. Do you know if it works with Wayland, or is it only usable on X11?

---

### Post by dragonfly41 on 2021-11-16
Don't know. But another favourite UI automation tool I use (xdotool on steroids) is Actiona which is a GUI.
After creating the MyScript.ascr, run it through
actexec MyScript.ascr.

I use this for all sorts of desktop/cloud configuration including having the equivalent of clicommander.

In this particular scenario I would use the Window object and keep all the windows parameters in an actionscript2 array in a Code box.

---

