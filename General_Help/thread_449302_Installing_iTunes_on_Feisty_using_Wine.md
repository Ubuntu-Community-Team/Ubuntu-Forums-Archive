---
title: "Installing iTunes on Feisty using Wine"
date: 2007-05-20
forum: General Help
---

### Post by _Pieter_ on 2007-05-20
Hello! I have been trying to install iTunes on my computer, and Wine seems to be handling the installation pretty well in the beginning. But at some point, the installation generates an error and has to close ("please tell Microsoft about this problem";) ). The same thing happened when I tried to install Office 2003 (I know, OOo is a good alternative but I REALLY need the advanced stuff in Excel). 
Is there something wrong with Wine, or do I do something wrong? When I install, I leave the standard options like they are, and I also do not change the location of where it needs to be installed. 
Any help will be greatly appreciated.

---

### Post by patrickfromspain on 2007-05-20
Why would somebody want itunes in Linux? If you want itunes for using you IPOD, forget about it: even if you got it running, Ipod wouldn't work, use gtkpod, amarok, banshee... lot's of apps. If you want itunes to listen music, just use amarok. If you want itunes to buy music... there's amule (:D) or a lot's of diferent music stores, were you'll find what you need.

As for office 2003.. you'll need to buy Crossover office to make it work, but some things don't work (math equations in word, for example), so I'd say the best solutions is to use windows: you can install it on a virtual machine

---

### Post by rich.bradshaw on 2007-05-20
Why would you want iTunes on a computer that you own?

---

### Post by justynbutler on 2007-05-20
> **rich.bradshaw said:**
> Why would you want iTunes on a computer that you own?

Perhaps he would like to buy DRM-free songs from iTunes?

---

### Post by aldenhg on 2007-05-20
These forums are not the place to pass judgment on someone's software preferences. OSS is better almost by definition, but we don't need to proselytize every second of every day. Tell him that it won't work and what his alternatives are, but don't make fun of him or his choices. Every one of us didn't know about OSS at some point and we've all been noobs. Get over it and get back to helping people so that they have a positive OSS experience and decide to continue using it. Doing otherwise won't do anything for Linux's 'only for hardcore nerds' image.

---

### Post by aysiu on 2007-05-20
I don't understand why people feel the need to bash someone wanting iTunes. Just because you don't like iTunes doesn't mean others can't like it. I happen to like iTunes a lot, but it isn't currently ported to Linux. 

Fortunately, there are many great alternatives (some of which have features that iTunes *doesn't* have). To the OP, I've never seen someone successfully install iTunes in Wine--on these forums or anywhere else on the web--so as to make it fully functional. Crossover Office can install a slightly older version of iTunes, but I don't believe even that can access the iTunes music store.

Your best bet, if it's iPod syncing is one of these native Linux applications:
[http://en.wikipedia.org/wiki/Comparison_of_ipod_managers#Linux](http://en.wikipedia.org/wiki/Comparison_of_ipod_managers#Linux)

If you want the iTunes music store on Ubuntu, too bad. There are other options, though:
*eMusic
*Magnatune
*Jamendo
*buying CDs (yup, the old-fashioned way)

---

### Post by pmusser on 2007-05-22
Hio!

I have a dual boot system w/ Win2k and Ubuntu (just installed today), and I was hoping someone could point me in the right direction. I use iTunes on my win2k install and love it dearly, and I have all the CD's I've ever bought (which were all stolen a year ago) backed up into it... However, if any of you know of a good program that does the following, I would be more than happy to try it out. the program i need:

-Plays M4A's
-Sorts & Organizes the music in a visually similar way to iTunes
-Has a party shuffle.

i know Rhythmbox does the middle one, but I couldn't for the life of me get it to play M4A's... the question then is, is there a plugin I can nab for it so that it would?

Thanks in advance...

---

### Post by pmusser on 2007-05-22
Oh, and I just did a little search in the help page for rhythmbox and it makes mention of the 'protected' status of m4a's purchased from iTunes Store... Not applicable for me I think, since I don't BUY music from iTunes.

Of course.. I could be wrong. It happened once before... ;D

---

### Post by aysiu on 2007-05-22
Apparently [AmaroK can play non-DRM'ed M4P files](http://ubuntuforums.org/showthread.php?p=1612412#post1612412).

---

### Post by Purple Grant on 2007-05-24
When I went fully linux recently, iTunes was the one thing I thought I'd really miss,

But I have since discovered Amarok, which is in fact I'd say much better than itunes (recognised and supported my nano as soon as I plugged it in too)
If a linux version of iTunes came out tomorrow I would still keep using Amarok.

have a go of that before you tear all your hair out trying to make itunes go

---

### Post by atlfalcons866 on 2007-05-24
you can install itunes

[http://www.frankscorner.org/index.php?p=itunes6](http://www.frankscorner.org/index.php?p=itunes6)

---

### Post by testube_babies on 2007-05-24
I really missed iTunes as well when I first moved to Linux.  But, like many others, I've found Amarok to be a suitable replacement which is in many ways better than iTunes.  I now find myself missing Amarok when I'm in Windows! Luckily, sometime in the near future Amarok will be made completely cross-platform.

---

### Post by aysiu on 2007-05-24
> **atlfalcons866 said:**
> you can install itunes

[http://www.frankscorner.org/index.php?p=itunes6](http://www.frankscorner.org/index.php?p=itunes6)
From the bottom of that page: > Notes:
Performance might be poor.
I have not tested the iPod.
Burning cds does not work.

---

### Post by zach12 on 2007-07-17
yes i see that but i'm thinking of useing itunes in wine to buy tunes and then play then in Songbird (i think that is the best ituneslike progam in linux

---

### Post by zach12 on 2007-07-17
hey here's how to install iTunes in wine 
> 
Tested Wine version: 0.9.19

Now type wine itunessetup.exe
After installing iTunes Quicktime will be installed. Kill Wine now.
You must install QuickTime Alternative ([http://www.free-codecs.com/download/QuickTime_Alternative.htm):](http://www.free-codecs.com/download/QuickTime_Alternative.htm):) wine quicktimealt173.exe. After the installation is ready download wininet.dll and copy it to ~/.wine/drive_c/windows/system32.
Set iTunes to use a virtual desktop in winecfg, also set wininet.dll to "native".
Type wine itunes.exe in the installation directory to run itunes.

---

### Post by testube_babies on 2007-07-17
> **zach12 said:**
> yes i see that but i'm thinking of useing itunes in wine to buy tunes and then play then in Songbird (i think that is the best ituneslike progam in linux

Songbird requires an add-on to allow you to playback Fairplay DRM'd tracks from iTunes.  Guess what?  That add-on is for Windows and Mac only.  So no Fairplay for Linux.  Yet.
[http://addons.songbirdnest.com/extensions/other_versions/23](http://addons.songbirdnest.com/extensions/other_versions/23)

Or am I wrong?

---

### Post by stchman on 2007-07-17
You would think that some Apple people would have heard of the need for iTunes for Linux and just make the thing.

There seems to be a market here.

---

### Post by stchman on 2007-07-17
> **_Pieter_ said:**
> Hello! I have been trying to install iTunes on my computer, and Wine seems to be handling the installation pretty well in the beginning. But at some point, the installation generates an error and has to close ("please tell Microsoft about this problem";) ). The same thing happened when I tried to install Office 2003 (I know, OOo is a good alternative but I REALLY need the advanced stuff in Excel). 
Is there something wrong with Wine, or do I do something wrong? When I install, I leave the standard options like they are, and I also do not change the location of where it needs to be installed. 
Any help will be greatly appreciated.

I don't believe that Office 2003 will work under WINE.  I believe that Office 2000 will.

---

### Post by vexorian on 2007-07-17
> The same thing happened when I tried to install Office 2003 (I know, OOo is a good alternative but I REALLY need the advanced stuff in Excel).
Like what? I mean , it would be good that you pointed those outs so OOo people could try improving.

---

### Post by qamelian on 2007-07-17
> **stchman said:**
> I don't believe that Office 2003 will work under WINE.  I believe that Office 2000 will.

Office 2003 will work in Wine but now perfectly. Word and Excel work fine, and I believe PowerPoint works, but there are problems with Access and Outlook.

---

### Post by zach12 on 2007-07-20
i'v played mp3's from iTunes a few times in Songbird (in linux) and they play well!!!

---

### Post by finalcut on 2007-07-21
if i can not use iTunes what program would let me import my iTunes library and play it in that program?

Any help is greatly appreciated, feel free to IM me

---

### Post by zach12 on 2007-07-25
if you backed up your iTunes library then just put the cd's(or dvds)in on ubuntu and copy
then to your harddrive then open the mp3's in the progam that you like 
have fun!
ps if you like itunes then try Songbird [http://www.songbirdnest.com/](http://www.songbirdnest.com/)

---

### Post by notwen on 2007-07-25
+1 GTKpod or Amarok

---

### Post by t2000kw on 2007-07-30
> **pmusser said:**
> . the program i need:

-Plays M4A's
-Sorts & Organizes the music in a visually similar way to iTunes
-Has a party shuffle.

i know Rhythmbox does the middle one, but I couldn't for the life of me get it to play M4A's... the question then is, is there a plugin I can nab for it so that it would?

Thanks in advance...

This might take care of part of your needs. THere are M4A to MP3 (and maybe other formats as well) converters. Here's one, but I don't know the cost. Apparently you can try it out for free.

[http://www.mp3-cd-converter.com/convert_mp3/free_convert_m4a_to_mp3.html](http://www.mp3-cd-converter.com/convert_mp3/free_convert_m4a_to_mp3.html)

---

