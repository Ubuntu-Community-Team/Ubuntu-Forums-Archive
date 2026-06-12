---
title: "Compiz with ATI + Hardy: the impossible dream?"
date: 2008-04-28
forum: General Help
---

### Post by jalefkowit on 2008-04-28
So I've been waiting eagerly for the release of Hardy so that I, a Kubuntu user, could finally enjoy the nifty Compiz desktop effects that Ubuntu users have been savoring for many months now.

Imagine my surprise, then, to do the upgrade and discover... nothing. No snazzy effects at all -- even after I go into the Desktop Effects tool and explicitly turn them on.

I do some Googling and discover that the effects won't work unless a package called "xserver-xgl" is installed.  A quick apt-get later, it's installed, I reboot and... lo! Desktop effects.

Except now a whole raft of weird new behaviors has cropped up:

1) When I try to shut the machine down, the dialog that usually has the Shut Down button (along with others to lock session, etc.) now has only one button -- Log Out.

2) If I click that Log Out button, the dialog goes away but the logout process appears to hang.  The system waits indefinitely on an empty screen.

3) Periodically the system will just crash and dump me out to that empty screen.  Only way to recover is to do a hard reboot of the system (hold down power button on case until PC reboots).

So I do a little more Googling to see what the problem is, and find several threads that imply that the problem is xserver-xgl.  Remove that, they say, and the bugs will go away.

And they're right.  Except that without xserver-xgl, there are no desktop effects.  So I'm right back to square one.

I guess the question is: is xserver-xgl just so buggy that I should forget about desktop effects at all?

(For reference, my video card is an ATI Radeon X1950 Pro, and I'm using the fglrx driver.  fglrxinfo confirms that the driver is loaded -- no "Mesa 3D" nonsense. I know that Compiz has historically had issues with ATI hardware, so that may be the cause.)

---

### Post by jalefkowit on 2008-04-28
shameless bump so this doesn't completely fall off the radar...

---

### Post by Cygoku on 2008-04-28
I hear you man, ATI + Compiz = Easy in reality, not "impossible".  Open synaptic and do a search for Envy.  Check and install EnvyNG-QT (since you are on Kubuntu).  When it is installed, launch EnvyNG and choose to install the Nvidia Driver (NOT manually).  it will do it's tuff and configured your xorg.conf file to restrict everything except AIGLX.  

This will work 100% right what ever you've done editing or installing driver before.  

Cygoku

---

### Post by jelofson on 2008-04-28
I have an ATI 9600/9700 radeon mobility in my dell laptop. With 7.10, I was able to get compiz to work with the open source driver, but not with the fglrx driver. After upgrading to Hardy, I use the fglrx driver and can use compiz. I didn't install xserver-xgl. All I had to do, was edit the xorg.conf file and set Composite to "Enable". Now the desktop effects work.

My card is pretty old, so it should work for you.
I think the bundled fglrx is 8.47.3, which is pretty recent.

---

### Post by jalefkowit on 2008-04-28
Thanks, jelofson -- that tweak to xorg.conf appears to have solved the problem!

I owe you a cup of Ubuntu :)

---

### Post by alexsabree on 2008-04-28
Kinda glad I decided to buy an Nvidia GPU instead of crossfiring two ATI cards. :)

---

### Post by jelofson on 2008-04-29
I can always use a free cup of Ubuntu! Just curious, if you have the desktop effects enabled, are you able to view video via mplayer or vlc or movie player? I have to disable my desktop effects to watch video. Not sure why.

---

### Post by urvaksh on 2008-04-29
how do i edit the xorg.file?
thanks

---

### Post by jelofson on 2008-04-29
> **urvaksh said:**
> how do i edit the xorg.file?
thanks

I usually use the terminal and then:

```
sudo nano /etc/X11/xorg.conf
```

You could also try 

```
sudo gedit /etc/X11/xorg.conf
```

be really careful with this file. Don't mess with things that best be left alone :)

---

### Post by leodp on 2008-04-29
> **jelofson said:**
> ...are you able to view video via mplayer or vlc or movie player? I have to disable my desktop effects to watch video. Not sure why.

Hi Jelofson,
a short answer here:
[http://forum.compiz-fusion.org/showthread.php?p=50192](http://forum.compiz-fusion.org/showthread.php?p=50192)
where adamk talks about DRI2.

With mplayer you can use the x11 video output. 
I followed these instructions:

Let’s start gmplayer and go in Option.
Choose the Video “tab” and set x11 driver.
Now close gmplayer, open a term and write
echo "zoom=yes" > $HOME/.mplayer/config
Start gmplayer and watch movie in fullscreen!

from [http://www.arearelax.org/2008/01/15/mplayer-compiz-problems-in-fullscreen/](http://www.arearelax.org/2008/01/15/mplayer-compiz-problems-in-fullscreen/)


If you do want to use xv output (and xvinfo says no adaptors present), check the Section "Device" in xorg.conf, it should have the entry:
	Option	    "TexturedVideo" "on"
together with the following I have:
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
There is some flickering (as explained on the forum.compiz-fusion post), also for openGL applications, except in fullscreen.


Ciao, Leo

---

### Post by jalefkowit on 2008-04-29
Whoops, looks like I spoke too soon :-(

The xorg.conf edit fixed the "all buttons except log out disappear" problem, and the "random lockup" problem (so far). It has not fixed the "system can't shut down cleanly" problem -- it's still getting hung up when I try to shut down and forcing me to go to the power button.

Of course, this could be some other Hardy-related issue and have nothing to do with Compiz, ATI et al...

---

### Post by jalefkowit on 2008-04-29
> Just curious, if you have the desktop effects enabled, are you able to view video via mplayer or vlc or movie player? I have to disable my desktop effects to watch video. Not sure why.

Haven't tried playing video yet -- I'll give it a spin when I get home from work and see how it goes...

---

### Post by Cygoku on 2008-04-29
> **jalefkowit said:**
> Haven't tried playing video yet -- I'll give it a spin when I get home from work and see how it goes...Mplayer and VLC, change the video ouput to X11.

Cygoku

---

### Post by jelofson on 2008-04-29
Thanks for the reply. I have used the gstreamer-properties to use the xwindow system (no xv) but the quality was a little poor.
I will read what you posted and see what happens.

Jon

---

### Post by elustran on 2008-05-08
> **Cygoku said:**
> Mplayer and VLC, change the video ouput to X11.

Cygoku
You don't have problems with pixelation when you render with X11?

---

### Post by Cygoku on 2008-05-08
> **elustran said:**
> You don't have problems with pixelation when you render with X11?A little, but since I don't watch my movies 6 inches from the screen, it's still perfect.

Cygoku

---

