---
title: "Flash slow on Hardy..."
date: 2008-05-06
forum: General Help
---

### Post by Moonfrost on 2008-05-06
Hey guys, I just installed Hardy Heron and noticed flash is really slow...I mean, I tried watching a video on youtube and the frames per second seem to be slower than what they are on Windows. The Videos display kinda slow and even slower when I turn on fullscreen, I'm using x64 version by the way if that matters. Before, the videos used to run smoothly when on normal screen but slightly slow when in fullscreen but now it's both! I was using 32bit version in case you know if Adobe flash doesn't work well with 64bit Linux or what.

My system specs are 512ram, 200gb Seagate HD, Nvidia 6150LE (integrated graphics) and AMD64 3500+ 2.2 GHZ. Flash videos and such work flawlessly and smoothly on normal or fullscreen on Windows (I'm dual-booting) but not on Linux, I have tried turning off Compiz but there's no difference at all.

---

### Post by foresto on 2008-05-06
One of these bugs on Adobe's site might be the cause:
[https://bugs.adobe.com/jira/browse/FP-7](https://bugs.adobe.com/jira/browse/FP-7)
[https://bugs.adobe.com/jira/browse/FP-83](https://bugs.adobe.com/jira/browse/FP-83)

---

### Post by ihatejoefitz on 2008-05-07
Similar problems here with 82852/855GM Integrated Graphics Device.

---

### Post by jfooobet on 2008-05-07
I'm completely new to Linux, but i read somewhere that Flash is slow in general on Ubuntu because of bad linux support from Adobe. Anyway, turning of hardware acceleration has worked to some extent for some people..

---

### Post by sofamensch on 2008-05-08
Turning Hardw Accel off doesnt change anything. See here:
[http://ubuntuforums.org/showthread.php?t=756239&highlight=flash+fullscreen](http://ubuntuforums.org/showthread.php?t=756239&highlight=flash+fullscreen)

---

### Post by Choad on 2008-05-08
hmmm this is bad. flash has always been a dog in linux, but for me hardy was a dream. flash runs fullscreen fast(er) for me

still tears like a mofo when running at 1920x1200 but if i'm at 1280x800 it will play fine.

c2d 2.0 + geforce 7600 go

---

### Post by wdaniels on 2008-05-08
If you're using the 64bit distribution it has to run through something called nspluginwrapper (because Adobe does not have a 64bit version of flash either for Linux or Windows) which probably has *some* affect on performance though I've no idea how much.

But flash is just really slow on Linux anyway - Adobe only seems to develop it to the minimum extent necessary to claim cross-platform support.  Sometimes it's actually faster using the Windows version on Linux through Wine, but not enough to bother doing that really.

I would suggest you try installing something like the 32bit version of Swiftweasel and see how it runs in that...

---

### Post by Choad on 2008-05-09
> **wdaniels said:**
> If you're using the 64bit distribution it has to run through something called nspluginwrapper (because Adobe does not have a 64bit version of flash either for Linux or Windows) which probably has *some* affect on performance though I've no idea how much.

But flash is just really slow on Linux anyway - Adobe only seems to develop it to the minimum extent necessary to claim cross-platform support.  Sometimes it's actually faster using the Windows version on Linux through Wine, but not enough to bother doing that really.

I would suggest you try installing something like the 32bit version of **Swiftweasel** and see how it runs in that...
i'm sorry but the name has got too abstracted now

firefox - yeah baby! a flaming fox!
swiftfox - well ok, it's not on fire but it's quick!
iceweasel - not as badass as a fox, but having ice powers makes it slightly cool
swiftweasel - it's just a damn weasel now. have you ever seen a slow weasel? not me. the swift part is redundant.

still, even a bog standard weasel could chew it's way through a big "e" so we all know who the real looser is.

...

suddenly i realise why they call osX point releases after big cats. because when computers evolve in to their true form the tigers and panthers will own us all. the penguin is good for is a meat shield, i suppose. microsoft's offerings again leave a lot to be desired.

---

### Post by wdaniels on 2008-05-09
> **Choad said:**
> have you ever seen a slow weasel? not me. the swift part is redundant

:lolflag:

...exactly, so imagine a weasel that's swift even compared to the other weasels!  What can I say, the guy is looking for speed :D

I only mention Swiftweasel because I know you can install the 32bit version from their 64bit repo, and that way saves screwing with the normal firefox install.  But of course, any 32bit firefox variety will do and there are plenty of guides around for all of them.  Personally, I use the standard Ubuntu 64bit FireFox but keep Swiftweasel32 installed also for when flash through npwrapper screws up (as it seems to quite often, albeit less often than it used to).

---

### Post by Moonfrost on 2008-05-10
The problem is...I would love to use an alternative to Adobe's flash and to Sun's Java so I can finally use 100% free software in both senses but unfortunately I tried both alternatives to Flash and the alternative to Java and they both suck...

---

### Post by wdaniels on 2008-05-18
> **Moonfrost said:**
> The problem is...I would love to use an alternative to Adobe's flash and to Sun's Java so I can finally use 100% free software in both senses but unfortunately I tried both alternatives to Flash and the alternative to Java and they both suck...

Same here...none of the FOSS alternatives for flash have worked (even remotely) for me, though I've had some good successes with OpenJDK.

I find Adobe's attitude and products to be very poor in general (not only as related to linux) which is why I prefer to run a browser without Flash even installed 99% of the time, so that my objection is at least reflected in the flash support browser stats for websites that I visit. This has a nice bonus of getting rid of all those annoying flash adverts, and on the odd occasion that I really need to use something in flash, I just open it in SwiftWeasel.

---

### Post by lukeluke on 2008-05-25
I had the same problem with flashplugin-nonfree 9.0.124 and resolved it by using the new Flash beta 10. I followed this [web site instructions]("http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/"). It's probably not as good as the windows version but I find it's much better than the 9.0.124 one.

---

