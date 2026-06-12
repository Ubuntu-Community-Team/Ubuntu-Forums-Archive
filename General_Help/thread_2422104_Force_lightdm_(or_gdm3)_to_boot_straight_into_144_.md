---
title: "Force lightdm (or gdm3) to boot straight into 144 Hz mode"
date: 2019-07-02
forum: General Help
---

### Post by HeroOfTime on 2019-07-02
Hey. So, I have a 144 Hz monitor. I can change the refresh rate in Ubuntu to 144 Hz, of course. Problem is, the display manager (the login screen) insists in rendering at 60 Hz. First of all, this causes my monitor to black out for a while after logging in because it's changing refresh rates, which is annoying. But more importantly than that, I've read online that some programs, such as Chromium / Chrome and any electron apps, are locked to 60 FPS not because they aren't capable of rendering at different refresh rates, but because they only read the first refresh rate at which xorg started at, instead of the current refresh rate. Since lightdm made xorg start in 60 Hz mode, Chrome is forever stuck in 60 Hz mode for that session. Meaning that if I am able to make lightdm and xorg boot STRAIGHT to 144 Hz without starting in 60 Hz mode first, I *should* be able to get Chrome and Discord to refresh at 144 FPS. Currently Chrome is locked to 60 FPS in both Ubuntu Budgie and regular Ubuntu (tested by going to testufo.com and, well, because I can tell that the scrolling is not 144 FPS) 

I've read some old tutorials around about how to create a startup script for lightdm, but no dice. Can anyone help me out? 

All I want is to get lightdm and xorg to start directly in 144 Hz mode and never enter the 60 Hz mode at any point. My monitor is an AOC G2590PX with FreeSync and my GPU is a Nvidia GTX1070 with the proprietary drivers if that matters.

Thanks.

---

### Post by HeroOfTime on 2019-07-03
Anyone? :(

---

### Post by Claus7 on 2019-07-03
Hello,

I do not know if you came across this one:
[https://askubuntu.com/questions/73804/wrong-login-screen-resolution](https://askubuntu.com/questions/73804/wrong-login-screen-resolution)

maybe providing more information such as the steps you followed, you probably will be able to get better responses. My advice is to stick with lightdm at the time being since it has more documentation as being relatively older.

Regards!

---

