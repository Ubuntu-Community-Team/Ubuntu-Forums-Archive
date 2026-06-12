---
title: "Strange lockups, reproducible."
date: 2008-06-19
forum: General Help
---

### Post by chaosrl on 2008-06-19
Hey all,

I'm pretty much stuck. I've been running Hardy for a couple months now on my T60, and it's been giving me almost no problems at all. Starting from the beginning, it would give me a few "Suspend Failed" errors *after* I successfully suspended and woke up, so I didn't pay much attention to that.

However, earlier today (possibly after a kernel update from 2.6.24-19.33 to .34?), something odd happened. I found my Fn+Sleep key stopped functioning, as well as my Fn+Brightness Up/Down keys. My Fn+Wireless and Media keys still work. The weirdest thing is that when I click the "Logout" button or click it from "System->Quit," the whole system freezes up, and requires me to use Ctrl-Alt-Backspace to return to the login screen.

From the login screen, "Actions->Suspend" works like a charm. I just can't seem to do it after I log in. Any suggestions would be appreciated, let me know if you need more information on my system! Thanks!

Edit: I forgot to mention, when I shutdown from the login screen (as I can no longer do it when logged in), the shutdown process appears to hang on the "* Running local scripts..." stage, and requires a Ctrl-Alt-Del to actually begin the shutdown process.

Edit 2: Sorry, but when I was putting my computer to sleep for the night, I realized that the Fn+Sleep/Brightness buttons don't work in the login screen either. I can only put it to sleep using the menu.

---

### Post by chaosrl on 2008-06-19
Ok. It looks like I posted waaaay too early for my own good. I've solved the problem, so mods can remove this or mark it solved or what have you.

The problem was powertop asked me to kill gnome-power-manager, and I disabled it in my sessions so it wouldn't "suck power," thinking that it was just the battery icon in my notification tray. Seems like that was the only thing that was messing up my computer. :)

---

