---
title: "Can't see YouTube or Streetview with latest FlashPlayer"
date: 2013-04-21
forum: General Help
---

### Post by 2CV67 on 2013-04-21
For the last year, I have been using outdated Shockwave Flash 11.1 r102 in Firefox, because more recent versions (11.2 r202.243 or .280) don't work for me. 
Typically, with r202 versions, I get blanks instead of Streetview images & YouTube videos, whilst the Adobe Flash Test page does not show the required bouncing cube. 

Chromium seems to use whatever flash player I install in FF and its behavior follows FF.

Recently, I started to get awful red warnings about r102 being "vulnerable" (which I believe, of course) & it is disabled & I have to activate it manually every time I want to use it on the above sites.

So in the last few days, I have tried r202 versions again, but they still don't work. I am currently using Lubuntu 12.10 with FF20.0, but I have the same behavior with the same versions of flashplayer in Ubuntu 10.04 on the same PC.

The r102 version which works (but is vulnerable) was obtained by copy-pasting the libflashplayer.so file from my 10.04LTS back-up system last year. 
I obtained r202.243 & r202.280 versions by temporarily installing Flashplugin-installer via Synaptic, then copy-pasting the libflashplayer.so file from /usr/lib/flashplugin-installer to a "safe" folder, then uninstalling flashplugin-installer, then copy-pasting the .so file to /usr/lib/mozilla/plugins. 
To get r202.243, I had to force the version. 

So now I have 3 different .so files I can copy/paste into ../mozilla plugins as I like. 

I have tried various other methods, like Flash-Aid 2.2.3 (installed but currently disabled) and of course by installing flashplugin-installer normally via Synaptic, & by following Adobe links, but with rubbish results. 

I have a separate netbook with Lubuntu 12.04 & FF 19.0 & libflashplayer 11.2.202.270 which works just fine, so I know it should be possible!

I am happy to try any other (preferably GUI) suggestions & would really like to be able to diagnose this problem somehow. 

Thanks

---

### Post by ajgreeny on 2013-04-21
As far as I'm aware there is nothing you can do but accept the need to activate the flash plugin each time you use it; annoying, but something you may have to accept and live with.  I am assuming that you are probably using a cpu that is not sse2 enabled, as I was until recently, an AMD Sempron 2400+.  You can check that out by running ```
cat /proc/cpuinfo | grep sse2
``` if there is no output, sse2 is not enabled, if it is enabled you will see a line or lines of text starting **flags**.

It may be worth looking in **about:config** in the addressbar of firefox to see if there is any setting that can be edited to alter this safety action, but I have no idea about that, and can not find anything on my new system, though it is now running the latest flashplugin, my old sempron having now died.

---

### Post by jockyburns on 2013-04-21
I too am having big problems watching Youtube video's since an update a few days ago. Ubuntu 12.04.01 and Google Chrome [COLOR=#303942][FONT=Ubuntu]Version 26.0.1410.63. 
Video is jerky and slow and seems to run like it's embedded in superglue.  Even slows the computer down to a speed akin to a snail on diazepam. I do wish someone would fully test updates before releasing them into the wild.  BTW I only update using the update manager, when it tells me updates are available.
 
Quick edit, Youtube video works fine with Firefox, but not with Google Chrome, but I prefer using Chrome, so any ideas please ?? [/FONT][/COLOR]

---

### Post by 2CV67 on 2013-04-21
> **ajgreeny said:**
> ...I am assuming that you are probably using a cpu that is not sse2 enabled...

Thanks for that pertinent information, ajgreeny!

My CPU is an AMD Athlon XP & your code produces no output, so I now know I am not sse2 enabled.

I did doubt & hesitate a bit & went back to check my Windows XP installation on the same PC, where Firefox works OK with a very recent version of Shockwave Flash (11.6.602.180).
Then I did a bit more digging & found many items like this:
[https://bugbase.adobe.com/index.cfm?event=bug&id=3161034](https://bugbase.adobe.com/index.cfm?event=bug&id=3161034)
which confirm your diagnosis!

So the latest news (a year after the problem arose) is that I have to live with my "vulnerable" version?

Are there non-Adobe alternatives? - Gnash?? - LightSpark??

Thanks again for that helpful reply!

---

### Post by 2CV67 on 2013-04-22
Browsing about this problem, I have noticed suggestions that some Google Chrome Flash Players should work with non-sse2 CPU's?

References included Chrome 19 & libgcflashplugin.so & 11.2.202.228.

Links to these seem to be dead now.

From various places, I have downloaded & tried the following versions of flashplayer, with no success:
11.2.202.228
11.2.202.236
11.2.202.243
11.2.202.280

Should I be able to find a "good" version of libgcflashplugin.so anywhere?

Thanks!

---

