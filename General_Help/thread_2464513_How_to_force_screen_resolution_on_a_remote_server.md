---
title: "How to force screen resolution on a remote server"
date: 2021-07-03
forum: General Help
---

### Post by shag00 on 2021-07-03
Kubuntu 21.04
I have remote server which has a screen attached. When I use the local screen I can easily set the resolution to 3840x2160 which is what I want. If I concurrently log into the server remotely I am presented with a viewing screen at the same resolution, again as I want.

If I turn off the screen attached to the server the resolution presented to the remote viewer is reduced to 1920x1080. This in itself is not the main issue, the main issue is that when this change to a lower resolution occurs the ability to input data, keystrokes, mouse clicks etc is significantly badly effected. For example it can take 30 seconds to type in an eight letter password.

If I try to change the resolution remotely Kstart>System Settings>Display & Monitor>Display Configuration I am met with a highlighted message: An output has been removed. Settings have been reloaded. When I click on the resolution drop down box I find that the highest resolution available is 2048x1152 but that displayed resolution is 1920x1080. It appears the reloading of settings is the problem. I suspect this is pulseaudio at work again. I have tried setting the sink and profile used while the monitor is turned on as the default sink and profile in /etc/pulse/default.pa but this does not fix the problem. 
So my question is how do I make the server think it's screen is still connected when it's powered off?

---

### Post by QIII on 2021-07-03
How are you connecting to this server? SSH? RDP? NX?  Etc?

What is the purpose of having a GUI on the server?  Are you sure you need one?

---

### Post by shag00 on 2021-07-04
I am using VNC connect but the same is also true for KRDC. I just find GUI faster and more convenient than terminal though the problem still remains when inputting to a terminal. Having said that, the problem does not centre around which Ubuntu interface I prefer or use it centres around computer programmers thinking they can implement systems that think they know more about what I want than I do and as a result end up creating interfaces that ignore or preclude doing what the user wants. 2 more recent examples, Plex, play a movie and when that movie stops it just starts playing another one without offering the functionality of it just stopping. If you spend 30 minutes chasing this down there is a convoluted method to choose but the way I use Plex it does apply. Second, load up google and download a file, what is does is create an empty an empty file with no content because it thinks there is something wrong with the file - talking about a download from the KDE store here. In this case I have set 3840x2160 as my default resolution in Grub, which is a supported resolution, but that's all to hard, some ******** programmer thinks they can build a better system that gives me what I want and as all to often the case, fail miserably.

I know exactly what I want, I have bought the hardware to support it and I have set the defaults I want but my only choice is to spend time finding ways to un**** their ****ed work. What is the thinking behind a drop box that does not contain many of the resolutions that the graphics card can support and are set as default in Grub? The card does not need a monitor to work.

---

