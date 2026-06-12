---
title: "ARRGH Stop redetecting/resetting my monitor!"
date: 2013-03-13
forum: General Help
---

### Post by egearbox on 2013-03-13
I just installed Ubuntu 12.04 on a [Zotac Nano AD10]("http://www.zotacusa.com/zbox-nano-ad10.html") .  It's a nice little all-in-one system about the size of a frozen turkey pot pie (5 inches square).   The system doesn't have a VGA port (which I didn't realize before I ordered it).   I installed Ubuntu with the system plugged into my HDMI-capable TV, and it worked fine at 1920x1080.   

However, I wound up with the system plugged into an HDMI-to-VGA converter, plugged into my KVM switch, and then into my Dell 2309 Monitor (max resolution 1920x1080@60Hz).   

The system now "redetects" my monitor and "resets" its resolution to 1920x1080 every three to five seconds!  Every five seconds, I see a beautiful desktop at 1920x1080, then it disappears as the system resets the monitor to ... 1920x1080!

To answer some of the basic questions ahead of time:   Yes, I know that the monitor supports this resolution.  Yes, I know that the system supports this resolution.   Yes, I have tested this hardware (I run all these KVMS and monitors with three other systems, including another Ubuntu box).   Yes, I have tried the proprietary driver that Ubuntu makes available.   

I would like to stop this redetection process and** [COLOR=#ff0000]"FORCE"[/COLOR] **the system to a resolution of 1920x1080 now and forever, regardless of what it's plugged into.   

Can anyone give me some (hopefully simple) steps to do this?   I know my way around Linux as a user but Linux admin is not my forte.

Thanks in advance....

---

### Post by HermanAB on 2013-03-13
Hmm, I really don't know how the detection plug and play process works - probably done by udev and dbus.

However, since I am an engineer, hardware solutions always come to mind:  
The communication with the monitor is over an I2C serial line through the VGA cable pins 12 and 15, so you can cut one of those and then set the monitor resolution manually with xrandr.

---

### Post by egearbox on 2013-03-13
> **HermanAB said:**
>  you can cut one of those and then set the monitor resolution manually with xrandr.

That's an interesting suggestion and I may get to that point.   However, I'm hoping that someone will chime in with a software-only suggestion that I can try (and if necessary, reverse) first.   But thank you, that's definitely a possibility.

---

### Post by egearbox on 2013-03-14
Boy is my face red - it was a bad cable.   Not really "bad" but marginal - just crummy enough so that the marginal video output in the little AD10 nano just couldn't keep powering it.    Switching cables (as I was mucking about doing something else) solved the problem.    Moral of the story:  TAKE NOTHING FOR GRANTED...

Thanks to HermanAB for his response.  :)

---

### Post by nubudedw on 2013-03-20
> **egearbox said:**
> Boy is my face red - it was a bad cable.

 I though I'd chime in here about bad monitor cables, as my problem also ended up being a cable related one.

Symptoms: System Tools > System Settings > Displays. My monitor was shown as UNKNOWN, so consequently the RESOLUTION choices did not fit the higher native resolution of my monitor, and my screen appeared with that lower resolution (not as bad as that constant resetting that @egearbox had).

I researched the Web for a day and a half about this problem, and read all about "xandr" and "xorg.conf". In my research, I noticed that EDID data from the monitor may not be properly passed on due to cable problems - and also that some forum complaints seemed to mysteriously solve themselves after a period, which might point to some hardware factor.

I unplugged and replugged my monitor cable at the PC end - my problem was unchanged, and I was disheartened. After another few hours of research and seeing another problem mysteriously resolve itself on the forums - I tried it again and unplugged and replugged the monitor cable this time at the Monitor end. Bingo! Instead of "unknown", display settings now identified my monitor as "Hewlett Packard 19", and my screen immediately looked good as it should be. (The monitor-end of my cable hangs vertically down, so might have a greater chance of a bad connection due to gravity pulling away over time.)

So if you have resolution or other monitor problems; before making "xandr" or "xorg.conf." changes", it could be your monitor cable, simple as that! (Try both ends, or try a replacement cable - it could save your brain a lot of work!)

---

