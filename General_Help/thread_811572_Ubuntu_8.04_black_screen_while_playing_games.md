---
title: "Ubuntu 8.04 black screen while playing games"
date: 2008-05-29
forum: General Help
---

### Post by Christor on 2008-05-29
Hi there.

I have a problem when trying to games on Ubuntu 8.04, the screen goes black in full screen mode with a resolution higher than 800x600.
I searched the forum and noticed that a few other people got the same problem but didn't get help or it didn't fix their problem.

I got no problem with playing games in 800x600 resolution, but the games that starts with a higher resolution is a problem. Because I can't change the resolution down to 800x600.

Any help is appreciated and I will gladly help with output if you give me the code/command to run them.

Thanks in advanced Christor.

---

### Post by pedro_orange on 2008-05-29
What games are we talking about here?
Are you using WINE to play it?
Did you follow a guide? Please show me.
What graphics card do you have?

---

### Post by Christor on 2008-05-29
All games with resolution over 800x600, wine games and native games.

Example 1: Installed Neverputt which started in windowed mode. Switched to 800x600 full screen mode which worked, but when I change the resolution to 1024x768 I get a black/blank screen.

Example 2: I installed Warcraft III FT and get a black/blank screen (default resolution: 1024x768 full screen), set windowed mode in wine and change resolution to 800x600 reverse wine settings to full screen mode and game works.

GFX card: Nvidia 7950GT.

---

### Post by michaelzap on 2008-05-31
I also have a Nvidia card and the same problem. I'm trying to play Urban Terror, but no full screen resolution is supported. I can play within a window just fine, but that's no way to play an FPS.

This worked fine in Gutsy, but now that I'm on a fresh Hardy install it doesn't. I guess I need to modify my xorg.conf file or something like that? Anyone have any suggestions?

---

### Post by pedro_orange on 2008-06-01
I'll try and repicate your error this evening

---

### Post by drink on 2008-06-27
I'm having the same problem with quadro fx1500m. Happens with basically any version of nvidia drivers (have tried nvidia-glx-new, nvidia-glx-new-dev-envy, and the latest binary drivers (177.13). This also did not happen to me on gutsy. However on gutsy I have the WSOD running xserver-xgl. (I have disabled Xgl but still have the same problem.)

I'm getting pretty tired of Ubuntu breaking stuff. First it was PRISM3, now it's fullscreen GL apps.

I managed to run ut2003 (for linux) in a window and then SWITCH to fullscreen at my full resolution. I suspect the problem only occurs when changing resolution and/or color depth.

---

### Post by michaelzap on 2008-06-27
I guess I should've followed-up before, but this problem was fixed for me by some driver or xorg update in the last couple weeks.

---

### Post by caarika on 2008-08-08
i had the same problem too. when you set maxfps to 30 in the .cfg file, you can run it at 1280x1024

---

### Post by connorh123 on 2008-08-18
I had this same problem with running Counter strike. Did you try disabling your sound? Disable ALSA and enable OSS. See if that works.

---

