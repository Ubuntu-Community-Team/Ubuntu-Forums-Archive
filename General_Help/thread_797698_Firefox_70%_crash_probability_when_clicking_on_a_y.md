---
title: "Firefox: 70% crash probability when clicking on a youtube video."
date: 2008-05-17
forum: General Help
---

### Post by SRTS on 2008-05-17
hi, I often browse youtube. With this firefox 3 beta 5 in ubuntu 8 I have around 2/3 probability of crashing the whole browser instantly (it just terminates) when clicking on any youtube link that would open a video. actually clicking pause/play buttons seems harmless though.
i was wondering if it might be related to shockwave flash and/or pulseaudio.

---

### Post by mpgarate on 2008-05-17
I also have this problem. its bad.

---

### Post by SuperNapalm on 2008-05-17
Not with me, works just fine.
Probably a bug in the browser, it is still in beta after all I suppose...

---

### Post by Sleaka J on 2008-05-17
Mozilla just released Firefox 3 RC1 a few hours ago, so hopefully it'll appear in Update Manager and replace Beta 5 soon. That may fix your problem.

---

### Post by dethredic on 2008-05-17
I have this problem too, but my % is more like 20. It happens with all flash objects. I haven't tried RC1, though, I will soon.

---

### Post by adult swim on 2008-05-17
mine has been doing this too, it comes from flash creating a segmentation fault and as far as i know there really isnt anything to do but open firefox again and click restore previous session to try again.

---

### Post by Greg T. on 2008-05-18
It's almost certainly a Flash problem, so upgrading Firefox probably won't do anything to solve it. Hardy uses PulseAudio, which doesn't play well with Flash 9. You can try the beta version of Flash 10, which was released only in the last couple days. It's only a beta, but it fixes the problem. You should see a big improvement. 

[http://ubuntuforums.org/showthread.php?t=795019](http://ubuntuforums.org/showthread.php?t=795019)

---

### Post by mpgarate on 2008-05-18
I successfully upgraded i think. Still had at least one random flash crash though.. but overall I think it did help

---

### Post by thecheat on 2008-05-18
I have about the same crash probability on YouTube videos as well. It sucks.

---

### Post by mpgarate on 2008-05-18
I think it is firefox-related on some level.. no problems here in opera

---

### Post by Promaster91 on 2008-05-18
Same thing happened to me. That is why I went back to Firefox 2. :)

---

### Post by elgr3co on 2008-05-25
I had similar problems, had to downgrade to Firefox2. FF3 would start consuming a lot of CPU, and also when I'd do 
pstree | grep firefox 
I saw that it had started a ld-linux.so process, but I don't know what kind of library it was looking for.
At best FF3 would hang, but once my system shut down, after which I went back to FF2.

---

### Post by executive on 2008-06-11
glad to know im not the only one. mine would crash 50% of the time. im tired of this crap. im downgrading to ff2 asap...

---

### Post by khanis on 2008-06-12
Excellent, I thought I was the only one haha.....
I'll try the Flash 10 beta.. then probably dgrade to FF2 =]

---

### Post by NTolerance on 2008-06-13
> **khanis said:**
> Excellent, I thought I was the only one haha.....
I'll try the Flash 10 beta.. then probably dgrade to FF2 =]

That's what I've done, and I still get crashes.

---

### Post by change_mode on 2008-06-13
I had the same problem with another distribution on different browsers and with the Ubuntu live CD too.
With the live CD it only happened when I had the mp3 and avi codecs installed. Removing them would fix it.

---

### Post by NTolerance on 2008-06-13
> **change_mode said:**
> I had the same problem with another distribution on different browsers and with the Ubuntu live CD too.
With the live CD it only happened when I had the mp3 and avi codecs installed. Removing them would fix it.

Are you referring to mp3 and avi plugins for firefox or just the system-wide codecs (gstreamer) ?

---

### Post by Deadheded on 2008-06-13
Firefox (and flash audio) needs probably libflashsupport. 
"sudo aptitude install libflashsupport" should do the trick. Although for some users libflashsupport apparently causes Firefox to crash.

This solved my problems in FF.  I have no crash...

---

### Post by paulderol on 2008-06-13
are all of these crashes related only to firefox, and not to some plugin of firefox? there is a serious possibility that, due to the variable responses that there is not actually an issue with firefox, but with a particular flash/java/other plugin. has anyone tried youtube without any plugins at all? 

also, could this be video card related? 

my Nvidia desktop card works fine, but sometimes my ATI laptop card has trouble with streaming flash esp. if it is a busy page with lots of things to load, but in neither case does flash crash firefox, it just never loads....

---

### Post by magnus0 on 2008-06-13
> **mpgarate said:**
> I think it is firefox-related on some level.. no problems here in opera

I use Opera too and no problems here too

---

### Post by magnus0 on 2008-06-13
I found a fix for that. I once tried it and I couldn't get it to crash!

[http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html](http://www.ubuntu-unleashed.com/2008/05/howto-fix-firefox-and-epiphany-web.html)

---

### Post by NTolerance on 2008-06-13
> **Deadheded said:**
> Firefox (and flash audio) needs probably libflashsupport. 
"sudo aptitude install libflashsupport" should do the trick. Although for some users libflashsupport apparently causes Firefox to crash.

This solved my problems in FF.  I have no crash...

Now this is interesting.  I followed this howto to help with the regressions in Hardy due to the move to Pulseaudio:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

The howto has a step that removes libflashsupport.  I've re-installed it and I'll see if it helps.

---

### Post by change_mode on 2008-06-14
> **NTolerance said:**
> Are you referring to mp3 and avi plugins for firefox or just the system-wide codecs (gstreamer) ?

The system-wide codecs (gstreamer). The problem is reproducible with the live CD. When I install the codecs, the videos crash. When I remove them, they don't.

On my old Linux system I had the same thing happen with both Firefox and Opera, so I think it's a problem with flash and not with Firefox.

---

### Post by dodle on 2008-07-03
From my post at [http://ubuntuforums.org/showthread.php?p=5315969#post5315969]("http://ubuntuforums.org/showthread.php?p=5315969#post5315969")

>  Re: Firefox 3 Random crashes with Flash
Not sure if this will work; but if you have manually installed any fonts on your system, delete them and delete the ~/.fonts folder.

It's worth a try, eh?

---

