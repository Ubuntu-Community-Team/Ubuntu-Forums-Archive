---
title: "Understanding HDMI multi-channel audio (home theater)"
date: 2023-04-07
forum: General Help
---

### Post by michael351 on 2023-04-07
I use Ubuntu 22.04 running Plex for home theater. My graphics card is a GeForce Gt-1030 with Nvidia driver 525 installed. The PC is connected to a Marantz AV8801 processor driving a 7.1 speaker setup.

Lately (after upgrading to 22.04 (from 20), I noticed movies coded in DTS, do not play properly and default to a bland multi-channel output. I get sound out of all of the speakers and it is terrible. If I play the same movie from the same server through Roku, it is perfect DTS Neo:X cinema sound. So the Marantz is handshaking with Roku fine, but not the GT-1030?

As I watch the Marantz display panel with Ubuntu running, it will switch back and forth from DTS Neo (ubuntu desktop no programs running) to "multi-channel in 7.1" when I start Plex and load a movie which I know is DTS encoded. The same happens with Netflix or Amazon Prime Video, so I don't think it is something to do with Plex. A driver issue? (I tried loading driver 390, but that didn't work, (blank screen)

When I test the channels, sound comes from each speaker selected using the test signal as expected. 
Any ideas on what to do to debug this? A conflict somewhere? (pulseaudio/Nvidia HDMI audio?)

---

### Post by MAFoElffen on 2023-04-07
This seems to be a problem with the NVidia driver, in not just 525... And not just for Linux. It is happening on Windows NVidia drivers also.

Answer from NVidia support to their own forum members:
> 
SOLUTION: Open nVidia Control Panel. Click "Change Resolution."  Dial it  down a notch (or two).  All supported audio formats should then become  re-activated.

...That all resolution do not support all codecs. To me, that answer is just a work-around to a problem that still exists, but hey, who am I to say.

---

### Post by michael351 on 2023-04-08
> **MAFoElffen said:**
> This seems to be a problem with the NVidia driver, in not just 525... And not just for Linux. It is happening on Windows NVidia drivers also.

Answer from NVidia support to their own forum members:

...That all resolution do not support all codecs. To me, that answer is just a work-around to a problem that still exists, but hey, who am I to say.

This is good to know, What is meant by "...dial it down a notch"?

---

### Post by MAFoElffen on 2023-04-08
*Change the resolution to something lower..*. They were all doing 4K, and had to try some lower in resolution for the codecs to all work again.

That is why I felt that was a work-around, not a fix. That is saying something like, yes, nVidia can display 4K, but not have on working sound codecs at 4K. That if you want sound codecs to work do 1080p. That make sense? I think they really need to fix that.

---

