---
title: "black and white screen before login, cannot log in"
date: 2007-01-29
forum: General Help
---

### Post by kbob on 2007-01-29
I am a newbie and totally lost.

I installed ubuntu version 6.06.1 from a disc that a friend gave to me.  Once installed, i downloaded and installed version 6.10 off the internet.  I wanted to try and install beryl, and was trying to work around my video card which is a sism661fx. While i was trying different things from various posts, i have downloaded something, and my screen will not make it to the log in screen.  

My screen displays what I think is the splash screen....where it says Ubuntu with the bar underneath, and just before log in, the screen goes to a black and white pattern and the mouse icon looks as though it is loading as the black dots inside go round.  It doesn't seem to load anything as i left it running for over 3 hours.

I have tried to select the sis vido card when i entered sudo dpkg-reconfigure xserver-xorg, and this is the screen i get.  I have tried all other video cards in the list, some have the same outcome,and others cause problems with my xserver. I have also tried to roll back to the previous version by using other code from various posts, but apparently i have no previous version.

Please can someone help, i have only been using ubuntu and linux for about 2 weeks.

---

### Post by Brunellus on 2007-01-29
> **kbob said:**
> I am a newbie and totally lost.

I installed ubuntu version 6.06.1 from a disc that a friend gave to me.  Once installed, i downloaded and installed version 6.10 off the internet.  I wanted to try and install beryl, and was trying to work around my video card which is a sism661fx. While i was trying different things from various posts, i have downloaded something, and my screen will not make it to the log in screen.  

My screen displays what I think is the splash screen....where it says Ubuntu with the bar underneath, and just before log in, the screen goes to a black and white pattern and the mouse icon looks as though it is loading as the black dots inside go round.  It doesn't seem to load anything as i left it running for over 3 hours.

I have tried to select the sis vido card when i entered sudo dpkg-reconfigure xserver-xorg, and this is the screen i get.  I have tried all other video cards in the list, some have the same outcome,and others cause problems with my xserver. I have also tried to roll back to the previous version by using other code from various posts, but apparently i have no previous version.

Please can someone help, i have only been using ubuntu and linux for about 2 weeks.
this thread is being moved to the general support section in the hopes that the right eyeballs might catch it.  

For your future reference:  Beryl is alpha software and NOT recommended for new users.  Also, please be more specific as to WHAT instructions you followed.  That will enable us to have at least some idea of where things went wrong.

In the short term, can you use the fallback VESA driver when you reconfigure the xserver using 

sudo dpkg-reconfigure xserver-xorg

?  If yes, then stay with that until you can figure out what else is wrong.

---

### Post by kbob on 2007-01-29
Hi, thank you for replying and putting the thread in the correct area.  I cannot remember where i found the thread, but it required me to go into a terminal and enter some code.  I had to edit some lines of code and take out the # symbol to allow downloads from some sites.  When i reloaded after that, thats when i got the problem.

I have tried the vesa driver, but i got the same screen.  i tried all the video drivers it asks to specify.  some have the same output (the black and white pattern) and others just say there is an error with the xserver.

Am i going to have to reinstall everything all over again?

---

### Post by Brunellus on 2007-01-29
> **kbob said:**
> Hi, thank you for replying and putting the thread in the correct area.  I cannot remember where i found the thread, but it required me to go into a terminal and enter some code.  I had to edit some lines of code and take out the # symbol to allow downloads from some sites.  When i reloaded after that, thats when i got the problem.

I have tried the vesa driver, but i got the same screen.  i tried all the video drivers it asks to specify.  some have the same output (the black and white pattern) and others just say there is an error with the xserver.

Am i going to have to reinstall everything all over again?
if you can't remember what instructions you were following, I'm afraid it's going to be extremely difficult for us to figure out what went wrong.  We're only human after all--we need information to make judgments.

---

