---
title: "Run Mythtv as different Users"
date: 2006-08-25
forum: General Help
---

### Post by CornMaster on 2006-08-25
I got a new TV tuner, and installed Mythtv but I couldn't run it as my user.  And since I wasn't setting up a standalone PVR, this is an annoyance.

So, in my quest to make MythTV run more like TvTime or a similar application (I failed btw...) I made it able to run in different user accounts.  First I created a Mythtv group, and added my users to that group.  Then I deleted the .mythtv folder it the home folders of all the users (except mythtv of course) and created a sim link to /home/mythtv/.mythtv as .mythtv in all the users directory.  The other users are able to start the back and front ends (Although there are errors, but I'm not sure hov it effects performance.  I'll update this when I test it more.  Haven't had time lately.)

I also had trouble making Mythtv appear on my main monitor when trying to watch live tv.  if would always go to the secondary.  So I have to decrease the resolution to enough to fit my one monitor, and run mythtv in a window.  I would then put the window on the main screen and then watch live tv.  This was the only way I could make it appear on my main screen, and it turns off my second monitor when it goes to watch live tv....which is why I tried to do what I have below:
Check my other post about how to run an IVTV based card in Mplayer (and therefore in a nice small window) because I couldn't find any application to do it.

---

