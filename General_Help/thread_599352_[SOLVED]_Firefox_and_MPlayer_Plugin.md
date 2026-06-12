---
title: "[SOLVED] Firefox and MPlayer Plugin"
date: 2007-11-01
forum: General Help
---

### Post by o_swas on 2007-11-01
Hello,

I'm a new user of both Linux and Kubuntu 7.10.  I'm trying to make the switch from the Winblows world.

I installed Kubuntu 7.10 on my notebook and thanks to Adept, I have pretty much everything I need set up and working.  The last thing I need to do is install a multimedia plugin for Firefox so I can watch Quicktime and MPEG movies right in the browser.

I used Adept to install the mplayerplug-in for mozilla (Firefox).  I restarted Firefox, went to about: plugins, and saw that mplayer was listed to play a whole bunch of media formats.  So far so good.

I then went to [http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html) to test the plugin.  None of the movies would play; the little "square" where the movie was supposed to play appeared to have mplayer loaded, but no movie would play.

So I downloaded a movie to my desktop and tried to play it with the stand-alone mplayer.  This failed, and I tracked the problem down to having to tweak a setting in the gui.conf file.  OK, so now it should work.

I tried the test page again and still no luck.  No errors are being thrown, the player just opens in the window (as it should) but the movies don't play.  

I then found this page ([http://plugindoc.mozdev.org/linux.html#mplayer](http://plugindoc.mozdev.org/linux.html#mplayer)) which describes mplayer an mozilla, and where to put the plugin fiiles.  This page says to put the .so file in the Frefox plugins directory, and the .xpt file in the components directory.  I looked on the file system and noticed that when I installed the mplayerplug-in for mozilla via Adept, it put both the .so and .xpt files into the Firefox plugins directory.  So I moved the .xpt files to the components directory and restarted Firefox.  Still no luck.

So, where I'm at right now is that I can't play multimedia content like Quicktime or MPEG movies in Firefox.  The mplayer plugin appears to load, as a little box with start/stop/pause etc buttons appears, but the movies never play.

This is really distressing to me as this is a big part of my user experience.  I have everything else set up and working, but I really need to get this working on Kubuntu so I can break from Winblows.

One last item:  The movies don't appear to play in Konqueror either, which appears to be configured out of the box to use mplayer as the multimedia plugin.

Can anybody provide some guidance on what might be wrong and what I can do to fix it?

Thank you!!!!!

-Ryan

---

### Post by o_swas on 2007-11-01
Any comments on how I can get mplayer working in Firefox?

If not, is there another Firefox plugin I should be using that does MPEG, Quicktime, AVI, etc?

Thank you!!

---

### Post by o_swas on 2007-11-01
Bump.

---

### Post by markharding557 on 2007-11-01
have you installed all the codecs for mulimedia 
ubuntu-restricted-extras or automatix from [http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by yostral on 2007-11-01
You don't need any other codec with mplayer, except the w32codecs from Medibuntu repository for some Real Media or some wmv.

From your stand-alone mplayer, what's the error message if you can't play the movie ?

---

### Post by o_swas on 2007-11-01
yostral:  That's the funny thing, is that I can play all the movies in the stand-alone mplayer.  I did have a problem with the stand-along player, but I tweaked something in gui.conf or something like that to be "x11" and that fixed it.  

Actually, when I use the stand alone player it plays the movie but pops up message about something, I think about gtk or something, but I just dismiss it as the movie plays.

Any ideas on what I should look for?

Thank you!!!!!

---

### Post by yostral on 2007-11-02
Try to disable IPv6 in firefox config. In the URL box type : about:config
Search IPv6 and disable it. Then try again.

---

### Post by o_swas on 2007-11-02
Problem solved.  I did two things:  I used Adept to uninstall mplayer and the mplayerplug-in for Mozilla, then reinstalled but this time also installed kmplayer (which had a dependency on mplayer).

Second, and I think this is the one that fixed it, when the mplayer plugin appeared in a web page (but wasn't showing anything) I right-clicked on it and went into the "configure" menu.  In the drop-down box asking where to send the video output, I selected x11, and that did it.

Yay!!!

Thank you for your help!!  I will mark this thread as solved.

---

