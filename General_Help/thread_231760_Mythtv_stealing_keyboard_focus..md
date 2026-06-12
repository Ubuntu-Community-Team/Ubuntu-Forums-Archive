---
title: "Mythtv stealing keyboard focus."
date: 2006-08-07
forum: General Help
---

### Post by scarfinger on 2006-08-07
Hi!

I put together a dapper/xgl running on 2 separate monitors. Everything seems fine, I can launch mythtv on the TV in all it`s fullscreen glory (NON XGL).

Here`s my issue, hopefully, someone more knowledgeable in ubuntu can provide a workaround or a fix, didn`t have this issue back in FC4.

When myth is launched on the other display, it steals keyboard focus and I can`t use my kb on my main display as usual, The keyboard is bound to myth on that display.... I`m pretty sure this is a myth issue, but maybe someone can help me redirect focus after the fact.:p 

thx

Scar

---

### Post by miobio on 2007-04-26
Same here! :( 

I have beryl + Xgl as well and I'm experiencing the same problem...

---

### Post by superm1 on 2007-04-27
It all comes down to how you are launching things.

So if your running Xgl, then typically you launch all applications on display :1 since Xgl is launched on :0.

Now in the case of video apps like myth, you want to launch them on display :0 so that they aren't unnecessarily processed by Xgl.  The problem is that you aren't running a window manager on :0.  Every app that is launched will take focus in the order that it is launched.  

I wrote a howto on this a long time ago before beryl split on the old compiz forums.  Its long gone now.  The jist of the howto described how to use either kwin or openbox,backstep,and devilspie to solve the problem.  

Basically, what you need to do is launch kwin on :0, and then configure it to hide all window decorations, and then configure how it handles focus for different things.  

I don't think I can recall the exact steps for either setup, but I can tell you it was a fair amount of work to do.  It was quite the blessing when Nvidia introduced AIGLX/texture_from_pixmap support for me and I didn't have to muck around with this
 stuff anymore !

---

