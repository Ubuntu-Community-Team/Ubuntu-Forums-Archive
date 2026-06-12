---
title: "Ubuntu 13.04 don't start"
date: 2013-09-07
forum: General Help
---

### Post by hugocamato on 2013-09-07
The problem I have is that my computer no longer load ubuntu. On several occasions I happened to be hung up with the purple screen and the system would not start, and I did was reset the computer and went and no problem. But today and not go flat and stays on the home screen of ubuntu. Yesterday i was working normally, appeared the message that had system updates, which installed. I remember saying something xorg installation. Follow work for long time without any problems. But today no longer turn it back started. Grub appears normally, the countdown begins and then it seems the system load with a black screen and lines of text, and then the purple screen with the word Ubuntu and some points that change color until completion , and now. It does not go. I do not mark any error or tell me any messages. It just stays there and only hear the fans.
I searched for hours but no solutions I have found.
The system I have is Ubunt 13.04, with an AMD Phenom, and a ATI Radeon HD 5700.
I hope I explained well and that someone can help me.

---

### Post by ibjsb4 on 2013-09-08
Sounds like a kernel upgrade has borked your video.  Do you still have the old kernel installed?  If you can, try loading it at boot.

[Also may be Radeon 5500 setup.]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Radeon+5500&sa=Search&cof=FORID:9")

---

### Post by hugocamato on 2013-09-08
> **ibjsb4 said:**
> Sounds like a kernel upgrade has borked your video.  Do you still have the old kernel installed?  If you can, try loading it at boot.
[Also may be Radeon 5500 setup.]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Radeon+5500&sa=Search&cof=FORID:9")

I am not an expert user, if you could be so kind to explain in more detail how to check what the kernel and how to fix it if so is the problem. Thank you!

---

### Post by linuxonbute on 2013-09-08
You could also try booting a live distro ( the disc you used to install ubuntu would do). If this works fine then it is something wrong with the software. If it doesn't then it is more likely a hardware problem

---

### Post by hugocamato on 2013-09-08
With the Live CD works perfectly. Also the w7 that I have on a partition, works perfectly.

---

### Post by buzzingrobot on 2013-09-08
Hugo, have a look here: [COLOR=#000000][FONT=Helvetica]https://wiki.ubuntu.com/RecoveryMode[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]

---

### Post by hugocamato on 2013-09-08
I also tried the recoverymode and does not work, just a black screen.

---

### Post by ibjsb4 on 2013-09-09
> **hugocamato said:**
> I am not an expert user, if you could be so kind to explain in more detail how to check what the kernel and how to fix it if so is the problem. Thank you!

At boot, if you either hold down the shift key or click it, you should get a screen that looks something like this.

[ATTACH=CONFIG]246133[/ATTACH]

The newest kernel will be on top.  If you have the option, select the next to newest (next one down, from the top) with your arrow key and then hit enter.

In the example above, that would be 2.6.20-16-generic.

---

