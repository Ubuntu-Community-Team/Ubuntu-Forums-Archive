---
title: "kino's busted"
date: 2005-09-20
forum: General Help
---

### Post by rob666 on 2005-09-20
As you can tell from my title, I'm having a few problems.

With the kino that comes with kubuntu (kino 0.75-6) all video from all codecs is mangled, regardless if I capture (the captured files can however be played in mplayer) or import them. The bottom eigth of the frame is green or red and the picture is made up of huge pixels. So I installed kino-0.7.5 from source. But then I started to get other problems. Before getting to those here are some details on my system. 

I am running exclusively kde on my system so I haven't been able to try this out on gnome. Although I have all the necessary libraries installed, so it should work. I've also built kino-0.7.6 from source and got the same problems.

I have all necessary modules loaded: i.e. ieee1394, raw1394, ohci1394, video1394 and dv1394. With all necessary permissions granted. 

I have kernel 2.6.10-5-686 loaded. DMA is enabled and I get 30mb/s on my harddrive, after it's had its morning coffee.

so here now the problems I've encountered

1)raw1394 is selected in preferences->ieee1394, I open capture, I click on av/c, I click on play, it does play shortly, and then I get the message "The Application "kino" has quit unexpectedly", kino crashes, and my mini-dv keeps playing. This happens with the kubuntu kino, too.

If I've opened kino in the console I get the following messages:

reader < # incomplete dropped frames: 1
reader < # incomplete dropped frames: 2
reader < # incomplete dropped frames: 3
....
reader < # incomplete dropped frames: 50

/var/log/messages gives the following messages a few hundred times per second:

.....
Sep 20 00:47:19 localhost kernel: ieee1394: dropped iso packet
Sep 20 00:47:Sep 20 00:47:19 localhost kernel: ieee<6>ieee1394: dropped iso packet
Sep 20 00:47:19 localhost kernel: ieee1394: dropped iso packet
Sep 20 00:47:19 localhost last message repeated 222 times
Sep 20 00:47:19 localhost kernel: ieee1394<6>ieee1394: dropped iso packet
.....

I have libraw1394-5 0.10.1-1.1 and dev installed. Capturing works with /dev/dv1394 so it can't be a faulty connection.

2)Kino don't play raw dv files it's captured properly. It don't play raw dv files dvgrab's captured either. It does on the otherhand not mind playing an odd .dv files I'v downloaded off the internet. And the raw dv files dvgrab and kino have captured can be played on mplayer, kdenlive and playdv.
The captured raw dv files do play on kino, but there are 5 big grey squares and the picture keeps scrolling down the screen like an old tv. The sound prattles a bit too, kind of as if it were modulating. 
I've had preference->display set to gdk, xv, and reduced xv all with the same effects. I have libdv4-0.103-2 & libdv4-dev installed.

3) Lastly I can't get any effects to work on .mov files. Avi's work fine, so the effect plugins do work. I have kinoplus-0.3.3-3 and kino timfx 0.2.2-2 installed, but they aren't recognized by kino.
When you put a video transition or filter on a file it sounds like a super 8 projector's running. This happens with 44 and 48 khz. I have oss non-free so it can't be because of that.
 
When I try to add an audio filter or audio transition all hell breaks loose. There's little left of the original picture. In pause the five squares that I saw with raw dv show up again. In play the picture is scrolling again, but much faster and it's difficult to recognize anything anymore.The sound clicks like crazy and the clips following the effect are distorted. I figure that because these fx clips are also stored in .dv files this also has something to do with the second problem. Quicktime1-0.9.3-2ubuntu1 is loaded along with the dev files.

I guess my problems relate to the fact that I have kino built from source but the dependencies are off the repositories. I guess kino can't find some files that it needs to run properly. I have to point the kino-built-from-source to the right places or I have to get the original-kubuntu-kino to recognize the codecs. Anyway, I can capture, edit, add effects, and export using avi. This is definetly way better than the good old days when I was running kino on a 700hz computer and it kept crashing. But, I would still pick raw dv and quicktime over avi anytime.

Anyway if anyone could help me out it would sure be appreciated.

---

