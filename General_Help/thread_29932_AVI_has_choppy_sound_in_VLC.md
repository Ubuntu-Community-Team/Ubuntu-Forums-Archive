---
title: "AVI has choppy sound in VLC"
date: 2005-04-26
forum: General Help
---

### Post by petehall on 2005-04-26
My digital camera produces AVI movie files, but when I play these in VLC the sound is incredibly choppy - it's barely there. The video stream on these files uses the MJPG codec, and the audio stream uses araw. Additional meta-information is Setting: HAS_INDEX

For comparison purposes, it works fine with other AVIs with video codec DIV3 and audio codecs wma2 or mpga, with Setting: HAS_VIDEO_IS_INTERLEAVED.

Presumably the problem is with the araw codec? Is this a common problem?

I am using a bog-standard Hoary on an AMD Athlon 1100+ with 256MB RAM.

---

### Post by DutchLau on 2005-04-26
I have the same problem. VLC is only choppy with a few files, but it's generally good. Try changing the output Audio driver or the output Video driver in the prefrences tab. Otherwise use Mplayer to play those movies  :) 

Cheers

---

### Post by petehall on 2005-04-26
Thanks. I also had to change the Video Codec family to Win32/VfW video codecs to get these particular files to play. And I'm still getting some error message about fonts which I understand is common, so I won't let that worry me too much.

---

### Post by deviant03 on 2005-04-27
I am getting choppy audio to but only if I play .bin files, it skips every 10 second or so.

---

### Post by DutchLau on 2005-04-27
[QUOTE=petehall] I'm still getting some error message about fonts which I understand is common, so I won't let that worry me too much.[/QUOTE]

Hi Pete,

Try this to see if it solves your problem:

Open a terminal and type in

sudo apt-get -t hoary install mplayer-fonts

This *might* solve your problem  :) 

Let us know if it worked :-P 

Greets, DutchLau

---

### Post by petehall on 2005-05-10
Yep, DutchLau, that worked beautifully. Thanks very much.

---

### Post by MsX on 2008-07-19
I was also having this problem, thank you for a working solution DuthLau.

---

