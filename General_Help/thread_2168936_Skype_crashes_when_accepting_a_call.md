---
title: "Skype crashes when accepting a call"
date: 2013-08-20
forum: General Help
---

### Post by joe15 on 2013-08-20
I was running Ubuntu 13.04 maybe about a month ago. I tried the Skype for Debian 7 multi arch and then also the one for Ubuntu 12.04. Everytime someone would call and I would press the green button Skype would crash completely. Has this been fixed yet? I moved to Manjaro linux because of this and Skype works fine in Manjaro.

---

### Post by thefuryion on 2013-10-24
Im going to post this as a fix to the skype crashing 13.04 issue, It works for me.  FROM what im seeing, on an initial install of Ubuntu, theres some components that are missing, that skype does not provies.  Whats happening is that skype is looking for a "port" for its audio to go into and come out of ,..ie speakers or headset and the mic.  This script that im going to share with  you should fix this for you.  What i have found is that when this script rins, it installs "ASOUNDv2.0" and JACKS,..im assuming that run in a vertual environment that allows skype AND OTHER programs to SHARE AUDIP ports in a vertual environment,...and thusly does ot crash.
I had the smae problem as all of you did,...I went to 13.10,...sorry but that update is buggy,...ill give it a month or so, Im confident that the UBUNTU community will iron out the prolbems  IMO,..but anyway, i ended up going back to 13.04 and i had found that i had lost the jacks port and yes SKYPE was crashing out 13.04 everytime i was turning around.
So the search bagan, finding the simple fix for the problem,..i found it,....

Before yo install this fix,..go look in your skype under the audio settings and see if you have all the audio listings there,...there will be a bunch of them,..IF SO,..Install the script!
After the script does its thing, go back and look in skype audio settings and you will find "PULSEAUDIO SERVER >LOCAL<"   Thats what you want....Your done!

This script will RE_DIRECT your sound to the correct port,...AND SHARE IT with other applications preventing your 13.04 install from crashing out,...Works for me.

Heres the script:    sudo apt-get install libasound2-plugins:i386

Thats it!
This script has been posted in this forum before,...so if you run acrost it in another place,...yea that probably wher ei got it,..Excuse the typos,..and enjoy.
>TDD<

---

### Post by Linuxisfast on 2013-10-25
Skype installed from Software center never crashes here, from 12.04 to the latest 13.10

---

