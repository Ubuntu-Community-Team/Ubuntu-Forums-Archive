---
title: "System breaking problem- whenever I open a terminal, display goes black &amp; must reboot"
date: 2021-03-16
forum: General Help
---

### Post by zyodei on 2021-03-16
This problem started when I sold my Nvidia 1080 graphics card without first removing the drivers. I downgraded to an AMD HD7870 GPU.

I used 'nomodeset' and totally removed everything nvidia, added 'nouveau' to /etc/modules, and everything seemed fine. I was able to boot into my 18.04.5 desktop.

However, when I pressed Ctrl+Alt+T to go into a terminal for something, my monitor went black (no input), and I had to restart the computer. This happened consistently.

Unable to figure it out, I decided to just reinstall, going with 20.04.2 MATE. (keeping my home partition)

However, after reinstalling, I have the exact same problem! When I open a terminal of any kind (including the basic xterm), I have to restart the computer. This is a major problem for me.

I am able to use Ctrl+Alt+F2 and get into a terminal that way, but obviously this doesn't work as a replacement for a proper windowed terminal. 

From this terminal, I was able to see that the last two lines of dmesg were:

fbcon: taking over console
Console: switching to colour buffer device 160x45

Has anyone ever had this issue before? In ten years I've never, ever had an issue that wasn't solved with a reinstallation of linux. 

Any help is greatly, greatly appreciated. Thank you!

EDIT: Swapping in an old GTX750ti I had sitting around fixed the issue, I can now open terminals as normal. But I had plans to use that card elsewhere! I'm still curious what the cause of this might be.

---

### Post by HermanAB on 2021-03-16
When I get these 'black screen' issues, I install/enable sshd, then log in over the network from another machine.

Sometimes, one can log in and fix something in the boot sequence 'blind', by doing the same thing on another similar machine and copying the keystrokes one by one - 'Monkey See, Monkey Do' style.

The final solution is of course to re-install, but do make backups of your data first.

---

### Post by Impavidus on 2021-03-16
As far as the graphics are concerned, opening a terminal isn't any different from opening any other GUI application. The window manager creates a window and the application writes pixels to it. Even most full screen applications don't switch display mode; they just make a window that covers the entire display. The one thing that terminals do and other applications don't is that they open a shell, which will run some commands automatically. Those commands can be in files like .bashrc and .profile. Maybe you somehow got a command in there that attempts to change display settings and makes the sceen turn black.

---

### Post by zyodei on 2021-03-16
+1000 to Impavidus here!

Some time last year I had put the command 'xrandr --output HDMI-0 --off' into my .bashrc. To disable by default a secondary TV monitor I hardly ever use. I haven't used this computer for around eight months because I got separated from my home because of Covid restrictions, and had totally forgotten I'd done this.

I was using the Displayport on the GTX1080; I'm using the HDMI on the 7870 I replaced it with. That's why this problem only cropped up once I started using the HDMI output.

That's why this bug survived a reinstall of the system. I thought, logically, that it might be something in my /home/ partition - but couldn't for the life of me think what it would be.

It isn't an Ubuntu problem, it's 100% a user error. Thank you so much for the concise and perfect advice :D

---

### Post by Impavidus on 2021-03-16
Good. Could you mark this thread as solved? Thread Tools -> Mark as solved.

---

