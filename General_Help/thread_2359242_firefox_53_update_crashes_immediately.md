---
title: "firefox 53 update crashes immediately"
date: 2017-04-21
forum: General Help
---

### Post by missmoondog on 2017-04-21
just got the firefox 53 update and can't even get it to start. crashes immediately. get this in error reporter details:


ExceptionHandler::GenerateDump cloned child 2116
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...
cork@cork-desktop:~$ Failed to open curl lib from binary, use libcurl.so instead

Gdk-WARNING **: crashreporter: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0

not sure if this is a firefox issue for sure or not, but that was the only update i had, i believe. i lied, had an ubuntu base thing update also.

i'm on a 32bit, lubuntu 16.04 AMD computer.

any ideas?

thank you

---

### Post by kostkon on 2017-04-22
Latest Firefox requires a SSE2 capable CPU to run (and the [ubuntu changelog for Firefox]("http://changelogs.ubuntu.com/changelogs/pool/main/f/firefox/firefox_53.0+build6-0ubuntu0.16.04.1/changelog") as far as I can see doesn't say anything about the SSE2 compiler flag not being used), so that could be the reason it crashes immediately on your system.

What's the output of:
```
cat /proc/cpuinfo | grep -i sse2
```

---

### Post by missmoondog on 2017-04-22
i thought i had read that some where before the new release came out but didn't think of that last night. i know that computer doesn't support sse2 already. :(

how can i revert back to previous version of firefox then or, what choice of browser do i have for that machine? i have the version of palemoon on it already without support for sse2, which is what i was using  last night to post here.

thank you

---

### Post by vasa1 on 2017-04-22
> **missmoondog said:**
> ...
i'm on a 32bit, lubuntu 16.04 AMD computer.
...
In addition to what kostkon mentioned,> Ended Firefox Linux support for processors older than Pentium 4 and AMD Opteronfrom [https://www.mozilla.org/en-US/firefox/53.0/releasenotes/](https://www.mozilla.org/en-US/firefox/53.0/releasenotes/)

---

### Post by mörgæs on 2017-04-22
> **missmoondog said:**
> 
How can I revert back to previous version of Firefox

Don't. Old browsers have security holes known to the black hats. 

Have you tried Chromium?

---

### Post by vasa1 on 2017-04-22
One could try Firefox 52 ESR which will get security updates: 
[https://www.mozilla.org/en-US/firefox/organizations/](https://www.mozilla.org/en-US/firefox/organizations/)
[https://www.mozilla.org/en-US/firefox/organizations/all/](https://www.mozilla.org/en-US/firefox/organizations/all/)

The drawback is that it isn't in the repos. You'll need to get it direct from Mozilla.

And, although there's a "Team ESR" [at Launchpad]("https://launchpad.net/~team-esr/+archive/ubuntu/firefox-esr"), there doesn't seem to be any ppa to download :(

---

### Post by missmoondog on 2017-04-23
thanks folks :)

---

### Post by Jorhel on 2017-05-08
Hi what did you do to solve it?
I'm on xubuntu 14.04 and Firefox has been crashing on start up since last week, I assume after something got updated.
I'm also on 32bit and AMD Athlon XP on a HP compaq Presario desktop.
I installed chromium and it crashes on launch up too.

---

### Post by mörgæs on 2017-05-08
Xubuntu 14.04 is out of support so better to do a clean install of 16.04.2. 

The Athlon XP does not have SSE2 so it's time to try a selection of other browsers.

---

### Post by pruda on 2017-05-09
I'd avoid chrome even if it worked, but you can find pale moon build without sse2. See [https://forum.palemoon.org/viewtopic.php?f=40&t=13530&start=40](https://forum.palemoon.org/viewtopic.php?f=40&t=13530&start=40)

---

### Post by Jorhel on 2017-05-13
> **mörgæs said:**
> Xubuntu 14.04 is out of support so better to do a clean install of 16.04.2. 

The Athlon XP does not have SSE2 so it's time to try a selection of other browsers.

did that and ran into other problems without sorting this specific one [https://ubuntuforums.org/showthread.php?t=2361007](https://ubuntuforums.org/showthread.php?t=2361007)

---

### Post by missmoondog on 2017-05-14
> **Jorhel said:**
> Hi what did you do to solve it?
I'm on xubuntu 14.04 and Firefox has been crashing on start up since last week, I assume after something got updated.
I'm also on 32bit and AMD Athlon XP on a HP compaq Presario desktop.
I installed chromium and it crashes on launch up too.

i did what pruda suggested and installed palemoon from here, [https://forum.palemoon.org/viewtopic.php?f=40&t=13530](https://forum.palemoon.org/viewtopic.php?f=40&t=13530) which i have installed on all my systems anyway as it's much snappier than firefox anyway. this version is only used on 2 older machines that i have that don't support sse2, obviously.

i only wonder how long it will be before palemoon doesn't work on my processor also though?

---

### Post by hackerb92 on 2017-06-17
It's a bug if upgrading a program makes it crash. I've let Ubuntu know about it by filing a bug here:
[https://bugs.launchpad.net/bugs/1697800]("https://www.google.com/url?q=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F1697800&sa=D&sntz=1&usg=AFQjCNGcBSYy0LqilWjrG6ZxziqQgJfwOA")

By the way, I tested other browsers packaged with Ubuntu 16.04 and all the webkit ones (Chromium, Konqueror, Epiphany) also require SSE2.

It doesn't make sense for a Long Term Support release of Ubuntu to require people to download software from third party sites just to keep their systems working. To that end, I've filed another bug asking the kindly Ubuntu-Mozilla folks to look into recompiling firefox so it doesn't require SSE2: [https://bugs.launchpad.net/bugs/1698501](https://bugs.launchpad.net/bugs/1698501) 

--b

P.S. The current version of Firefox in Ubuntu (54) is a little more  stable than 53, by the way. I'm using it right now to type this message.  However, as soon as you do certain things, like playing mp4 from  youtube, it uses SSE2 and dies. Fortunately, running Firefox's noscript  extension seems to block most of the problematic code from running by  default.

---

### Post by Jorhel on 2017-06-17
Hi,
I have installed palemoon that work for my system but for some reason can't get it in the right place to make it my default browser. I just open it from the run file. But today firefox started working .
By the way I'm not sure wich version of FF I'm running, whatever came with the xubuntu 16.04 install and update. So maybe your bug reports did something Hacker92, well maybe not since your post was only 3h ago....

---

