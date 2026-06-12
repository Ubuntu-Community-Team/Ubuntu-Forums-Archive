---
title: "Flash Player crashing constantly in Xubuntu 12.04"
date: 2013-09-04
forum: General Help
---

### Post by RallyDarkstrike on 2013-09-04
Hi all,

I post here as I am at a loss as to what to do now. I'm trying to run Xubuntu 12.04 on an older desktop (AMD AthlonXP 1.8ghz, 256mb Radeon All-In-Wonder video card, 1.5gbs RAM) and all is running smoothly so far. I was trying to run Linux Mint 15 on it before this but couldn't get Skype to work at all and couldn't find any solutions to THAT problem, so I'm giving Xubuntu a whirl for the first time in awhile...

However....no matter what I do, I cannot seem to get Flash player to work in FireFox (my prefered web browser). Every time I try to load a video on Youtube, the video will pop up for a second and then disappear...the rest of the page will still be there, but where the video WAS will simply be a blank white area. After a few seconds I get error messages telling me that Flash has crashed. I've made sure I'm running the latest version of Firefox, and I've made sure I'm running the latest version of Flash. I've even manually installed Flash in Firefox's plugin directory, still no dice....any workarounds I could try...?

Thanks for any and all suggestions! I won't be using the machine on a regular basis, so I was thinking of installing Linux, getting everything working and then donating it to a needy group or family...hate seeing perfectly fine, functional hardware going to waste if it can still get good use! I know it can't run 1080p, but it would certainly make a good basic e-mail/web browsing/etc. machine! :)

---

### Post by ajgreeny on 2013-09-05
Run command ```
cat /proc/cpuinfo | grep sse2 
```

If there is no output your athlon CPU will not be sse2 capable and you will need to run flash version 11.1

There are some other threads about this so do a search and you should be able to find out more details.

---

### Post by RallyDarkstrike on 2013-09-05
Thanks for the reply ajgreeny!

Just ran that command, I DO get an output, but I don't see "sse2" listed anywhere. There is an "sse" listed under "flags" though...?

---

### Post by RallyDarkstrike on 2013-09-05
I installed an older version of Flash (11.1) to my Firefox directory and all seems ok now, thanks for the suggestion! :)

---

### Post by ajgreeny on 2013-09-05
Great!
It has been a problem with some older AMD cpus for a while now.  Just make sure you have either flashblock or noscript enabled in your browser for security's sake.

---

### Post by RallyDarkstrike on 2013-09-06
Will do! I use Flashblock on all my computers...no point wasting needless CPU/Memory usage! ;)

---

