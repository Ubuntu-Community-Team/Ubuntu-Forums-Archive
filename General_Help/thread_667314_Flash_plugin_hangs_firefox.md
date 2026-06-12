---
title: "Flash plugin hangs firefox"
date: 2008-01-14
forum: General Help
---

### Post by Xhosa on 2008-01-14
I'm having an odd problem with the Flash Plugin under Firefox which started a few days ago.

The second or third flash page I visit causes firefox to lock up completely, and has to be killed to recover.  Which web pages or flash things I view seems to be unrelated to the crash.

I'm using Firefox 2.0.0.11 and Flash 9 (tried r48 and r115)

I have so far tried the following without success:

Replace flash plugin (r115) with older one (r48) (removed flashplugin-nonfree, then manually copied in .so files from a known good machine - confirmed version etc in about:plugins).
Reinstall Firefox (apt-get remove --purge, then reinstall)
Run firefox in safe-mode with an empty profile.

Does anyone have any ideas about what might be causing this to happen?

---

### Post by perixx on 2008-01-14
I'm having similar problems with prolonged surfing and other types of videos; perhaps this is a cache- or memory overflow problem...

Maybe either the HDD is running out of space during the process (somewhere in /var), the memory runs low or there's a Firefox-internal 'cache overflow'... 

Have you checked you HDD space, the size of your RAM and swap partition? Perhaps if you use some sort of memory usage tool, you're able to see if the memory is running low while loading new vids (if they're cached in memory).

There's an Addon on Mozdev, called 'PrefBar' - you can use it for instantly access and switch the most important internal Firefox settings, like Java, Javascript, Cookies, Kill Flash... and also clear MemCache / DiskCache - maybe that's of some use here... 

For flash-videos, there's also the option to set the 'flash storage objects' cache (accessible via rightclick on an object or the 'flash settings manager', found on the Adobe homepage).

Hope this helps :)

perixx

---

### Post by NilsE on 2008-01-14
This is a known problem with Flash.  The frequency and trigger are unknown.  Sometimes it will go a long time without freezing and sometime very frequently.

 It is a problem opened with the Flash developers but I have heard nothing on a fix.

---

### Post by Xhosa on 2008-01-14
In my case its 100% reproducible within seconds of opening the browser:

Open firefox
Go to e.g youtube.com
Click on a video
Click on another video

95% of the time thats enough to cause the crash.  In 5% of cases, it'll hold for 3-4 clips before crashing.

Machine doesn't appear to have any memory problems, swap is largely unused, hard drive has tens of GB free etc etc.

If there's any more diagnostic info I can throw in the direction of the official bug report, please let me know, or pass on the bug report URL :)

---

### Post by Crenfinkle on 2008-01-14
fyi this does *not* happen with opera 9.x. It seems to be a mozilla-specific problem.

---

### Post by WhiteOvertoneWind on 2008-01-14
Hello all, same here. same conditions also. :\  Like to see the outcome of this thread. :)  Oh, BTW, this is my first post. Nice place here people. :D

---

### Post by cotcot on 2008-01-14
Only freezes on firefox ?
All nvidia graphics cards ?

I have solved my freezes (not only with firefox) by installing an older nvidia driver (9643).

---

### Post by NilsE on 2008-01-14
I have had it freeze on Opera as well but less than Firefox.  Could be because I like Firefox better I have not used Opera as much.

I have tried different version of the Intel drivers with no luck.

---

### Post by dyrer on 2008-01-14
Any solution?

---

### Post by perixx on 2008-01-15
So it's a well-known bug? I didn't investigate this matter further so far - I'm not watching videos via internet that often.
I guess this should be addressed to the new owners of Flashplayer, Adobe, then...

I was reading about free alternatives like 'libflash' - anyone tried them, if they're having the same problems?

perixx

---

### Post by jlacroix on 2008-01-15
This is well known for me. In my case, and most other cases, it's due to using onboard sound.

To try to fix this problem, I bought an Audigy SE sound card, and it fixed this problem and created many more problems. Then, I bought a Diamond Multimedia 24-bit sound card and this problem is COMPLETELY solved.

I don't know why Adobe Flash has such a problem with onboard sound. Also, this issue will probably never be fixed. As much as I hate to be condescending, we have as much chance of getting this issue fixed as we do NASA's Messenger probe snapping pictures of Dinosaur fossils on Mercury. So, if you have a laptop, try a USB sound card that is known to work in Ubuntu. If you have a desktop PC, buy the aforementioned Diamond Multimedia sound card, or use almost any other sound card other than onboard.

Adobe has been completely ignoring this issue as well. The only way anyone will get their attention is if everyone reports them to the BBB at the same time.

---

### Post by Xhosa on 2008-01-15
A backtrace on the hung firefox results in the following:

```

#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb779e03b in semop () from /lib/tls/i686/cmov/libc.so.6
#2  0xb51aa5a1 in snd_pcm_dmix_open () from /usr/lib/libasound.so.2
#3  0xb51ab287 in _snd_pcm_dmix_open () from /usr/lib/libasound.so.2
#4  0xb5179385 in ?? () from /usr/lib/libasound.so.2

```

Which does seem to point to it being a sound problem.  I vaguely remember configuring something to do with Firefox and ESD/aoss  many moons ago, so I'll see if I can repeat this experiment to check for differences...

---

### Post by jlacroix on 2008-01-15
We've tried that too. The only thing that works is not using onboard sound. Trust me. The best you can hope for with that method is to make it crash slightly less often. 

One *annoying* work around is to load a page with flash, move it to another desktop, and then load another instance of Firefox on your main desktop and it shouldn't crash as long as the other window is still open on another desktop.

Here is the bug report where I've been active and you can see what was already attempted:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/104470](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/104470)

Another one:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688)

Another one:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/102604](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/102604)

(The Ubuntu bug database is full of these).

I heard a rumor that Firefox 3.0 fixes this problem. Can someone confirm?
```
sudo apt-get install firefox-3.0
```

---

### Post by Xhosa on 2008-01-16
I heard a rumor that Firefox 3.0 fixes this problem. Can someone confirm?
```
sudo apt-get install firefox-3.0
```[/QUOTE]

Nope - problem exists in firefox 3 as well, it just takes a few more flash loads for it to lock up than with firefox 2.x

---

### Post by zipperback on 2008-01-16
It is a known bug with flash 9. Adobe knows about it and has done nothing to resolve the issue.

I have an ATI Radeon 1100 video card in my laptop (acer aspire 5050-3371) and it happened to me quite a bit with flash 9 and firefox.

I downloaded and installed Flash 7 and the problem does not happen.

I use flash 7 to watch you tube videos and it works fine for my needs.

Here is a link to download the flash 7 plugin archive from macromedia

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp7_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp7_archive.zip)

- zipperback
:popcorn:

---

### Post by Xhosa on 2008-01-16
OK - not a fix, but a workaround, which seems to be working for me (your mileage may vary)

Open firefox, and go open a  flash website (e.g a clip on youtube).
Pause this clip, then leave this window open and put it off on another desktop and forget about it.
Open a new firefox window and use this for browsing.

I've viewed around 30 clips on youtube at this point and my browser hasn't locked up - previous record was 3...

Having read all the bug reports it does look like this is an Adobe problem - here's hoping they'll fix it at some point in my lifetime...

---

### Post by jlacroix on 2008-01-16
They won't fix it ever.

Has anyone tried Firefox3 yet? Does it fix the issue? I can't test because I'm using a PCI sound card now. (This problem usually only happens with onboard sound, especially Realtek).

---

### Post by Spyros_Gre on 2008-01-16
I have the above problems with Firefox AND Opera.
I have Nvidia GFX card, latest firefox from Synaptic, latest opera from its site, and latest (115) non-free Flash plug-in. It is making flash websites unreachable sometimes, sometimes not.

---

### Post by miscz on 2008-03-07
I have actually more problems with Audigy SE and Flash being unstable than with integrated audio. With Audigy Flash hangs all the time, it's seriously annoying, it can crash even while having one tab playing Youtube. I have taken out my Audigy and enabled onboard Realtek ALC861 and it doesn't crash at all now.

It still has it's moments when I think it's about to crash (CPU usage spike, distorted sound) but it gets to normal in a split of a second.

---

