---
title: "Lubuntu 17.10, Firefox 58, 64-bit unable to watch netflix"
date: 2018-03-13
forum: General Help
---

### Post by cowboyenvy2 on 2018-03-13
So I'm trying to watch Netflix on linux on my Acer Aspire One d255-2256

-Computer-
Processor        : Intel(R) Atom(TM) CPU N450   @ 1.66GHz
Memory        : 1011MB (776MB used)
Machine Type        : Notebook
Operating System        : Ubuntu 17.10 alternative LXQT minimal amd64 
OpenGL Renderer        : Mesa DRI Intel(R) Pineview M x86/MMX/SSE2
X11 Vendor        : The X.Org Foundation
Audio Adapter        : HDA-Intel - HDA Intel



I  can't remember all versions of Ubuntu(debian) Chrome and firefox that  I've tried but I've been unable to get AMD64 Ubuntu to run Netflix

I  currently have Lubuntu-alternative-17.10-i386 LXQT minimal installed  with Firefox 58 on an lvm lv which does work but I would prefer a amd64  version (just seems wrong to run 32 bit operating system on a 64 bit  processor) I have worked with 16.04 to 17.10  and version of firefox  from 52 ESR to firefox 58.

When Running the above configuration  with Firefox 58 Firefox freezes and the only way to return to a working  system is to kill Firefox.
If I remember correctly Firefox 57 or 58 on debian unstable plays choppy.. 

Trying to install nss3:i386 and firefox:i386 onto results in an error from netflix asking if my version of firefox is an official build.

I'm at a loss, any suggestions would be helpful.

---

### Post by monkeybrain20122 on 2018-03-13
Seems that your ram is a bit low.

---

### Post by kerry_s on 2018-03-13
+1
 you should max out that netbook ram, i think its 2gb

you might want to try elementary os as well, it's bare bones. it ran really well on the netbook i had.

---

### Post by hrsetrdr on 2018-03-13
On a desktop I've seen Firefox ask to [enable DRM content]("https://support.mozilla.org/en-US/kb/enable-drm"), once that happened, Netflix would play.

> Processor : Intel(R) Atom(TM) CPU N450 @ 1.66GHz
Memory : 1011MB (776MB used)
Machine Type : Notebook

With the Atom N450 and low RAM installed, negotiating most modern websites I'm sure is difficult, is why I finally retired my Asus 1001px| Debian 9 | XFCE , even-though it's maxed out at 2gb RAM.

---

### Post by kerry_s on 2018-03-13
> **hrsetrdr said:**
> On a desktop I've seen Firefox ask to [enable DRM content]("https://support.mozilla.org/en-US/kb/enable-drm"), once that happened, Netflix would play.



With the Atom N450 and low RAM installed, negotiating most modern websites I'm sure is difficult, is why I finally retired my Asus 1001px| Debian 9 | XFCE , even-though it's maxed out at 2gb RAM.

i loved that hp mini i had, i used it till it completely fell apart, broken hinges, chips & cracks. lol

---

### Post by cowboyenvy2 on 2018-03-13
I'm actually fairly happy with the laptop over all using qupzilla arora palemoon etc as a browser it works really well for light weight look stuff up on the internet type type of things i just miss being able to watch my netflix on my 64 bit os..
It's not the end of the world if I just have to convert go 32 bit, or ultimately go tiny-core to keep this thing alive for browsing web/documents.
I'm just hoping that I can avoid resorting to drastic measures yet.
I'll check in my bios and system docs, I could have sworn at some point I had maxed out ram

---

### Post by hrsetrdr on 2018-03-13
> **kerry_s said:**
> i loved that hp mini i had, i used it till it completely fell apart, broken hinges, chips & cracks. lol

My Asus is in good shape, basically,  the 4 year old  9cell 7200mah battery is still providing 4-6+ hr.s per charge.

  But, it seems most modern commercial websites have such a load of code going on, that an Atom with low RAM( < 4gb) just freezes. 

  I've tried the lighter DEs(xfce,lxde) but really made no difference.    I used [Android-x86]("http://www.android-x86.org/")  for a bit, it would freeze up as well.

---

### Post by hrsetrdr on 2018-03-13
> **cowboyenvy2 said:**
> I'm actually fairly happy with the laptop over all using qupzilla arora palemoon etc as a browser it works really well for light weight look stuff up on the internet type type of things i just miss being able to watch my netflix on my 64 bit os..
It's not the end of the world if I just have to convert go 32 bit, or ultimately go tiny-core to keep this thing alive for browsing web/documents.
I'm just hoping that I can avoid resorting to drastic measures yet.
I'll check in my bios and system docs, I could have sworn at some point I had maxed out ram

Netflix runs on 64 bit Firefox, just need to allow DRM content. Firefox will take care of that, with your permission.   

See this screeny of my Firefox on Netflix: [ https://i.imgur.com/ClcVFBT.png]("https://i.imgur.com/ClcVFBT.png")

---

### Post by kostkon on 2018-03-13
Unfortunately, it's just a pipe dream. You will never manage to make that system, with an Atom 1.6Hz CPU and GMA3150 as graphics card, to play Netflix content properly, there's no way. Maybe you'll get something like 10fps; video will be choppy, that's a definite.

---

### Post by kerry_s on 2018-03-13
as long as you can watch youtube, you can find all those netflix movies. ;)

---

### Post by monkeybrain20122 on 2018-03-13
> **kerry_s said:**
> as long as you can watch youtube, you can find all those netflix movies. ;)

And better use mpv, smtube or vlc to watch Youtube instead of through the browser. These options are less demanding on resources.

---

### Post by kerry_s on 2018-03-13
> **monkeybrain20122 said:**
> And better use mpv, smtube or vlc to watch Youtube instead of through the browser. These options are less demanding on resources.

that's pretty nice, i grabbed the smtube+smplayer , i like that it can be set to try remove ads. i also set to 360mp4, cause the boys a hard core gamers & suck up all the internet.

---

### Post by cowboyenvy2 on 2018-03-14
As per original message, 64bit  lubuntu and 64 bit FF results in firefox freezing,
64 bit lubuntu and 32 bit firefox (DRM enabled) results in "something went wrong, is this an official FF build" type message.

As to ram, it does apprear that I can upgrade to 2 g, and chip is on order but will not be here for a while.

---

### Post by kerry_s on 2018-03-14
try elementary os, you should then have more ram to play with.
[ATTACH=CONFIG]278944[/ATTACH]

---

### Post by mörgæs on 2018-03-17
> **cowboyenvy2 said:**
> just seems wrong to run 32 bit operating system on a 64 bit  processor

One should not let the processor decide which operative system to run. If you are low on memory, that being 1 or 2 GB, then I would recommend 32 bit.

---

