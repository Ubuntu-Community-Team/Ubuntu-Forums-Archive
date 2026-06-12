---
title: "Why are all movie qualities bad?"
date: 2007-08-01
forum: General Help
---

### Post by beemzet on 2007-08-01
Hi, all.

I have been watching about 10 movies but strangely the quality is bad for all movies. I've watched those movies in XP and that was OK.

Should I install any drivers?
When I go to System->Administration->Restricted Drivers Manager, it says " Your hardware does not need any restricted drivers".

Give some advice, guys.

---

### Post by MikeEvans on 2007-08-01
What specifically is bad?  Do you see compression artifacts, is it dark, sound problems?

---

### Post by beemzet on 2007-08-01
The resolution is bad.
I mean, like in youtube or something, you see the video and when you enlarge to fullscreen, the quality worsens.

And also, not only with movies, but with music files also, when I put to max volume it seems like the speakers (or only one speaker, on my laptop) shake and the sound is not good.

---

### Post by MikeEvans on 2007-08-01
I did a little searching and it looks like your problem is either the media player or your graphics card/drivers.  What media player are you using now?  Try Mplayer, VLC, and Totem.  Is the video bad in all of them.  If so what graphics card are you using?  You should make sure your acceleration is working.

---

### Post by Mark Phelps on 2007-08-01
I'm using most of the video players and I've found that SMPlayer produces the highest quality video of them all.

As to the video quality worsening on full-screen, that's to be expected.  The video was created with a single resolution.  Your player can't improve upon that.  For example, if the original video is 320X200, when you enlarge that to full-screen (say 1024x768), it will simply map one original pixel to several pixels.  Unlike what you see in the movies, it will not then be able to break the original pixel down into several new, different, pixels.

Also, the video quality is better with the restricted drivers -- those distributed for Nvidia or ATI cards.  So, if you're using generic drivers, switching to restricted drivers should help.

---

### Post by beemzet on 2007-08-01
> **MikeEvans said:**
> I did a little searching and it looks like your problem is either the media player or your graphics card/drivers.  What media player are you using now?  Try Mplayer, VLC, and Totem.  Is the video bad in all of them.  If so what graphics card are you using?  You should make sure your acceleration is working.

I've tried all media players you counted. Same bad quality.
How do I know if the acceleration is working?

> 
I'm using most of the video players and I've found that SMPlayer produces the highest quality video of them all.

As to the video quality worsening on full-screen, that's to be expected. The video was created with a single resolution. Your player can't improve upon that. For example, if the original video is 320X200, when you enlarge that to full-screen (say 1024x76, it will simply map one original pixel to several pixels. Unlike what you see in the movies, it will not then be able to break the original pixel down into several new, different, pixels.

Also, the video quality is better with the restricted drivers -- those distributed for Nvidia or ATI cards. So, if you're using generic drivers, switching to restricted drivers should help.

The problem is not because of video resolution/size. Same videos under WIndows XP give a decent quality.
I have M2043AP Compaq notebook. Whenever I used to reinstall Windows XP, I went to HP's homepage to download drivers and everything was fine. I suppose there should be something similar with UBUNTU, right? BTW, I think I have an Nvidia card, but I'm not sure.
Also, how do I know if I am using generic or restricted drivers?

Thank you guys so much.

---

### Post by MikeEvans on 2007-08-02
To straighten out your video card / Driver issue first you need to know for sure what video card you have. For that you can look in device manager (system -> preferences -> hardware information) or run the command lshw.  If you do have a Nvidia card (or an ATI) I suggest you try Envy, which will install the proper restricted driver and set everything up.

[Get Envy Here]("http://albertomilone.com/nvidia_scripts1.html")

Or you can do it manually,  here is a guide. [http://doc.gwos.org/index.php/Latest_nvidia_feisty]("http://doc.gwos.org/index.php/Latest_nvidia_feisty")

Be warned that its not hard to break your X configuration when messing with video drivers.  If it breaks you'll have to fix it from the command prompt in recovery mode.  The best thing to do is have a backup your xorg.conf file.  Run the following commands from a terminal to get a backup:

```
cd /etc/X11/
cp xorg.conf xorg.config.backup
```

Now if your forced into recovery mode log on and do:

```
cd /etc/X11/
rm xorg.conf
cp xorg.conf.backup xorg.conf
```

Now reboot and you should be ok.  If not you'll have to reconfigure your X server

```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by beemzet on 2007-08-04
thank you

---

### Post by pietshah on 2007-10-28
I have the very same problem.

All players give me the same result (low quality - pixels) for movies offering good quality when read on XP.

I couldn't succeed to know about what is my graphic card.


Got that with lshw
--------------------------
*-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:e0100c00-e010
-------------------------

Should I install a driver?

Or would it simply be a codec problem?

greetings from Caracas :)
Pierre

---

### Post by Greekman on 2007-11-16
I have EXACTELY the same problem
PLEASE HELP ME!

got Ubuntu 7.10 32bit, ATI X1600, newest fglrx-driver with Envy

when i start the movie with OPENGLoption@VLC it seems from the videoquality good but a lot of frames are skipt !

---

