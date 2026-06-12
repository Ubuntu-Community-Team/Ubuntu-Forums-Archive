---
title: "Hi - need help again."
date: 2007-04-15
forum: General Help
---

### Post by yyz on 2007-04-15
My sound was working fine but it stopped working with no reason at all, it was working even when I didn't have Alsa Mixer but then it stopped working so I installed Alsa Mixer but no hope, what can I do now ?


[Thanks to Joseph and everyone else that helped me solve this. I learned a few miny things now :)

---

### Post by yyz on 2007-04-15
Bump>

---

### Post by josephus on 2007-04-15
did you check all the volume sliders (master, pcm, etc) to make sure you haven't accidentally muted something?  and is sound not working for just one program, or have you tested it with a couple of different programs?  Also check in Systems->Preferences->Multimedia Systems Selector and see which output plugin you are using.

---

### Post by yyz on 2007-04-15
> **josephus said:**
> did you check all the volume sliders (master, pcm, etc) to make sure you haven't accidentally muted something?  and is sound not working for just one program, or have you tested it with a couple of different programs?  Also check in Systems->Preferences->Multimedia Systems Selector and see which output plugin you are using.

No they are all unlocked, on my Xubuntu 6.10 Edgy menu I don't have Preferences nor Multimedia Systems Selector option/menu.

Thank you

---

### Post by yyz on 2007-04-15
> **yyz said:**
> No they are all unlocked, on my Xubuntu 6.10 Edgy menu I don't have Preferences nor Multimedia Systems Selector option/menu.

Thank you

Here is a demonstration of the Alsa Mixer audio settings [image]:

[IMG]http://img237.imageshack.us/img237/4366/screenshotgr3.png[/IMG]

I will try re-installing Alsa Mixer, and then recall back to this thread at a glance :KS 

God bless all & peace to unix'ers :) 

.

---

### Post by yyz on 2007-04-15
I'm still having problems with Sound. Isn't there anybody who can guide me on this situation please?

-
...aa :guitar:--

---

### Post by strabes on 2007-04-15
Well from looking at your screenshot "PCM Out" is muted....

Try this: ```
amixer set Master 150 unmute
```

---

### Post by yyz on 2007-04-15
Wow, thank you !

Just how simple things can be;

My stupidity, I didn't know how to use the interface of the Alsa Mixer application.

Hail Strabes :D

---

