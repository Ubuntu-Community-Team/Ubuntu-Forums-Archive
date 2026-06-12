---
title: "FlashPlayer unusual displaying swf content"
date: 2014-03-29
forum: General Help
---

### Post by Janusz_R on 2014-03-29
Im not new in linux, but never faced similar situation. I do not have any idea what I made wrong. After install Ubuntu 12.04 on my old IBM g40 2388 model I install flash player. For some reason swf content wasnt displayed properly. I removed it and install swfdec - better, but many errors with external loaded swf files. Found another player 'lightspark'. Similar problem as with adobe fp. I made move and here is link: [http://youtu.be/KMcUpzAgutQ](http://youtu.be/KMcUpzAgutQ) showing infocentre.pl full flash site. In addition I was trying to downgrade FP to 10 version and on movie one can see version 10, but with the newest sfw files on web look similar,
Maybe someone could help me to solve this problem?

---

### Post by mörgæs on 2014-03-30
Hi, welcome to the fora.
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Janusz_R on 2014-03-30
Dont see any "add file" so put the file here:
[http://www.infocentre.pl/lstw.txt](http://www.infocentre.pl/lstw.txt)

---

### Post by mörgæs on 2014-03-30
This is old, but standard hardware. Flash should work in Lubuntu 13.10, but you need a small modification for the Intel graphics card.
It's all explained in the link in my signature.

---

### Post by Janusz_R on 2014-03-30
Sir, You were right. Put mentioned info into xorg.conf solved problem. Thanks a lot!
I will stay with 12.04.

---

### Post by mörgæs on 2014-03-30
Good, please mark the thread 'solved'.

---

### Post by Handssolow on 2014-03-30
Sorry but this didn't get flash working on my old Toshiba Satellite laptop with it's Intel 82852/855M Integrated Graphics Device. On Youtube I get purple and green and it plays in only half of the usual window, but sound is OK. I've got Google Earth, DTV and DVD Video playback working normally. If I need to view a Youtube clip I  can download, save and play it as a MP4 file.

I'd not used this laptop for a couple of months and after lots of updates, the new Firefox 28 lost my configurations except for bookmarks. It created an old data file on my desktop, though in the end I manually re-installed my prefered Firefox Add-ons. Adobe Flash is now broken as mentioned. I've tried reinstalling Flash and reverting to an older version of Flash plus the suggested changes in the xorg.conf  from “sna” to “uxa”.

I'm running Ubuntu 12.04 LTS and apart from the current Adobe Flash issue, the laptop still works fine.

---

### Post by mörgæs on 2014-03-31
Do you feel like testing how it behaves in 14.04?

---

### Post by Handssolow on 2014-04-06
Solved here too. I've got YouTube clips playing again normally on my old Toshiba Satellite laptop by using the Firefox Add-on, Video WithOut Flash 1.4.1. Whilst this hasn't strickly solved my problem running Adobe Flash on 12.04 (with this Add-on disabled I still get purple/green video), it doesn't matter, I can stream and play YouTube videos.

With Adobe's Flash support heading for the sunset, it's reassuring that I can manage without their help.

---

