---
title: "YouTube in Firefox"
date: 2006-07-24
forum: General Help
---

### Post by Jessehk on 2006-07-24
No matter what I do, youtube constantly freezes in the middle of playback and I have no sound for any flash content in Firefox.

I have done searching but nothing seems to have worked. Does anyone have any ideas to enable proper flash playback in Firefox?

I know other Ubuntu users have configured it correctly, so I'm assuming there is a common fix.

Thanks in advance. :)

---

### Post by Skia_42 on 2006-07-24
YouTube is probably using flash 9 by now which is not supported in Linux. Check and see if they made an anouncement about switching to flash 9.

---

### Post by Hairy_Palms on 2006-07-24
youtube works fine for me with the default firefox,

---

### Post by kinematic on 2006-07-24
no problems here either....

---

### Post by Jessehk on 2006-07-24
Rather then saying you are not having any problems, why not do something useful like post the flash-related packages you have installed, etc?

Saying it works for you doesn't help me in the slightest.

---

### Post by agurk on 2006-07-24
Works for me, using Shockwave Flash 7.0 r25
(to check, type about:plugins in the address field)

---

### Post by Sef on 2006-07-24
> I have no sound for any flash content in Firefox.

To have flash you work, you need to download alsa-oss.

Ubuntu: Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install alsa-oss

---

### Post by Rashid584 on 2006-07-24
Jessehk, saying it does work IS useful, because it shows that its not a problem with it being flash 8 or flash 9 or whatever. It may not directly help you, but it helps narrow down the possible problems :)

Anyway, it works for me, and all I did was follow the "default" instructions for installing flash when it first came out. 

Shockwave Flash 7.0 r63

-Rashid

---

### Post by Cordate on 2006-07-24
I was having the same troubles, running Dapper, Firefox & Flash 7. I shut down other apps using sound (which was just XMMS), shut down Firefox, opened a terminal and did
```
killall esd
```
to shut down the ESD sound daemon (it doesn't get along well with the Flash plugin, apparently) and then reopened Firefox, went to youtube and watched my little Schoolhouse Rock video with sssoooouuunnnnd! :) Maybe this will work for you!

Oh, and to bring back ESD when you are done, just type esd in your terminal and it will start up again, giving you beepy noises to let you know it's working.

---

### Post by Mtnear on 2006-07-25
I used two or three of the methods described here on the boards including the FIREFOX_DSP=aoss after the alsa-aoss pkg install, but none of those things worked.  

It wasn't until I ran the update to install the latest linux kernel image that everything worked for me.  Now video and sound are perfect in youtube.

---

### Post by Skia_42 on 2006-07-25
I guess I was wrong...:rolleyes:

---

### Post by Mtnear on 2006-07-26
Ummm...okay...this evening I turned my computer on and now there's no sound again from youtube video.  Great.  So much for it "working perfectly".  This has got to be the most annoying problem that I've had with Ubuntu.

_EDIT_:  A quick re-boot and now there are no problems on youtube with video and audio.  So, in summary, I have no clue what this problem is or how it is fixed.  Thanks.

---

### Post by Rashid584 on 2006-07-27
Haha...thats life :p

-Rashid

---

### Post by Jessehk on 2006-07-28
I apologize for getting impatient. I don't like that this is working for so many people and for some incomprehensible reason, not for me.

I have tried killing esd, I installed alsa-oss and set FIREFOX_DSP="aoss" and nothing works. YouTube videos play with no sound for 2 seconds, and then stop. Any attempts to close that tab or firefox results in a freeze.

Any suggestions would be really appreciated. Thanks again.

---

### Post by Rashid584 on 2006-07-29
> **Jessehk said:**
> I apologize for getting impatient. I don't like that this is working for so many people and for some incomprehensible reason, not for me.

I have tried killing esd, I installed alsa-oss and set FIREFOX_DSP="aoss" and nothing works. YouTube videos play with no sound for 2 seconds, and then stop. Any attempts to close that tab or firefox results in a freeze.

Any suggestions would be really appreciated. Thanks again.

OK dude :)

What version of flash do you have installed? You can check with about : plugins (without the spaces)

try apt-get updating then upgrade and see what it gets you.

-Rashid

---

### Post by Jessehk on 2006-07-29
> **Rashid584 said:**
> OK dude :)

What version of flash do you have installed? You can check with about : plugins (without the spaces)

try apt-get updating then upgrade and see what it gets you.

-Rashid

Thanks for the reply. :)

Here is a screenshot of the about:plugins page:
[[IMG]http://img222.imageshack.us/img222/9200/flashproblemsmj3.th.png[/IMG]](http://img222.imageshack.us/my.php?image=flashproblemsmj3.png)

There are no new package updates.

---

### Post by Rashid584 on 2006-07-29
Hmm, thats exactly the same version as me. And mine works.

Have you tried upgrading your kernel image what-sit? Someone in this thread reported that that made it work for them...

-Rashid

---

### Post by Xizorbg on 2006-07-30
Hi All-

Runing Dapper, Flashplayer 7.0 r63, but I have no VIDEO picture at all.  My other plugins work.  And even flash works on other sites EXCEPT youtube.  Any  help or ideas are appreciated. 

-X

---

### Post by [S|G] on 2006-07-31
If it makes you feel a bit more at ease, youtube occasionally freezes firefox on my computer as well. I'm using firefox with aoss (I start firefox by using 'aoss firefox') and it had been working until recently. Sometimes things go really well, some other times it just hangs.

I'm using firefox 1.5.05 with Shockwave Flash 7.0 r25. I noticed it started to hang recently, when youtube added those fancy video links at the end of the movies.

My guess, however, is that flash support for linux is buggy, and not youtube's code. It hangs as well on some other flashes randomly. It also happens when I'm not using it through aoss.

I noticed that it freezes a lot less when there is no audio playing or it isn't on that fancy screen with video links at the end of the movie, so I usually start and pause the video before switching pages.

By the way, does macromedia ever intends to release an update for linux flash?

---

### Post by adamkane on 2006-07-31
For us Flashophobes, does anyone know how to play YouTube .flv file in Ubuntu?

You can download the .flv files via Firefox VideoDownloader rather than playing the videos with the nasty Flash Player.

VLC is supposed to work, but no success for me.

---

### Post by Angellis_ater on 2006-07-31
Ok - this worked for me.

1. Edit the Firefox link (right-clik) and at the "Starter" part, write "aoss firefox %u"
2. Reboot, just to make sure.
3. Go the "killall esd" route
4. Try Firefox

---

