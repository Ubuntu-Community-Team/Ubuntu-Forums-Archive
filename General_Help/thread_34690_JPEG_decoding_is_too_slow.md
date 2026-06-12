---
title: "JPEG decoding is too slow"
date: 2005-05-16
forum: General Help
---

### Post by 23meg on 2005-05-16
i have thousands of digital photos on my hd that i took with my digital cameras, and lately i've been looking into various open source image management  and viewing software. i haven't found one that suits my needs yet, but before that i'm having a much more essential problem: while viewing images with any of the software i have installed (namely: eye of gnome, gqview, qiv, gthumb, f-spot), i'm experiencing very slow load times compared to windows, which makes image browsing very uncomfortable and impractical.

the issue probably isn't hard disk transfer speed, since my experiments have revealed that copying/moving  the same bunch of image files both between two physical drives and within the same drive takes 15 to 20% less time in Hoary compared to windows :) but decoding is a whole different matter: while windows decodes my average 3-4mb jpeg file in less than a second, Hoary takes about three seconds. the speed is more or less consistent in all apps i've tried, and this leads me to think that the jpeg decoding library / libraries used by these apps are not performing as fast as those used in windows.

i wonder if others have similar problems... what common libraries are generally used for decoding jpeg? are there alternatives / updates to improve loading time? or do you think the problem lies elsewhere?

---

### Post by notos on 2005-05-16
im not what you can say realy linux literate but you can install

libjpeg o libjpg if you have them then you can try to upgrade to the lastest CVS or lastest stable ...

you can also put us some debung

example

is you run feh (the one i use)

you can do from a terminal something like this

feh [vervose options] &> error.log

then you post them here to see if there is any error ;)

---

### Post by Malakin on 2005-07-26
This is an old problem.

I'm not much of a programmer but I poked around and wasn't able to figure out exactly what was causing it. You can put the images on a ramdrive and it makes no difference, you can edit the jpeg src so that the image it's loading isn't even being decoded, I made it just skip all the decoding loops and it doesn't actually speed it up very much which explains why when I upgrade to a faster CPU jpeg's in linux don't speed up very much, so I wasn't sure what the hell was taking so much time. The next thing I was going to look over was how much of the jpeg was being loaded at a time and try to track down some bottlenecks there but I never got around to it.

Gqview starting with version 2.1 has some fairly fast thumbnail code, it's quite a bit faster then any other Linux app that I've used when it comes to thumbnailing.

---

### Post by 23meg on 2005-09-26
anyone complaining about this in Breezy? i feel it's got significiantly faster, but wonder if it's due to my new computer being faster.

---

### Post by mazor on 2006-04-25
Hello I am new to ubuntu, but I too, that "eye of gnome" is real slow to load up JPG compared to windows XPs image viewer. 

And to complicate things, when u enable the slide show, it works well, then when you finish, eye of gnome will occaionally crash out unexpectly!

I am using Breezy 5.10 by the way.

Lucky for me, after reading this thread I solved my problems both in load speed and in reliability! use "gThumb image viewer"  I have set all my JPGs to load using this app and now JPGs all load in less than a second at times.


hope this helps


Mazor

---

### Post by TitusDalwards on 2006-04-25
i use eye of gnome with my system and i have no complain about this, my Xwindows manager is fluxbox so maybe for this reason eye of gnome works quick.

---

