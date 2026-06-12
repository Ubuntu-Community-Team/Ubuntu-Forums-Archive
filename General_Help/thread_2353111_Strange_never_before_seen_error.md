---
title: "Strange never before seen error"
date: 2017-02-18
forum: General Help
---

### Post by vdashv on 2017-02-18
**[I need urgent advice I just noticed something stranger]**

Hello,

Ubuntu Gnome user here.

Never had any problems before.

Today for the first time had a lot of tabs open on chrome (never been a problem before) and ubuntu crashed and I was pushed into the the "black" text only variant of ubuntu for a few seconds before the desktop resumed again. 

For those few moments, I saw something that looked like this:

"hw fail ret = -62"

Google is clueless about this, does anyone know what the hell is going on?

Thanks, 
vdashv


EDIT:

I ran traceroute on [www.google.com](www.google.com)

The usual response is the starting IP (mine) going to [www.google.com](www.google.com) after a series of hops.

Now I see something like this:

1. 2604:6000:___:___:___:___:___:___                                                                 0.0%     8    5.8   6.7   5.8   9.6   1.3
 2. 2604:6000:ffc0:65::1                                                                                   0.0%     8   13.5  14.4  13.5  17.2   1.0
 3. 2604:6000:0:4:0:2001:0:120a                                                                            0.0%     8   18.6  21.3  18.4  24.4   2.3
 4. 2604:6000:0:4:0:2001:0:596                                                                             0.0%     8   15.6  17.7  15.2  23.6   2.6
 5. 2604:6000:0:4::de             

This happens for facebook and some other sites, what is going on. Not so usual random sites I tested (man.com, yahoo.com) are fine.

What the hell is going on, please help me

---

### Post by Skaperen on 2017-02-19
was chrome in full screen mode at the time of this failure?

---

### Post by vdashv on 2017-02-19
> **Skaperen said:**
> was chrome in full screen mode at the time of this failure?

I think so, does it make a difference? I think I might have been switching out of full screen and back [ F11 ] when everything slowed down came to a stop before crashing.

Also had python running on a terminal, would this cause a difference?

---

