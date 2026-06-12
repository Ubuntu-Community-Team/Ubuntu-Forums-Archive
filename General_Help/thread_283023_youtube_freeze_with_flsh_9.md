---
title: "youtube freeze with flsh 9"
date: 2006-10-23
forum: General Help
---

### Post by konst88 on 2006-10-23
Hello.
i installed flash 9, first manually with the howto on the forums, and then i tried with the reposition given.
both ways, the movie freezes after some time. it may be 15 secs, or 4 mins, randomly.
with flash 7, it worked fine, just it wasn't syncorized...
any ideas?
thx.

---

### Post by konst88 on 2006-10-24
bump!

---

### Post by Beggar Su on 2006-10-24
I sometimes have problems if I play something on youtube and do a system task like updating avast or reloading ubuntu update manager while watching...it would stop playing after a few seconds and without sound.

---

### Post by konst88 on 2006-10-24
thx for the reply.
i am not doing system wide things, but still the sound of the movie just got stuck, and the movie too, but i can seek it, but with no sound..

---

### Post by ba5e on 2006-10-25
I have exactly the same problem, running flash 9 on Ubuntu 6.10, however I have an old PC, its a PIII 733 / 384MB RAM so I beleive this could be the problem, as cpu usage lies around 60-100% when watching flash movies. 

I hope someone can look into this, maybe we should write a bug if more people are experiencing this, I have tried on 'Google Video':

[http://video.google.com/videoplay?docid=-1839844097221052410](http://video.google.com/videoplay?docid=-1839844097221052410)

and at 1min43sec I have the same problem, video stutters, then freezes and CPU usage drops to 0%

I beleive that this whole issue could be due to beagle-helper (which I have running) but am unsure where to find the correct info to ascertain this. Are you using beagle?

---

### Post by nrgtek on 2006-10-25
I'm running into the same problem when pulling up pages such as anandtech and engadget. Firefox freezes and then I have to force quit.

---

### Post by konst88 on 2006-10-25
i dont have beagle installed, and my firefox don't freeze, but just the movie itself.
i can still use ff after it.
my computer not so old, and on windows' firefox all works wonderfull.
so we have no clue...

---

### Post by ba5e on 2006-10-26
> **nrgtek said:**
> I'm running into the same problem when pulling up pages such as anandtech and engadget. Firefox freezes and then I have to force quit.


Yes, this is a different issue, firefox does not freeze its just the flash window. I find also that the sound just stops sometimes (I have to close /re open firefox to get it to work again)

---

### Post by IYY on 2006-10-26
I have this issue as well, usually when I am doing something on the system. If I just leave it to play and don't touch it, it tends to work better.

Note that other flash players (Google Video) don't have the problem.

---

### Post by PriceChild on 2006-10-26
> **ba5e said:**
> I have exactly the same problem, running flash 9 on Ubuntu 6.10, however I have an old PC, its a PIII 733 / 384MB RAM so I beleive this could be the problem, as cpu usage lies around 60-100% when watching flash movies.You need an 800Mhz machine to use flash9... according to the sys reqs.

Can't remember how much ram though.

---

### Post by konst88 on 2006-10-26
it happens to me on other flash sites, for example which plays music.
what do you ,mean by "doing something on my system"? i always do something on my system..

---

### Post by PriceChild on 2006-10-26
> **konst88 said:**
> it happens to me on other flash sites, for example which plays music.
what do you ,mean by "doing something on my system"? i always do something on my system..with low specs.. doing anything else could cause the stuttering.

---

### Post by konst88 on 2006-10-26
the problem is not with the specs, cuz on windows all works fine.

---

### Post by beerfan on 2006-10-26
> **konst88 said:**
> the problem is not with the specs, cuz on windows all works fine.

You're right. Hardware specs is not the problem but the fact that flash9 for linux is only in beta is.

---

### Post by konst88 on 2006-10-26
but for most of the people, it works perfectly.

---

### Post by beerfan on 2006-10-26
Yeah, I've heard the same reports. It was crashy for me though.

---

### Post by PriceChild on 2006-10-26
Could you post your system specs?

---

### Post by matrooswolf on 2006-10-26
Same problem here, flash 9 freezes, video loads, but playback freezes, I can manually skip through the video, or it plays without sound, (on Youtube, myspace, ...)

Specs, 1 gig RAM, AMD 3000, Nvidea 5200FX

(installed XGL/Beryl (still on Dapper))

---

### Post by konst88 on 2006-10-26
> **matrooswolf said:**
> Same problem here, flash 9 freezes, video loads, but playback freezes, I can manually skip through the video, or it plays without sound, (on Youtube, myspace, ...)

Specs, 1 gig RAM, AMD 3000, Nvidea 5200FX

(installed XGL/Beryl (still on Dapper))

yes, this is exactly the problem.
the specs are totally not connected here.
i dont gave XGL, so it is also not the problem..
i will try to upgrade to edgy, and hope this will get fixed.
maybe we should report for a bug somewhere?

---

### Post by Spano on 2006-10-26
```
Note that other flash players (Google Video) don't have the problem.
```
I run into this problem only on youtube.
my libflashplayer.so is installed at /usr/lib/flashplugin-nonfree

---

### Post by matrooswolf on 2006-10-26
Hi, 
flash 9 seems to crash when I have amarok on and I get a popup (when the song changes).  I tried it 5-6 times and bingo, flash goes down every time.  

Does that mean something?  Is it popup related?  Sound related?  ... (just speculating ...)

When I change the sound with my keyboard, a popup comes up, and flash freezes again (actually when the popup disappears)

---

### Post by konst88 on 2006-10-27
man, i think you discovered the problem!!
when amarok is closed, alll works wonderfull.
when i open it, and it is on the tray, all is good.
but when i open the window of it, the flash freeze..

---

### Post by matrooswolf on 2006-10-27
Hi, 
it is actually not Amarok, but the popups, wherever they come from, menu's, tooltips, whatever.

When the popup closes, flash 9 freezes.

Can anybody confirm this?

(for the record, I'm using Dapper, Xgl, Beryl 0.1.1)

---

### Post by nu2this on 2006-10-27
Keep in mind every body that the flash9 is still in beta so it's bound to be buggy.

---

### Post by matrooswolf on 2006-10-28
Yes, I know it's beta, and beryl is pre alpha and so, but still:

Does anyone experience the same:

Flash freezes (or looses sound) when a popup appears,
in fact: at the exact moment the popup dissappears
(I can repeat that again and again)

Anybody any ideas what the link between flash and popups could be???

---

### Post by littlemazeton2 on 2006-10-28
I'm always running Amarok so that might the problem...I will look more into it to see if the problem persists if I close Amarok

---

### Post by stoffe on 2006-10-28
This seems to be a bigger problem... pre-Edgy, I've had no problem playing sounds from different sources at the same time, but now using Rhythmbox blocks just about everything, giving the same symptoms with flash as listed above, and also stopping games using ALSA from playing and more. Is it a problem with gstreamer perhaps? Running such a game and then starting gstreamer-properties makes even the test sound be silent for auto, and alsa fails completely.

It seems that somehow, gstreamer or something does not play nicely with other ALSA stuff, but this worked earlier... maybe some mixing has been trashed or something?

Anyways, it's not just Amarok, it seems to be a gstreamer issue.

---

### Post by stoffe on 2006-10-28
I take that back, it seems to be an ALSA mixing issue. Two ALSA applications/libraries doesn't work at the same time anymore, not sure why. I'm not even sure it used to work without manual intervention, but I thought so...? Hasn't Ubuntu fixed that since at least Dapper, so that ALSA mixing is active and working OOTB?

Would be nice to know, otherwise it's bug filing time.

---

### Post by xKid on 2006-11-24
sudo apt-get install alsa-oss

sudo vi /etc/firefox/firefoxrc


FIREFOX_DSP="aoss"


restart firefox... :mrgreen: :rolleyes:

---

### Post by stoffe on 2006-11-24
> **xKid said:**
> sudo apt-get install alsa-oss

sudo vi /etc/firefox/firefoxrc


FIREFOX_DSP="aoss"


restart firefox... :mrgreen: :rolleyes:

That's for 7. Flash 9 uses ALSA... :roll: And the 2nd beta seems to fix many of the issues, just like they said.

---

### Post by fragos on 2006-11-24
Let's not forget Flash 9 is beta.  I've seen the same thing but decided I'd stick with 9 and look forward to the additional releases.  True 7 worked well but the number of unwatchable Flash 9 videos has been increasing.  I'm just happy there will be a Linux Flash 9.

---

### Post by youShotWhoInTheWhatNow on 2006-12-07
When the first flash 9 beta became available I installed manually.  I did not have any problems with freezing at all.  Then after the recent software update (including a update to flash) opera started to freeze when browsing flash sites.  I tried firefox and I get the same result.  As far as I can tell, it happens regardless of what other programs are running.  I just uninstalled flash and the problem is gone.  Was the recent update to flash 9 beta 2 or something?  I don't understand why this problem did not appear when I had the the manually installed version of flash.

---

### Post by fragos on 2006-12-08
I'm using Flash ver 9.0 d55 and haven't upgraded.  is this what you call beta 2.  I got the version number with "about:plugins".  I have no freezing problem with Ubuntu 6.10 and Firefox 2.0.

---

### Post by urosh2 on 2007-06-03
I found this solution on this forum.
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/596006505831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/596006505831)
From XWRed1


1. Open a new FireFox window.
2. Go to Youtube and select to open any random video.
3. Press pause so it doesn't reach the end.
4. Minimize that window.
5. Open a new FireFox window.
6. In the new browser, surf the net, watch videos, do whatever.

---

### Post by FuturePilot on 2007-06-28
Hey I have the same problem. It can happen with any flash content but it seems to happen the most with YouTube:(

---

### Post by ajm2005 on 2007-12-02
This problems appears to have cleared up for me after upgrading from kubuntu 7.04 to 7.10

---

