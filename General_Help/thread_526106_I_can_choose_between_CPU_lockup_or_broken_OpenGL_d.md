---
title: "I can choose between CPU lockup or broken OpenGL driver :("
date: 2007-08-15
forum: General Help
---

### Post by wiberg on 2007-08-15
Hi,

on startup I have two options:
[LIST]
[*]load the 2.6.20-15-generic kernel
i can't playback videos. when using vlc and the openGL output module, cpu goes 100% and the picture moves really slow. When using any other output module, the picture gets grainy
[*]load the 2.6.20-16-generic kernel
bootup will work 1 out of 10 times, usually dieing with a soft lockup. video playback works just fine, if bootup succeeds.
[/LIST]

i don't really like either option :) I don't know what to do!

greetings,
wib

---

### Post by heimo on 2007-08-15
Personally, I'd try Gutsy - which is still in Alpha, not ready for everyone - at least from Live-CD and see if it works better (it has newer kernel). Or - and this is rare that I suggest - compile a new kernel. You didn't mention which GPU and Xorg drivers you're using.

---

### Post by wiberg on 2007-08-15
My graphics card is an ATI X1300, which is not very well supported by either fglrx nor xgl nor anything (correct me it that sounded stupid, i have not a clue about linux graphics. i tried to install compiz and failed. it may very well be that i messed something up on my way). i don't know which x.org i have, it's the one that comes with feisty 7.04 updated and upgraded.
I don't really want to switch to gutsy. it's not stable, is it? (well, my feisty isn't exactly stable either, but still)
also, compiling a kernel is not something that i would want to do all by myself, on my only computer...
i rather want to fix that cpu lockup problem, i understand it has something to do with my wlan, which i depend on btw. so i'm gonna look into that.
if anybody has any further suggestions... or if you want some more information, dont hesitate to ask me.
thanks for now,
wib

---

### Post by heimo on 2007-08-15
> **wiberg said:**
> I don't really want to switch to gutsy. it's not stable, is it?

It's in alpha, some things are broken. After two months it'll be released, and I think it'll be quite good after September 27th (beta release). You could try it as a Live CD to see if it'll solve your current problems, and if not, you still have time to file bug reports.

---

