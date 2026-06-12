---
title: "Stuttering pointer with x11vnc and osx2x"
date: 2007-05-09
forum: General Help
---

### Post by roobarb! on 2007-05-09
Hi all,

Right, I'm having some pointer problems with x11vnc and osx2x (the Mac OS X version of x2x) with Feisty.

My Ubuntu box is hooked up to my Mac via gigabit ethernet on a crossover cable (static IPs, obviously), and I've got x11vnc set up so that display :0 is accessible. Just the one keyboard and mouse, but two monitors. I can connect up and control the screen fairly well with a VNC client (although it is a little 'choppier' than I would have expected), and initially it works perfectly with osx2x - the pointer movement is as smooth as if it were actually connected to the box.

However, after a minute or two, the pointer starts jumping as you move it around the screen. This happens regardless of whether the machine is busy or not, and only occasionally does it go back to being perfectly smooth again. I had exactly the same setup with XP Pro, with TightVNC Server running things on the PC side, and never had these difficulties. Does anyone have any hints as to where things are going wrong?

My initial thought was that too much data was being pushed over the network, so I was wondering if osx2x / x11vnc were sending video data (which is obviously not required with a monitor and x2x / osx2x), but there seems to be very little network traffic. This and my lack of knowledge about exactly how x11vnc works probably means that's a very wrong assumption.

So does anyone have any clues?

TIA,

     Andy.

---

### Post by krunge on 2007-05-09
Are you running x11vnc like this:

```
x11vnc -nofb ...
```

as described here  [http://www.karlrunge.com/x11vnc/#faq-win2vnc]("http://www.karlrunge.com/x11vnc/#faq-win2vnc") ? 

However, can't osx2x go straight to the Linux X server, so you can skip VNC and x11vnc completely?

---

### Post by roobarb! on 2007-05-10
Ooh, thanks for the pointer about x11vnc - I'd scrolled through that web page so many times, but I think my eyes were giving up no me at that point! I'd set the server up using [this HOWTO]("http://ubuntuforums.org/showthread.php?t=363236"), but not tweaked the flags in /etc/xinetd.d/x11vnc much.

Yes - as you say, osx2x should be able to talk to the X server, but I had troubles getting it set up - every time it would just come back with 'connection failed'. I'd used VNC previously with the Windows box, so I had a better idea of how to get that working.

What would be the best way to get it to talk directly to the X server? I tried using:

```
sudo xhost +
```

To allow any host to connect for testing, but using '192.168.0.250:0' in osx2x gave me nothing but the 'connection failed' response. I'm guessing there's a config file I don't know about, or some way to tell the X server that I want it to respond, but I've never tried this before...

Any help would be very much appreciated - but I'll also give the x11vnc -nofb flag a try and post back.

Cheers!

---

### Post by roobarb! on 2007-05-10
Well, I'm posting this from my Ubuntu Feisty box being controlled from my Mac's keyboard and mouse - and it's working perfectly. Not having:

```
x11vnc -nofb ...
```

was definitely the cause of my problems. Now you really can't tell that the mouse isn't physically attached to the machine.

Fantastic - thank you very much for your help, krunge! :)

---

### Post by krunge on 2007-05-10
Good, glad "x11vnc -nofb" is working for you!

WRT osx2x and X11 server, my guess is you will need to use a ssh tunnel (e.g. ssh -X or ssh -Y).  This is because the X server is probably configured to "-nolisten tcp" (check ps output).   I set up a friend to do x2x between two linux boxes using ssh X tunnel.  So xhost + (why sudo??) won't work.

BTW, I use "x11vnc -nofb..." the other way round.  Not too many people know it, but x11vnc works natively on Mac OS X (try it on your mac for fun).  I have a mac next to my Linux box, and often run "x11vnc -nofb" on the Mac and run x2vnc on the Linux box to redirect the linux box keyboard and mouse to the mac.

---

