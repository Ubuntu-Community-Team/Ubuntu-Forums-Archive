---
title: "GLX plz get off my system."
date: 2007-01-12
forum: General Help
---

### Post by Kossilar on 2007-01-12
Hello.

I'm confused about this GLX thing. My impression was that if I was running the Latest NVIDIA drivers, I didn't need to have GLX, but my freaking computer keeps referencing it automatically in  xorg.conf, despite the fact that I've repeatedly removed it.

I keep having to reinstall my Nvidia drivers and its making me go crazy.

Now I'm trying to hook up a second monitor, and its causing me more problems. It keeps popping up and whenever its running, beryl stops working. Its a nightmare.

I know what GLX is supposed to do, but if I don't need it, why does it keep causing me problems?

---

### Post by Kossilar on 2007-01-12
Okay so I DO need it. Whatever I had read telling me that I didn't need it was obviously inaccurate... or more likely I read it wrong. Anyway, Its a  moot point now.

---

### Post by jem7v on 2007-01-12
Disclaimer: Okay, I might be wrong about everything I say in this post, but I think I'm right.

Nonononono! GLX is part of XOrg, and has been since XOrg 7.0... you can read more about it HERE: [http://en.wikipedia.org/wiki/GLX](http://en.wikipedia.org/wiki/GLX)

That's why you don't have to *install* it - it's a default part of your X server.  I think part of the reason you're having issues doing dual monitor with Beryl is that, um, Beryl is awful at dual monitor support.  If you Google "beryl dual monitor," you'll see what I mean.  I can't be of much help fixing the problem, though, because I used Compiz instead of Beryl (until I got tired of wiggling windows).

What version of Ubuntu are you running - Dapper or Edgy?  And did you take the XGL or the AIGLX route to enable compositing?


(edit: um, I guess I posted just after you. I didn't see your second post until after I wrote this.)

---

### Post by Kossilar on 2007-01-13
Hey thanks for the reply! You're right. I do need it. I didn't realize that I was probably undermining my own efforts by trying to remove it from xorg.conf. 

As for dual monitors... we'll see what happens. Maybe I'll have to wait until more work is done on Beryl. For now, the cube is almost as good. :)

Thanks a lot for taking the time to reply to my post. I appreciate it.

:)

---

### Post by jem7v on 2007-01-13
Yeah. I feel that none of the composite managers for X are very polished yet... They work comfortably under a certain, limited set of conditions, and outside that happy zone they start to get nervous.  They just haven't been under development long enough yet... i.e., Compiz is still floating around version 0.3.6 and Beryl is cruising along at 0.1.4, so obviously both teams of developers feel they have quite a way to go before they have a fully functional program.

With time, these things sort themselves out. Patience! We will have reliably wiggly windows and exploding menus to fill our screens with virtual shrapnel soon enough.

---

### Post by Kossilar on 2007-01-13
Virtual shrapnel...?

Exxcelleent... :mrgreen:

---

