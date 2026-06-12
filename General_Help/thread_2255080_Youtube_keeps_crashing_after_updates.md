---
title: "Youtube keeps crashing after updates"
date: 2014-12-02
forum: General Help
---

### Post by funked up on 2014-12-02
A few weeks ago after some usual update youtube started crashing almost on every video on both chromium and firefox. Sometimes it does it after the video has finished and sometimes sooner. And sometimes it crashes when I try to replay the video. This is happening on a desktop I have that has ubuntu 14.04 32-bit installed. This desktop has also mint 17 Qiana installed and the same issue appears.

I also have a laptop with ubuntu 14.04 64-bit installed and it started to have a similar problem exactly the same period. On the laptop it's worse cause after playing a youtube video the screen just goes black and there is no response whatever I try to do unless I "hard shut down" the system. You can hear the video that keeps playing but there is a black screen.

I've tried several things I've read so far like clearing the cashe and dissabling add-ons but none of them seems to change anything.
There's no problem with videos on vimeo and I had no problem at all a few weeks ago even if I had multiple tabs open. Although my computers are a bit old I have upgraded them a couple of years ago and I use programms such blender, kdenlive, ardour, gimp, etc with no problem. On my desktop I have a Radeon ATI-5450 and as I mentioned everything else works alright.
There's no problem when watching youtube videos on facebook unless I open a new window in youtube.

The thing is that I'm a musician and I use youtube on a daily basis. So I'm desperately trying to find a solution cause I don't want to change to some other OS since I use only ubuntu for about 4 years now.

I've found some other related posts but everyone has a slightly different issue and none of them is solved yet.
I don't think that it's a distro problem cause it's happening with mint too. And some other threads I read have a similar problem with ubuntu 14.10.
So I would guess that it's a kernel issue...?!

Thanx in advance.

---

### Post by Yougo on 2014-12-02
Do you have older kernels still installed?

hold down shift at boot and choose an older kernel from the Grub menu, and see if youtube doesn't crash.
could be a graphics related thing. do all of your machines have graphics cards and drivers from the same vendor?

i do vaguely remember having such an issue a few years ago on a laptop i no longer have. the problem went away with a new ubuntu release, and i never learned what or why. :-\

When faced with a hard reset situation, REISUB would be a 'nicer' way to do it. 
see here: [http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/) (or anywhere else a google away ;-) )

---

### Post by funked up on 2014-12-02
Already tried that. The oldest I found under the grub menu was 3.13.0-24 and I had the same issues. But I guess it's the same kernel with the latest I have installed 3.13.0-35 just updated. Or not?
Anyway, this did not solve the problem.

Graphics cards are not the same either.
Desktop: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430]     (although the one I bought sais HD 5450)
Laptop: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

Actually all I can do is wait for a new kernel to see if the problem continues. Otherwise I'll have to try an older Ubuntu version again or swich to some other OS :(

---

### Post by funked up on 2014-12-02
UPDATE: 
After the last updates firefox seems to work fine now on both machines. Chromium still has the same problems on both machines as described in my first post.

---

### Post by Yougo on 2014-12-02
Well, that at least suggests it's a browser problem, specifically in handling certain video formats. i can understand if you have reservations about using chrome, but if you insist on using a Google browser, getting full Chrome might get you better video support. 

maybe someone can confirm the problem with chromium? i myself don't have it installed currently.

sadly browser features like video format support tend to lag behind and can be iffy in linuxland...

---

### Post by funked up on 2014-12-02
Ok, I've downloaded chrome to use it instead of chromium and everything seems to be working fine on both machines. So the problem was/is chromium.
Chromium even crashed when I opened the chrome.com page to download it.

So I guess it is farewell chromium...
It seems odd though that there are not more people affected by this and why this problem also occured with firefox until the last update.

Anyway, thanx for your time. I'm just happy I don't need to change OS!

---

### Post by John_Durgin on 2014-12-06
I'm still having the same problem with Chome, Chromium and even Firefox.  I'm wondiering if it's a Flash problem.  Anyone else getting crashes randomly while playing videos?

---

### Post by funked up on 2014-12-06
Actually Chrome keeps crashing on my laptop which has an Ubuntu 14.04 64bit version installed but Firefox seems ok until now.
On the desktop which has Ubuntu 14.04  32-bit version Chrome works ok.

The latest Opera 26.0 is working ok too.

---

### Post by nordik14 on 2015-01-30
In my case Kubuntu 14.04 is crashing while playing video in Youtube only. I think it's a flash issue. However although I've installed and updated the [COLOR=#000000][FONT=monospace]pepperflashplugin it does not work properly with Youtube. Other browsers like Rekonq is working fine. Does anyone has a solution?
[/FONT][/COLOR]
chrome://version/

[TABLE="width: 550"]
[TR]
[TD="class: label"]Chromium[/TD]
[TD="class: version"]39.0.2171.65 (Build para desarrolladores) Ubuntu 14.04[/TD]
[/TR]
[TR]
[TD="class: label"]Revisión[/TD]
[TD="class: version"]b853bfefba0da840f4574eb3b5c7ad6e9b8573b5[/TD]
[/TR]
[TR]
[TD="class: label"]SO[/TD]
[TD="class: version"]Linux [/TD]
[/TR]
[TR]
[TD="class: label"]Blink[/TD]
[TD="class: version"]537.36 (@185325)[/TD]
[/TR]
[TR]
[TD="class: label"]JavaScript[/TD]
[TD="class: version"]V8 3.29.88.17[/TD]
[/TR]
[TR]
[TD="class: label"]Flash[/TD]
[TD="class: version"]16.0.0.235[/TD]
[/TR]
[TR]
[TD="class: label"]User agent[/TD]
[TD="class: version"]Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Ubuntu Chromium/39.0.2171.65 Chrome/39.0.2171.65 Safari/537.36[/TD]
[/TR]
[TR]
[TD="class: label"]Línea de comandos[/TD]
[TD="class: version"]/usr/lib/chromium-browser/chromium-browser --ppapi-flash-path=/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so --ppapi-flash-version=16.0.0.235 --enable-pinch --flag-switches-begin --flag-switches-end[/TD]
[/TR]
[TR]
[TD="class: label"]Ruta ejecutable[/TD]
[TD="class: version"]/usr/lib/chromium-browser/chromium-browser[/TD]
[/TR]
[TR]
[TD="class: label"]Ruta del perfil[/TD]
[TD="class: version"]/home/poe/.config/chromium/Default[/TD]
[/TR]
[TR]
[TD="class: label"]Variaciones[/TD]
[TD="class: version"]24dca50e-c4e4c5f
ca65a9fe-91ac3782
5e29d81-f23d1dea
246fb659-92bb99a9
f296190c-e7e0c21f
4442aae2-7158671e
ed1d377-e1cc0f14
75f0f0a0-e1cc0f14
e2b18481-cdc3d902
e7e71889-4ad60575[/TD]
[/TR]
[/TABLE]

---

### Post by intoanother on 2015-05-19
anyone figured this one out??
It's driving me bonkers. 








> **nordik14 said:**
> In my case Kubuntu 14.04 is crashing while playing video in Youtube only. I think it's a flash issue. However although I've installed and updated the [COLOR=#000000][FONT=monospace]pepperflashplugin it does not work properly with Youtube. Other browsers like Rekonq is working fine. Does anyone has a solution?
[/FONT][/COLOR]
chrome://version/

[TABLE="width: 550"]
[TR]
[TD="class: label"]Chromium[/TD]
[TD="class: version"]39.0.2171.65 (Build para desarrolladores) Ubuntu 14.04[/TD]
[/TR]
[TR]
[TD="class: label"]Revisión[/TD]
[TD="class: version"]b853bfefba0da840f4574eb3b5c7ad6e9b8573b5[/TD]
[/TR]
[TR]
[TD="class: label"]SO[/TD]
[TD="class: version"]Linux[/TD]
[/TR]
[TR]
[TD="class: label"]Blink[/TD]
[TD="class: version"]537.36 (@185325)[/TD]
[/TR]
[TR]
[TD="class: label"]JavaScript[/TD]
[TD="class: version"]V8 3.29.88.17[/TD]
[/TR]
[TR]
[TD="class: label"]Flash[/TD]
[TD="class: version"]16.0.0.235[/TD]
[/TR]
[TR]
[TD="class: label"]User agent[/TD]
[TD="class: version"]Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Ubuntu Chromium/39.0.2171.65 Chrome/39.0.2171.65 Safari/537.36[/TD]
[/TR]
[TR]
[TD="class: label"]Línea de comandos[/TD]
[TD="class: version"]/usr/lib/chromium-browser/chromium-browser --ppapi-flash-path=/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so --ppapi-flash-version=16.0.0.235 --enable-pinch --flag-switches-begin --flag-switches-end[/TD]
[/TR]
[TR]
[TD="class: label"]Ruta ejecutable[/TD]
[TD="class: version"]/usr/lib/chromium-browser/chromium-browser[/TD]
[/TR]
[TR]
[TD="class: label"]Ruta del perfil[/TD]
[TD="class: version"]/home/poe/.config/chromium/Default[/TD]
[/TR]
[TR]
[TD="class: label"]Variaciones[/TD]
[TD="class: version"]24dca50e-c4e4c5f
ca65a9fe-91ac3782
5e29d81-f23d1dea
246fb659-92bb99a9
f296190c-e7e0c21f
4442aae2-7158671e
ed1d377-e1cc0f14
75f0f0a0-e1cc0f14
e2b18481-cdc3d902
e7e71889-4ad60575[/TD]
[/TR]
[/TABLE]


---

