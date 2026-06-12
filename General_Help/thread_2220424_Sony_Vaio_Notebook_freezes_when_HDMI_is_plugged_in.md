---
title: "Sony Vaio Notebook freezes when HDMI is plugged in"
date: 2014-04-27
forum: General Help
---

### Post by guilherme6 on 2014-04-27
Hi people,

I hope you can help me. I have a Sony Vaio PCG-3B2L notebook. I used to have Windows Vista as factory OS, but I formatted the notebook and installed Mint. After settiing up Mint I could use my Phillips TV to extend my notebook's monitor normally, but after a few days the notebook started freezing whenever I plugged the HDMI cable in it. I thought that it was some sort of compatibility problem with Mint, so I formatted the notebook once again installing Ubuntu this time, but the problem remained. Ubuntu simply freezes completely (including mouse) whenever I plug in the HDMI cable. If I plug it in before starting the notebook, Ubuntu does not start and I get an empty black screen. I don't even know where to start.

Thanks in advance.

---

### Post by cranerja on 2014-04-28
I can't find the specs for that laptop anywhere. What does```
lspci | grep "VGA"
``` return?
Also, since it was working originally, could either of the ports or cable have become damaged? Have you tried different cables, screens, or ports?

---

### Post by guilherme6 on 2014-05-01
The output is the following:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I've just changed the cable and tried to plug it in. The laptop freezes the moment I plug the HDMI in the TV. I tried even using the HDMI cable that was plugged to my cable tv decoder and got the same result. I left a youtube video playing with sound while I plugged the cable in when I did, even the sound of the video started looping where it stopped, so it isn't just a video freeze I suppose.

---

### Post by cdeboden on 2014-05-02
I have exactly the same problem on my Medion P8614 laptop with a Mobility Radeon HD 4650/5165 graphics card. 

In my case there is only the open source driver, maybe you'll have better luck, and there may be a good driver available. 

I think this is a critical bug in the xorg server. I think of a clock frequency problem with older video cards. 
I did not suffer from image problems and the computer started simply smoothly on with Ubuntu 13:10 (all variants), but I had no sound with HDMI. 
I have problems with both HDMI and VGA with Ubuntu 14.04LTS. But the VGA output is normally not in use here.
It's like a Russian roulette, sometimes it does work and often does not work. 
As soon as it works, I have a perfectly sound over HDMI with Ubuntu 14.04.
 
My 2nd screen is a Sony KDL 32p2530 HD-ready television, happens to be a Sony :D

See also:
[http://ubuntuforums.org/showthread.php?t=1543009&page=38](http://ubuntuforums.org/showthread.php?t=1543009&page=38)

and on Launchpad:
[https://answers.launchpad.net/ubuntu/+question/247770](https://answers.launchpad.net/ubuntu/+question/247770)
(dutch language)

ps Sorry for my bad English, i'm from the Netherlands.

---

