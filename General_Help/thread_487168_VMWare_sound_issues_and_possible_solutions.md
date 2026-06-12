---
title: "VMWare sound issues and possible solutions"
date: 2007-06-28
forum: General Help
---

### Post by sublimation on 2007-06-28
So I've been trying to get VMPlayer to work on my copy of Ubuntu and allow me to run Google Talk on a WinXP Pro guest. So far, runs great, but I get
>  The PCM sound device is not available (dev/dsp: Device or resource busy)
and that's not a great thing, since my main motivation at this time is to use google talk. So after doing some searching, I found a [[COLOR="Red"]linspire.com forum thread[/COLOR]]("http://forum.linspire.com/viewtopic.php?t=422427&") that addresses the problem. 

one possible solution is to [[COLOR="Red"]use VMWare's scripts for ESD or ARTS support[/COLOR]]("http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1611")
However, I don't know which to use, or if Ubuntu runs these services. I'd like some advice concerning this.

The second solution suggested is to run VMWare through
```
audiowrapper --alsa-native /usr/bin/vmware
```
since this was a linspire forum I again wonder how Ubuntu will respond to the audiowrapper call
you can find these solutions in the thread at the 5th and 4th post from the bottom

I'd just go run them if i wasn't stuck without my Ubuntu for the time being.

Thanks for any help anyone can give, and if you've had similar problems to me with VMWare and VMPlayer, maybe we can find a solution together.

---

### Post by dramenard on 2007-07-07
Hi,

I have the same problem in feisty, and it started only after I installed LTSP server. It did not resolve even after removing LTSP...


dramenard

---

