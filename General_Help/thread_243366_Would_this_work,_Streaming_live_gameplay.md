---
title: "Would this work, Streaming live gameplay?"
date: 2006-08-24
forum: General Help
---

### Post by UltraSonicSite on 2006-08-24
What I'm thinking about doing is having a screen recorder record me playing Tribes 2. At the same time it is recording, I will be streaming the file through VLC. Basically, as the file is created, the file is played. Would it work? Are there other more effecient ways of doing it? And why does my streaming always stop when I wish to stream a different file on VCL, like a playlist?

---

### Post by peabody on 2006-08-25
I'm pretty sure there's no way to do it, since something like Tribes would be using graphics acceleration which bypasses any way that the software could access the imagry.  If you have a TV out on your video card however, you may be able to clone the display, then output to an analog to firewire bridge (sold seperately), input via firewire and viola, stream that digital stream.

---

### Post by UltraSonicSite on 2006-08-25
Well when I had windows installed I was able to see my computer on my television throught my Radeon 7000 graphics card. Does it mean I can do it in linux?

---

### Post by peabody on 2006-08-25
> **UltraSonicSite said:**
> Well when I had windows installed I was able to see my computer on my television throught my Radeon 7000 graphics card. Does it mean I can do it in linux?

If you get TV-out working ;).  I'm under the impression that requires the fglrx drivers, although if you're playing Tribes I take it you've got it working?

---

### Post by siDDis on 2006-08-26
You mean something like this

rtsp://213.167.99.110/arkiv ?

I do this with using svideo out and svideo in on the same computer. Windows media encoder is exellent for this since it has an option were it can stream smooth without using too much cpu power.

I wish there was a similar alternative to Linux but there isnt. However if you have a dual core cpu you should be fine. 

I do that stream *live* with just a old p4 3ghz cpu. Smooth as silk :)

---

