---
title: "aMSN opening"
date: 2007-10-23
forum: General Help
---

### Post by wiem on 2007-10-23
good day,

I just installed gutsy , and then aMSN, first it all workt, until i wanted to use the special grafic effects in ubuntu. The system activated my unsupported nvidia driver, and ever since, every time i open my amsn it opens, but inside i only see a white window, with a banner of aMSN at the bottem, and a blue line of aMSN in the upper left corner.... i can't loging,.... cant't see a thing, exept the two things in a white window.

I wanted to shut down compiz, but i don't know how to do it ( don't have any GL-destop thing in my system list ), at the menu of visual effects i allready shut down the visual effects in ubuntu.

( i installed aMSN 0.97 several times....)

What do i have to do now? 

Plz help me, don't know what to do now.....

Thankx!

---

### Post by NVRO on 2007-10-30
Same problem here... :icon_frown:

---

### Post by gp95ac on 2007-10-31
I havs AMSN probs too, but not like yours, unrelated.

I can help get you out of compiz and back to metacity

save this as an executable text file

#!/bin/sh

# click to start, click to stop

if pidof compiz.real
then
 exec metacity --replace
else
 exec compiz --replace 
fi


Then click and run, great little script for switching back and forth, also works if your in metacity and want compiz back

cant help you with the AMSN probs, i downloaded it for webcam support and im still stuck with that not working (could be the laptop cam im trying to use with my tower, not sure)

Hope this helps,
Cheers

---

### Post by boeing777 on 2007-11-01
same problem here, white window, can't do anything, someone please help us.

---

### Post by Varlooper on 2007-11-01
I was using Fiesty with aMsn just fine.  Once I put Gusty on after a clean install (Upgrade did not finish because of server issues).  I myself have no problems to speak of with 7.10 to speak of, just that aMSN launches and only shows the aMsn window, the banner, and some unfilled in drop down fields, if I try to attempt to find the login option (Just for testing) I get a pop up window from aMSN with no text, just a exclamation point in the dialog box.

I like this application so, being the type to try to resolve it, I un-installed it and reinstalled it incase of errors in the original install.  No dice, still does the same thing.

System CPU :  AMD XP2000
VideoCard:     ATI Radeon 9000 (Atlantis - Saphire) 128mb ram
Ram:               512MB
Disk:               WD EIDE 80Gig with 30gig free

Usage of 3D environment has no relevance to this issue, could duplicate on a totally different machine and completely different hardware.  This issue has to be something in the aMsn build.

---

### Post by NVRO on 2007-11-22
Found the solution! :)
[http://www.amsn-project.net/forums/viewtopic.php?t=4306](http://www.amsn-project.net/forums/viewtopic.php?t=4306)

---

