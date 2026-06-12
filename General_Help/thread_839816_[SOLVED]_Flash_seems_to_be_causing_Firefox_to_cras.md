---
title: "[SOLVED] Flash seems to be causing Firefox to crash..."
date: 2008-06-24
forum: General Help
---

### Post by diablo75 on 2008-06-24
For about the last 2 weeks or so (I've not kept a very close watch, but that's what it feels like) Flash has been crashing my Firefox about %50 of the time.  Up until a couple days ago or so, restarting Firefox also provided me with the option to restore my previous session, a page that had caused Firefox to crash just a moment ago.  But often times reloading it quickly in this way would not produce a second crash, at least not for quite some time.

What are some general things that can be done to remedy this type of problem?  I kind of have a secondary question that's related to this, because I am curious about the open-source flash player solutions.  I often only use flash for videos, and almost never for anything interactive than perhaps a photo slide show or something like that.  But primarily, youtube and similar sites.  I was wondering if the performance of video playback in any of these alternative players affords you some extra hardware (overlay/video post-processing) features that you can't currently get from the Adobe version of Flash that is currently crashing Firefox sometimes.

Thanks for the help and advice in advanced!

---

### Post by ibuclaw on 2008-06-24
Yeah, I used to have this.

The way I fixed it was by following this howto [here.]("http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html")
Then I pinned hardy and upgraded Firefox and Flash to the Intrepid versions.

I get no more crashes, but not everything is supported in Flash10 yet.
So you may get a few flash games that refuse to load (grey box).
But 99.99% of flash videos play perfect without a crash in sight.

Regards
Iain

---

### Post by Dan_Dranath999 on 2008-06-27
yeah, i have the same problem. Since the last Flash update, my firefox has been crashing with regularity. (and Epiphany too)

---

### Post by diablo75 on 2008-06-27
I wanted to give it a couple days of testing before replying back to this thread in particular, but a while back I actually installed the libflashsupport package because firefox was crashing while Ubuntu was still in Beta (so the problem might have been something else...).  Anyway, since removing libflashsupport, I don't seem to have the crashing problem anymore.  Though better framerates/performance from Flash in general is still to be desired (though it's no big deal).

---

### Post by caro on 2008-06-28
> **diablo75 said:**
> I wanted to give it a couple days of testing before replying back to this thread in particular, but a while back I actually installed the libflashsupport package because firefox was crashing while Ubuntu was still in Beta (so the problem might have been something else...).  Anyway, since removing libflashsupport, I don't seem to have the crashing problem anymore.  Though better framerates/performance from Flash in general is still to be desired (though it's no big deal).

i've been ready to pull my hair out (and i don't have much!) removing libflashsupport seems to have fixed the problem for me.  thanks.

---

### Post by Re1lly on 2008-06-29
same problem here but removing libflash support makes audio in flash videos go away. any clues?

---

