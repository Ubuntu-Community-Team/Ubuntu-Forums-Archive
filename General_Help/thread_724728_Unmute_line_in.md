---
title: "Unmute line in"
date: 2008-03-14
forum: General Help
---

### Post by guitarist809 on 2008-03-14
Hey everyone,

I've just started using linux, so bear with me here... I'm trying to un mute the line in thats going into my computer. In windows its a simple click the sound icon, change to recording mode, and uncheck mute on the line in part.

In linux I am unable to figure this out. I've got a PodXT connected to my PC via the line in connector (no usb support fiom line6) and I'd like to jam along with some songs, but I can't hear any guitar comming out of my speakers...

I've got the Realtek HD stuff that comes with the 680i mobo. Using ubuntu 7.10.

All help will be greatly appreciated.

Thanks in advance,

Guitarist809

---

### Post by ibuclaw on 2008-03-15
Hi there, and Welcome to Ubuntu!

Line 6 drivers for linux ARE availiable [here to download.]("http://www.tanzband-scream.at/line6/")
But they are somewhat experimental and require compiling source code (I'll be happy to run you through it).

Though personally, I'd wait a year or two for a more complete release (I have a Toneport UX2, but no support yet, else I'd switch 100%).

In the meantime I currently use my ZoomG2.1u with Ardour (Multitrack Editor for Linux) as well as for playing all my flacs/mp3s. And am saving up for a RME HDSP 9632 (Or maybe the 9652...). But enough about my setup.

Enabling Line In is just as easy as Windows!
You should see a Speaker Icon in your top right-hand corner of your screen in the upper panel. (It's right next to the Date and Time)

Right-Click it and Select "Open Volume Control".

The Realtek Device should be the default audio device. Here's my untouched settings.
[[IMG]http://img153.imageshack.us/img153/6964/sisrg6.th.png[/IMG]](http://img153.imageshack.us/my.php?image=sisrg6.png)
My Line In is set to mute by default too.

And unmuting is done by clicking the mute/unmute button
[[IMG]http://img227.imageshack.us/img227/9675/sis2mq3.th.png[/IMG]](http://img227.imageshack.us/my.php?image=sis2mq3.png)

Followed by turning up the volume accordingly.

Oh and noticing your musical background, just for know-how in the future, if you have any M-Audio MIDI interface devices (Uno, 2x2, 4x4 etc), be sure to install the midisport-firmwares in the Ubuntu Repository.
```
 sudo apt-get install midisport-firmware 
```
Then you can plug your MIDI keyboard in too and discover the world of MIDI and Linux!

Hope this helps you out.

Regards
Iain

---

### Post by #Reistlehr- on 2008-04-26
how about from command line? Alsamixer doesnt work.

---

