---
title: "Fluxbox config questions &amp; Misc (Opera)"
date: 2005-05-25
forum: General Help
---

### Post by UrbanSlayer on 2005-05-25
Hi,

Im running Fluxbox, and ive got a couple of config questions that I havent been able to find the answers to, plus a few other queries (Opera etc)

Firstly, full screen maximization.  When setting mplayer to be fullscreen, or a terminal window etc, instead of full screening to one screen, it covers all 3 of my screens.  Is this because this version of Fluxbox wasnt compiled with Xinerama support, and if so does that mean i will need to compile my own?  I have tried altering the Full Maximization setting, but this has had no effect.

Secondly, font size for anti-aliasing is quite large, and i havent been able to work out where I change it.  I couldnt see it in the init script or the style file.

Opera - I've set Opera to open .torrent files with btdownloadgui, but when doing this, I get the error - Error: Too many args - run with no args for (something which is blocked by the Pause button).  I have only given opera the actual btdownloadgui command, which works fine in Nautilus/Rox etc to open Torrent files.

Thanks :)

---

### Post by UrbanSlayer on 2005-05-26
Nobody?

I should clarify that when maximising Mplayer, the video only plays on one screen, but the other 2 are blacked out.

---

### Post by Moobert on 2005-05-26
which fluxbox you running ?

i've had no problems with 9.11 to 9.13 using mplayer (compile from source with a default ./configure)... the problem sounds like a bug i had with luminocity, but with konquerer... i can only surgest you launch mplayer with res settings. Maybe try updating to the lastest verson and of course file bug reports. Same goes for opera... do you have the same problem in Firefox ?

---

### Post by UrbanSlayer on 2005-05-26
I am now running Fluxbox 0.9.13 from the Backports repo.  I am also running 1 screen with Xinerama and the other 2 with TwinView.  The middle and right screens are TwinView and the left is Xinerama.

After fiddling with various settings i am now at this point - running cmdline mplayer with the following settings - mplayer -vo xv -screenw 1280 -screenh 1024 -xineramascreen 0 or 1

When running with xineramascreen 1, it appears on my left most screen, and will maximise fine.  It can not however be maximised to any other screen, trying to do so, sends it to the left screen.  With xineramascreen 0, it appears on the middle screen (without blanking out the right screen), but again, can not be maximized elsewhere.
I have attempted to use the same settings with gmplayer, with limited success.  Using the xineramascreen 1 setting, I am able to either maximise the screen to the left monitor fully with no stretching etc and it doesnt blank out any other screen, or i am able to maximise to the middle screen but this blanks out the right screen.
I am using a config file for gmplayer under ~/.mplayer/config and it does appear to read it as i have placed the xineramascreen setting there.  However, it seems to completely ignore the screenw and screenh settings, i have tried them from the cmdline and from the config file, and nothing seems to work, it continues to blank out the right screen.  Is this a bug that should be reported, or do i need to use something else for gmplayer?

On Opera - I have the latest version of Opera, installed via a static .deb from the opera site for Ubuntu.  I am using the same command in Firefox and it works fine from there (I can open the torrent via firefox).

---

