---
title: "Installing 7.10 on T60p Error"
date: 2007-10-18
forum: General Help
---

### Post by eTronicGaming on 2007-10-18
Installing 7.04 on a T60p took a lot of work to figure out.  I had to add fglrx drivers onto a usb, plug it in, mkdir /media/disk and mount my usb to it, dpkg -i the xorg packages,  and configure the xorg.conf file to change the graphics card from vesa to fglrx, then init.d/gdm restart twice to get it to work.

However, when installing 7.10 on a T60p, I can't get it to work.  I get through the startup (going into the live cd), but when starting xserver, the screen refreshes back and forth from a glitchy desktop to the terminal 10 times before throwing out an error message.  I tried the same method to install fglrx, but to no avail.

Anyone having these problems on a T60p or any other laptop (it's a Lenovo brand thinkpad).  Please help, as this has been bugging me for the past few days (installing both RC and final version).

-Josh

---

### Post by Ediec on 2007-10-18
I got 7.10RC running fine here on my t60p.

From what i understand from your post you're having issues with the live cd starting. you should either check the integrity of the burn, try burning another copy or use the alternate-install iso

also, what gfx card are you running? 

-JC

---

### Post by eTronicGaming on 2007-10-18
Thanks, but it still isn't working.  I even tried upgrading from update-manager, but my computer wouldn't run.

BTW, I have an ATI Radeon graphics card.

---

### Post by Ancheron on 2007-10-18
Same problem here with a T60P. After error screen, startup hangs, so you can't get to a terminal line or anything.

---

### Post by Ediec on 2007-10-18
> **Ancheron said:**
> Same problem here with a T60P. After error screen, startup hangs, so you can't get to a terminal line or anything.

There was a post somewhere on here about that. read it about an hour ago in class but can't seem to find it now.


> Thanks, but it still isn't working. I even tried upgrading from update-manager, but my computer wouldn't run.

I'm sorry. I don't know what to tell ya. You either got a odd hardware quirk or a bad burn


-JC

---

### Post by Ancheron on 2007-10-18
I strongly suspect it has something to do with the FireGL v5250 ATI Radeon graphics card that comes standard on the T60P. Either the restricted drivers can't handle it, or something else is screwed up in the boot procedure. 

Either way, its kind of a big problem. The boot shouldn't just hang because X server can't initialize... it should dump you off at a terminal of some sort. If that's not the procedure in the liveCD these days... I'm not sure.

---

### Post by Ediec on 2007-10-18
I don't think its the restricted drivers (its run flawlessly for me, so much better then from 7.04). It could be the ati chip but i've yet to see an issue with it. I have (earlier today actually) had a kernel dump on boot which required me to do a hard reboot, but forgot what the error was. I'll keep an eye out for it if it happens again.

I really hope we can figure out whats happening here. Gusty is 200% better then feisty was. best of all is the wifi works great (sitting at 87% strength when it was 50% under 7.04)

-JC

---

### Post by Ancheron on 2007-10-18
Posted bug report on launchpad. The problem is, because it happens while in booting from LiveCD, I can't post any dumps of what is going on beyond simple visual indicators (x-server renders, restarts, and tries to render again until error screen.)

It's kind of frustrating. I had 7.04 working on a T60P, but as the OP said, it took a good deal of work. I uninstalled my old 7.04 because it was messed up, and now 7.10 doesn't even let me install. I'm not going to touch a manual install disk... don't have that much time on my hands.

---

### Post by Ediec on 2007-10-18
Oh i know about 7.04. it took me a good 2 days to get it working right.

Have you checked the liveCD on another machine yet? i'd hate for it to just be a bad burn or the iso missing a few bits here and there.

Also, i stll have the RC iso sitting on my mythbox. I know it works fine. so if you want me to set up a torrent of it or something, i'd be game.

-JC

---

### Post by Ancheron on 2007-10-19
It seems that there are few people that are having this problem, so I will re-download an image and burn it today. On launchpad people actually get beyond installation, so it seems likely it is something wrong with my image (if only!).

---

### Post by eTronicGaming on 2007-10-19
I reburned an iso and it didn't work, but the ubuntu site suggests adding Option "LVDSBiosNativeMode" "false" to the xorg.conf driver line for the graphics card.

---

### Post by Ancheron on 2007-10-19
....But you can't change the X conf fom the Live CD boot, though, can you? 

The thing is, safe graphics mode doesn't work either (and that should an absolute fail-safe option). Kind of a problem when you consider that with at least a crappy Vesa driver it should start up, if slowly.

---

### Post by eTronicGaming on 2007-10-19
As I said in a thread earlier:


I followed the instructions on selecting safe graphics mode, pressing F6, and editing it to say nosplash instead of quiet splash. I then change my xorg.conf file to read 'Option "LVDSBiosNative" "false"' under where it says vesa driver. I then save, quit, and run startx.
Everything loads fine (well it starts off really slow, and then barely works), but I can get to the desktop... a very inactive one. From there, the taskbars do not work and are not clickable, there's no wireless/battery/sound icon anymore, and the only thing that highlights when you mouseover is the two desktop icons... but when selecting one or right clicking, the computer/desktop freezes and I can't get anywhere.

---

### Post by Ediec on 2007-10-19
I'm uploading the RC to a storage site right now and i'll post the link once its done. I know it works.

[http://www.box.net/shared/gl5b04e2pl]("http://www.box.net/shared/gl5b04e2pl")

I'm also grabbing the final release to see if it works for me.

- JC

---

### Post by eTronicGaming on 2007-10-19
I got everything to work.  I will be writing up a how-to later on.  The main thing I did, however, was reconfigure xserver.  (i think i did sudo dpkg -i xserver-reconfigure xorg [then hit tab to autocomplete) then it worked fine after going through step-by-step process.  As for resolution problems, if you have fglrx you have to enable restricted drivers and what not.. here's what I did:

1) System->Administration->Software Sources
        - Check the first four boxes.
        - Click close (make sure WebSense is authenticated so you can download
packages once you click close).
2) System->Administration->Restricted Drivers Manager
        - Check the ATI box (it should say disabled).
        - If it gives you an error, do a 'sudo apt-get -f install' or go to
Synaptic and Edit->Fix Broken Dependencies to get this working and try
again.
        - Click close (it should first download packages and ask to reboot).
3) If you haven't already (or it still has wrong resolution after
reboot):
        - Edit xorg.conf and add "1680x1050" under monitor.

---

### Post by Ediec on 2007-10-19
Cool. glad ya got it working

-JC

---

### Post by softtower on 2007-10-21
I am having exactly same issues on T60p with FireGL v5250, except I tried to go to an alternate console with Ctrl+Alt+F2. However, the screen resolution is set to 320x200 (or something like that) so I am unable to edit any config files...

I am trying ot use nosplash option with F6 and "Safe Graphics Mode" but it shows no difference. I'll spend 2 more hours and I'm restoring my 7.04 partition. This is very frustrating... Why whould graphics issues prevent me from using the command line?

---

### Post by kesnei on 2007-10-23
I am having a similar issues as well

---

### Post by nandaiyo on 2007-10-25
I also have a T60p and have been trying to do a FRESH install of Gutsy 7.10.  I also have the problem of the flashing screen and the stretching.

This is how I got it to install. I am still working on how to fully enable the ATI drivers once in Gutsy, but at least this will get you inside.

1. Boot off liveCD
2. Select Install with Safe Graphics option, then press F6
3. In the command line at the end, remove quiet and change splash to nosplash
4. Press enter and start the install.
5. The screen will start flashing and the error message will appear that it will try again in 2 minutes. At this time you have a 2-minute window to enter in everything. If you don't get it all done in time, don't worry, you'll just need to go through the screen flashing+ error message again. 

6. Hit enter a few times (about 10-14) until you can see the prompt on the screen.
7. Enter the following:
> $sudo apt-get update
$sudo apt-get install xorg-driver-fglrx

You'll have to hit Y + enter a few times blindly, because the Y/N prompt is off the screen. Just hit Y+Enter a few times.

> $sudo depmod -a
$sudo aticonfig --initial
$sudo aticonfig --overlay-type=Xv

That's it. You may have to hit enter a bunch of times to make sure you can see that what you typed is correct because it'll be offscreen. Then you wait until the 2 minute timer is up and it starts flashing your screen again. This time, however, it should work.

The annoying thing is the 2-minute timer. And the fact that Ubuntu hates ATI.

---

### Post by nandaiyo on 2007-10-25
When you run Gutsy for the first time it will repeat the flashing and error. Just hit CTRL + ALT + F2 and login to get to a prompt, then repeat the process above. Keep in mind that you may be prompted to enter your password more than once so keep hitting Enter to see what's going on offscreen.

---

