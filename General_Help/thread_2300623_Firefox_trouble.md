---
title: "Firefox trouble"
date: 2015-10-27
forum: General Help
---

### Post by Roosje on 2015-10-27
Since 15.04 i have some trouble with Firefox, out of the blue it freezes my whole system, even locks out my keyboard (mouse still working) as in that no switch to alternative prompt screen is possible, neither does the keycombo for a reset work.
The only solution is a hard reset. 
So no error msg, no escape. This happened the past 6 months 2 times on 15.04, but now i have upgraded to 15.10 and it happens every day, even on a 'safe mode' i have had this happening.
I have removed all add-ons except the Ubuntu one and Ublock, as it happens a lot with gestures (tried 3 different add ons, same results), renamed the file in troubleshooting / Basic, but no change.
So now i am on Chrome, and boy do i not like it :-/ 
Is there a fix? Am i the only one having this problem? 
I am so used to have my system running for years without a hitch i feel quite lost now :-(

---

### Post by v3.xx on 2015-10-27
Could you be running out of ram and going to swap?

---

### Post by Roosje on 2015-10-27
Nope, my system has 4GB, Firefox using around the 350 - 450 Mb with a load of tabs open.
This happens random, just after starting it with no tabs, in the middle of using it for hours with dozens of tabs open. It happens a lot more with any gestures add on active.

---

### Post by v3.xx on 2015-10-27
I do not know what the true problem is, but maybe you should try FF-ESR.

I run it for the stability.

[https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)

---

### Post by Roosje on 2015-10-27
Currently running Chromium to see if it happens again, just to be sure, otherwise, i want it fixed, i can not imagine this is just my system having this problem.

---

### Post by v3.xx on 2015-10-27
Rename your .mozilla folder in your home directory and start FF.  This will create a new one and allow you to restore the old.

Have you tried a reinstall?

Not much, I know, but all I got.  Good luck

---

### Post by vasa1 on 2015-10-27
Trying a new profile would definitely help: you could run **firefox -ProfileManager** in a terminal to get a nice GUI which would let you switch profiles without the need for renaming them.

---

### Post by sammiev on 2015-10-27
Have you tried disabling all your add-ons?

---

### Post by Roosje on 2015-10-27
Is that not the same as safe mode?

---

### Post by Roosje on 2015-10-27
I try that tomorrow, let you know how it goes.

---

### Post by jim_deadlock on 2015-10-28
It could be something in ~/.config rather than ~/.mozilla see here:

[http://ubuntuforums.org/showthread.php?t=2290024](http://ubuntuforums.org/showthread.php?t=2290024)

---

### Post by philinux on 2015-10-28
I think you might find it's the scripts that some websites run.
I have to use noscript to disable scripts on some websites in order to stop firefox from greying out. One example is natwest.com and their login page.
As soon as you put your customer number in and hit enter FF greys out for ages.

---

