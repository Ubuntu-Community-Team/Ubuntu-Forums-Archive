---
title: "github.com-linuxmint-hypnotix stuff"
date: 2024-07-27
forum: General Help
---

### Post by jgw on 2024-07-27
I am considering installing hypnotix into my system so I can watch tv.  The majority of the suggestions as to how to do that involve 'Mint' and I use ubuntu 22.04  I am, obvously, confused.  I was wondering if anybody here had thoughts on any of this.  I would do a search of I am so clueless on the whole thing I fear screwing up even that. 

Just dawned on me that the above may be the wrong question.  What I would really like to do is watch regular tv on my computer.  (been reading too much stuff I think)

Thank you...............

---

### Post by dragonfly41 on 2024-07-27
I always rephrase the OP question.

Found this.

[https://askubuntu.com/questions/1464744/hypnotix-on-ubuntu-23-04](https://askubuntu.com/questions/1464744/hypnotix-on-ubuntu-23-04)

If you really must use hypnotix (I have zero experience with this) then my thoughts are you could dual boot between Ubuntu and Mint (separate partitions). Or run a Mint virtual machine in Ubuntu.

---

### Post by #&amp;thj^% on 2024-07-27
You mean this app:

If so I'll work out a process for you with no mint or mint PPA's

---

### Post by grahammechanical on 2024-07-27
Looking into this question I viewed some Linux Mint forums. Even if you use Hypnotix in Linix Mint you will be disappointed. Many Linux Mint users say it does not work in the sense that very few TV channels load. To quote the main Linux Mint developer as of April 8th 2024

> We only care about the software itself here, we don't provide TV channels. 

Anyone who wants to watch TV on their computers then they should research IPTV. 

[https://www.reddit.com/r/linuxquestions/comments/ocxilm/whats_a_good_iptv_player_for_linux/](https://www.reddit.com/r/linuxquestions/comments/ocxilm/whats_a_good_iptv_player_for_linux/)

VLC is available in Ubuntu and it has addons for Internet Channels. I am not sure if what is offered will be what you are looking for.

[https://addons.videolan.org/browse?cat=322&ord=latest](https://addons.videolan.org/browse?cat=322&ord=latest)

Regards

---

### Post by #&amp;thj^% on 2024-07-27
Seems to work fine on my end. Loading can be slow on some channels.

---

### Post by jgw on 2024-07-31
thank you for all the replies!

I will see what I can do.  I have kinda found a different solution which may work.  Goodwill often has dvd players that are really cheap and not that old.   I was looking at them and most have a hdmi/usb input/output which also means you can hook a computer up as well.  My thought is that one could probably switch from one to the other easier than getting a program.  it would be better if they had a receiver with such input/output but those are harder to find but, I suspect, it won't make any difference. 

Thanks again!!

---

### Post by TheFu on 2024-08-01
What you need to watch TV depends on your location, what the input signal uses (stream/broadcast format/CATV/Satellite) and without that nobody can help.

So, I live in North America and broadcast TV here uses the ATSCv1 standard. That means I need a tuner that supports that and software that works with the tuner.  If I take the exact same equipment to Europe, it won't work at all.  There are a number of other standards and more happening every year because broadcasters don't want end-viewers to have control over when we can watch or because they think they can show commercials AND charge for access.

Many TV players will use the Video4Linux2 standard.

The way I handle TV - Live and Recordings  - is with Silicon Dust HDHR tuners.  They are DLNA servers on the network and available to any network device that supports DLNA and can decode the ATSCv1 signals.  Currently, those are ts containers with mpeg2 video and AC3 audio. Not the most efficient. ATSCv3 is just starting to be broadcast, but because the ATSC standards cobbal wants DRM for everything, they've broken their own standard and very few tuners actually work.  There are about 15 tuners available. The ones that work require internet for DRM reasons, which sorta defeats the idea of broadcast TV.  I hope my govt blocks all DRM on public airwaves. After all, the broadcasters are suppose to be there for the public good as they lease the specific frequencies.

---

### Post by jgw on 2024-08-01
I am all for receivers.  There are, however, about 2 little problems.  The first is that the really good ones tend to be big and there isn't always enough room to put them.  The second is that the really good ones are seriously expensive.  In my installation, however, I have been using a denon harmoney 650 for several years with no problems at all and I bought it used and its still working fine.   I had some problems setting it up but I contacted Denon and they took care of everything.  One of the reason I was considering the hypnotix thing was it might make things easier.  After my answers, however, I think I will stick with my Denon.  You can get one for about 100.00 to 300.00 on ebay and it does the job well.  Its also easy to hook in your computer and swap between the two with the harmoney remote.  It will also take care of speaker stuff.

Thank you for all the replies!  I will mark this one solved.

---

