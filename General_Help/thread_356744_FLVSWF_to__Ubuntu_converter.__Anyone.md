---
title: "FLV/SWF to *** Ubuntu converter.  Anyone?"
date: 2007-02-08
forum: General Help
---

### Post by emarkay on 2007-02-08
I don't want to install the Adobe module, but I have a few .SWF and .FLV videos saved.  
I would rather find a OS (free) converter to convert them into a more easy-to-play format (AVI, MPG, WMV, etc) than to try to find a stand alone player for these formats.  (It seems that there is none.)

ffmpg can't seem to convert the .SWF files, so that option is out.

Any ideas?

THANKS!

MRK

---

### Post by defishguy on 2007-02-08
I haven't used Lives for SWF files, but I understand from the documentation that it can encode and decode them.

Here is a link [http://www.gnomefiles.org/app.php/LiVES]("http://www.gnomefiles.org/app.php/LiVES")

You can also try WinFF for some GUI video conversion goodness.

Here is a link [http://www.gnomefiles.com/app.php/WinFF]("http://www.gnomefiles.com/app.php/WinFF")

Good luck, let us know how it works out.

---

### Post by OmniCloud on 2007-04-23
Ok....here's a thread that maybe I can get some help...

I have Winff and ffmpeg installed...I can open Winff, but none of the conversions work...

Also when I run *sudo Winff* it works, I get the front-end screen

but when I run *sudo ffmpeg* I get this...

[B]smilez@smilez-desktop:~$ sudo ffmpeg
ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory
smilez@smilez-desktop:~$ [/B]

I also installed all the files that looked like that in synaptic but it still doesn't work?!! So i guess the problem is ffmpeg right, but I don't know what else to do after I installed the file that they said was missing from synaptic??

Help guys...Before I got 7.04 I only got the mpeg-2 converter to work. But changing the bitrate and frames made for some good quality videos to transfer to my PS3. This is the only conversion I need to wokr!!! Please help!! anybody...

---

### Post by applez on 2007-05-14
hey hey hey 

Yes this issue is a pain in the *** I am a linux noob but happy to be as I have discovered an awesome world with ubuntu but enough *** kissing.

This problem I came across since upgrading to the edgy eft not just for flv files but any 

Its a pain in the *** a lot of forums seem to have people talking about this problem but no one seems to have an answer apart from making ffmpeg yourself with different options.

The package ffmpeg is chasing libraw1394.so.5 is listed in synaptic but can u download it no no no its obsolete

Also  tovid fails as it waits for its audio.ac3 which it cant have because ffmpeg is to scared to look for libraw1394.so.8 

So checking google for an hour I find the only real answer is to make my own ffmpeg which looks quite heavy for a beginner  there is surely an easier option 

So I checked the folder where libraw1394.so.8 resides usr/lib I notice it says link to shared library 

I dont know what a link to a shared library is but I am now thinking what is I just copy the file and rename the copied file to libraw1394.so.5 

goto usr/lib in naughtylis pick view pick view as list find libraw1394.so.8, right click pick copy, pick view, pick  
right click on libraw1394.so.8 pick copy, pick view as icons, scroll down to bottom of list in space at bottom right right click and pick paste

it will paste a copy of libraw.1394.so.8 with copy in the title right click it pick rename, then in its box type libraw1394.so.5 
hit enter

run your prog that uses ffmpeg happy days!

therefore its linking to whatever its linking to it tricks ffmpeg into thinking its reading what it thinks its reading which encodes mah file and we can all go home early so I make a copy rename it and I think there is now way its going to work but fook me it did!
Yes I am elite and super cool or at least I feel like after pissing around for 2 hours but whahey lateral thinking pays dividends everyones happy bobs your aunties husband! jobs done see you next time for my next top tip.

---

### Post by Lord Illidan on 2007-05-14
I couldn't understand the above post, but Super Converter is great. Only works in Windows, though. :(

---

### Post by applez on 2007-05-14
It is an answer to the problem when ffmpeg bombs out with the error 

ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory

and the reason for the tovid waiting for audio.ac3 problem

cause by ffmpeg

but u cant download the libraw1394.so.5 as it is obsolete in synaptic so u just copy and reanme libraw1394.so.8 to libraw1394.so.5 in /usr/lib and it works great!

---

### Post by Funzo22 on 2007-07-15
> **applez said:**
> hey hey hey 

Yes this issue is a pain in the *** I am a linux noob but happy to be as I have discovered an awesome world with ubuntu but enough *** kissing.

This problem I came across since upgrading to the edgy eft not just for flv files but any 

Its a pain in the *** a lot of forums seem to have people talking about this problem but no one seems to have an answer apart from making ffmpeg yourself with different options.

The package ffmpeg is chasing libraw1394.so.5 is listed in synaptic but can u download it no no no its obsolete

Also  tovid fails as it waits for its audio.ac3 which it cant have because ffmpeg is to scared to look for libraw1394.so.8 

So checking google for an hour I find the only real answer is to make my own ffmpeg which looks quite heavy for a beginner  there is surely an easier option 

So I checked the folder where libraw1394.so.8 resides usr/lib I notice it says link to shared library 

I dont know what a link to a shared library is but I am now thinking what is I just copy the file and rename the copied file to libraw1394.so.5 

goto usr/lib in naughtylis pick view pick view as list find libraw1394.so.8, right click pick copy, pick view, pick  
right click on libraw1394.so.8 pick copy, pick view as icons, scroll down to bottom of list in space at bottom right right click and pick paste

it will paste a copy of libraw.1394.so.8 with copy in the title right click it pick rename, then in its box type libraw1394.so.5 
hit enter

run your prog that uses ffmpeg happy days!

therefore its linking to whatever its linking to it tricks ffmpeg into thinking its reading what it thinks its reading which encodes mah file and we can all go home early so I make a copy rename it and I think there is now way its going to work but fook me it did!
Yes I am elite and super cool or at least I feel like after pissing around for 2 hours but whahey lateral thinking pays dividends everyones happy bobs your aunties husband! jobs done see you next time for my next top tip.


Much simpler, all you gotta do is create a link from libraw.1394.so.5 to libraw.1394.so.8

Run this command:

> sudo ln -s '/usr/lib/libraw.1394.so.8' '/usr/lib/libraw.1394.so.5'

---

### Post by nexx on 2007-07-15
I folowed these instructions and ffmpeg works like a charm for me :

[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

---

