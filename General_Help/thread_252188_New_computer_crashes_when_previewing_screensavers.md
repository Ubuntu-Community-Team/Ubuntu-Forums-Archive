---
title: "New computer crashes when previewing screensavers"
date: 2006-09-06
forum: General Help
---

### Post by frank05 on 2006-09-06
When using the screensaver selection app on my new computer the xserver gets restarted. The screensaver which is selected when this application starts is the "busy spheres" screen saver. If I quickly select another one before busy spheres loads then my xserver will continue to run as normal. I am currently using the "nvidia" driver.

Does anybody know what log files I could check for clues? I've looked at xorg and gdm log files but couldn't find anything.

I'm guessing this means that one or more selected screensavers will crash my xserver, which won't be fun.

Relevant rig specs:
2.13 GHz Core 2 Duo
2 gigs RAM
7600 GT Graphics

---

### Post by DoctorMO on 2006-09-06
If there arn't any log lines in the xorg config and the xserver crashes that speaks to me of a problem with the hardware. I know I've had problems with nvidia 440MX cards which would crash for no reason on both Linux and windows machines. (but those cards are quite old now)

---

### Post by frank05 on 2006-09-07
A little more info now. It seems as though this crash only happens when running the xgl x server. (Crash is reproducable when running busyspheres from the command line)

---

### Post by whein on 2006-09-13
Hmm, I just stumbled across this problem myself last night.  Problem is, now I don't know how to change the screen saver to another option.  Everytime I open up the screen saver selection dialog the computer locks up since it thinks BusySpheres is the last selected option.  It takes out the keyboard instantly and the mouse almost instantly so I don't even have time to click on another option.  My question is: Is there an editable file that says what the selected screensaver is and where is it located on Ubuntu 6.06?  Also, other than Busy Spheres, are any of the other screen savers dangerous?  And lastly is there another way to configure screen savers that has more options like how fast they run, colors, text, etc?  I noticed a lot of them seemed like they should be configurable (things like picture slide shows, etc.) but the built in preference dialog only gives me the options of time till idle, start screen saver when idle, and lock display.

I'm sure there is a simple line or two in a text file that configures these, I just have no clue where to find it!  ](*,) 
-Will

---

### Post by whein on 2006-09-15
Ok, so I was mucking about in gconf-editor for an unrelated problem and I happend to stumble across the entry for the screensaver.  So I switched the key value from busyspheres to atlantis (which I had seen work just fine) and now I can open up the dialog again without crashing!  woot!  Just gotta be careful which ones I preview now.  I never did test whether BusySpheres would actually crash when it ran or if it just didn't like being previewed.  On a side note, for some reason my xserver mysteriously rebooted a minute or two after I closed the gconf-editor and tested opening the screensaver dialog again, but I'm passing that off as a hiccup.
-Will

---

