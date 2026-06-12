---
title: "CounterStrike"
date: 2007-12-09
forum: General Help
---

### Post by syntheticz on 2007-12-09
I have steam running by the use of the trial version of crossover. 
My graphics card is a Nvidia Geforce 7600 GT, I have used Envy to acquire a driver for it.
When I try to run counterstrike source the notice that my driver is out of date pops up, i choose to continue anyway, however I then get this error

"Steamstartup() failed:SteamStartup(0xf,0x0034E064) failed with error 
1: The registry is in use by another process, timeout expired "

I am a complete newbie to linux, I have used windows XP for most of my computer life with the exception of windows 95 back when i was 4 :p  

Is there any way of solving this? Without going into various lines of code which i don't understand because years of microsoft brainwashing has turned me stupid.

thanks 

PS: I am using Linux Mint it is to my knowledge a variation on Ubuntu with no real difference.

---

### Post by syntheticz on 2007-12-09
anything?...

---

### Post by kjbuente on 2007-12-09
Are you sure your using the newest version of it? I know that was a error for some time and I belive that they worked it out in the newest version. I know it works well since I just finished playing CS for about two hours. You may want to check out the forums at code weavers and sometimes they have notes about getting things to work. After this I'll head over myself to see if I can find it again.

Did you search BTW?

Also, are you using Source?

---

### Post by TechnoJunky on 2007-12-10
Here's a quote from the WineHQ site.  

When starting a game Steam throws an error saying The registry was in use by another process.
This seems due to a tendency of the steam client to crash when trying to shut down and release its registry. You can fix this problem by shutting down steam cleanly (keep running and exiting steam itself until you get a clean shutdown without any errors after "Shutting down" - watch the console you ran steam from) and then restarting it. Once steam has been shut down cleanly and restarted the error should not occur.
If all fails, start Steam, right-click on the game and select Properties. Go to Local files tab and click on Verify integrity of game cache...

I don't remember where I saw it, but it said that the video driver being out of date was expected and not to worry about it.  I used to get it too, till I clicked the box saying not to tell me again.

---

### Post by syntheticz on 2007-12-10
Thanks for the help guys, I now have counterstrike source working but now I have 2 problems

1) Theres no sound
2) The writing on server select is all squashed together

Any ways to fix?

I have counterstrike working with crossover linux, not wine i don't think.

---

