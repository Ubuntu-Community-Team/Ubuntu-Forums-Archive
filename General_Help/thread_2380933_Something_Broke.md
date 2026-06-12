---
title: "Something Broke"
date: 2017-12-23
forum: General Help
---

### Post by Shmoogly on 2017-12-23
Hi, I was installing nvidia drivers through the point and click interface and then clicked cancel and proceeded to restart my computer. It was stuck in the screen where it says ubuntu and has those loading bars. It was stuck there for about 10 minutes and I then just hard reset. Now I can't log into ubuntu. During startup I never used to see anything before the ubuntu login screen, now I see some kind load screen and for one of them, Failed to start kernel module, I see a fail next to it. Then the ubuntu screen shows up but if I type my password, the sceen blinks black for a split second and then throws me straight back to the login screen. If I press ctrl alt f1, I can't log in. What's going on?

---

### Post by HermanAB on 2017-12-23
Hmm, aborting a video driver install is about the worst thing you can do, since you will almost always end up with a black screen.  There are three ways to fix it that I can think of:

1. If you have sshd running on that machine, then you can log in from another machine over the network and fix it from there.
2. If you have install media, then you can boot with that, mount the disk and fix it.
3. You can give up, backup your data and re-install.

To fix it, you need to hunt around in /etc for the video configuration files (Wayland? Xorg? xorg.conf? modules.conf?) and load a simple video driver (VESA?), so that you can get your display back, then restart.  

It has been more than ten years since I had these kind of issues, so I don't know how to fix it exactly these days!

---

### Post by Shmoogly on 2017-12-24
I'm in the process of re-installing my entire computer. The problem is that in Ubuntu I unmounted the DVD drive for no real reason other than I thought it couldn't hurt. Straight after that, the windows installer came up with an error saying that it can't locate drivers for my DVD drive. I also can't start Ubuntu installer from my DVD after I select it as my primary boot location. So I'm stuck. BIOS sees the DVD drive without a problem.

---

### Post by HermanAB on 2017-12-24
Well, does the machine have a USB socket and do you have a USB memory schtick?  

If so, copy the ISO file to the schtick using rawrite or similar on Windows, then reboot using USB.

---

