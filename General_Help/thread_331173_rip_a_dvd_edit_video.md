---
title: "rip a dvd/ edit video"
date: 2007-01-04
forum: General Help
---

### Post by Elena678 on 2007-01-04
hej, can sonboddy help me please. I would like to coppy a dvd to my cumputer. what program do i need to use, and how do i need to install it?

If it's possible, i would like to store it as a dvix or somthing like that, becouse i have not dat much harddisk.

When it's on my computer, is there also a program to add it, like in windows, windows movie maker.

oh yea, when it's on my pc, can i burn it after all back to a dvd or a cd, if yes, what program do i need to have for that?

tanks a lot

Greetings

Elena

---

### Post by pseudonym on 2007-01-04
Hi, you can do all these things on Ubuntu. there are many programs in the repositories (use the search function in synaptic package manager), but there is a good list of applications in [this forum]("http://forum.doom9.org/forumdisplay.php?f=63") , many of which are easily installed via Synaptic.

HTH :)

---

### Post by TLE on 2007-01-04
**dvdrip** for making a copy to your HD. (Please note that you will need to have enough space on your HD to make a complete copy of the DVD while it is working on the copy)

**gnomebaker** or **k3b** to burn files to a optical disc.

Both of them can be installed with synaptic.

Links to documentation:
[how to install software with synaptic]("https://help.ubuntu.com/community/SynapticHowto"). This was easily found by searching the [wiki]("http://wiki.ubuntu.com/") for "installing software"
[dvd::rip]("http://www.exit1.org/dvdrip/doc/index.cipp")
Both gnomebaker and k3b should be pretty easy to use. Otherwise try to google for some documentation on them. Also if you are on a GNOME system gnomebaker has builtin help.

---

### Post by handband2 on 2007-01-04
Elena678,

check out these sites:

**Gnome**:  [http://www.gnomefiles.org/category.php?cat_id=12](http://www.gnomefiles.org/category.php?cat_id=12)

**KDE**:  [http://kde-apps.org/index.php?xcontentmode=220x221x56](http://kde-apps.org/index.php?xcontentmode=220x221x56)

To install the programs go to **Applications **-> **Add/Remove**.  Then do a search for the program you like.  OR look for .deb file for Ubuntu.   

For Divx support I recommend [Automatix]("http://www.getautomatix.com/"), or [EasyUbuntu]("http://easyubuntu.freecontrib.org/get.html").  You can also install the codec support [CLICK HERE]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")

I hope that helps

---

### Post by Elena678 on 2007-01-05
> **handband2 said:**
> Elena678,

check out these sites:

**Gnome**:  [http://www.gnomefiles.org/category.php?cat_id=12](http://www.gnomefiles.org/category.php?cat_id=12)

**KDE**:  [http://kde-apps.org/index.php?xcontentmode=220x221x56](http://kde-apps.org/index.php?xcontentmode=220x221x56)

To install the programs go to **Applications **-> **Add/Remove**.  Then do a search for the program you like.  OR look for .deb file for Ubuntu.   

For Divx support I recommend [Automatix]("http://www.getautomatix.com/"), or [EasyUbuntu]("http://easyubuntu.freecontrib.org/get.html").  You can also install the codec support [CLICK HERE]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")

I hope that helps


By installing dvdrip, i saw i have rar version 3.30 on my computer. but the maximum version is only 2.99 what do i need to do now?

thanks

---

### Post by TLE on 2007-01-05
rar is only needed if you want to use subtitles and compress them. They can usually be compressed from about ~5-8 MB to about ~1 MB. But since the entire movie will usually be >700 MB in size it's not really a necessity. So before you do anything else about it, you need to figure out if you need subs and if they should be compressed

---

### Post by Elena678 on 2007-01-05
yea, i need subtitles, my english is not so good :P

okei, i could finish one part of the things to put the dvd to my computer.

i could put create some vob files on my pc, so now i can see the movie on my computer in DVD quality. that's nice, but it's to havvy for my pc, so i was tryng to convert it to divx4. but then i got an error.

i tink this is the most importent of the message
> 
Job 'transcoding video - title #1 , pass 1' failed
....
libdvdread: Couldn't find a device name.
libdvdread: Can't open dile VIDEO_TS.IFO.
....
[transcode] warning: /usr/lib/transcode/export_divx4.so: cannot open shared object file. No sich file or directory
....
[transcode] warning : (dl_loader.c) loading "/usr/lib/transcode/export_divx4.so" failed
[transcode] warning : (encoder.c) loading video export module failed
[transcode] warning : failed to init export modules.
[transcode] critical: plug-in initialization failed


greetings

Elena

---

### Post by Elena678 on 2007-01-05
I also can't convert it to vcd, that would also have been nice

then he is not giving anny error, he even says, DVDRIP_SUCCESS but i can't find the file, so i tink ther still be somthing wrong :(

so, if somboddy know what is the problem, please help me

thanks

Elena

---

### Post by TLE on 2007-01-05
Ok first things first. The first error is probably just because you don't have the DivX codec installed. Try once to use the Xvid codec instead. It should be the same quality, and it's open source ;) and then, even if you prefer DivX then at least if it works with Xvid, we'll know what the problem is.
\TLE

---

### Post by Elena678 on 2007-01-05
yea, i have the error not annymore now, but i have only a avi file of 6,4kb now, and a dvdrip-info file of 923 bytes. i tink this is also not a good thing :S

do you know how i can fix this prob.?

greetings

elena

---

### Post by TLE on 2007-01-05
Maybe, but first of all. You should really read the documentation on the dvd::rip homepage first, if you haven't already done it. If there is something you don't understand in the documentation you can just ask. But it is a lot easier to find the problem if I know that you followed [this documentation]("http://www.exit1.org/dvdrip/doc/index.cipp").

---

### Post by Elena678 on 2007-01-06
yea, sorry, i will try to make it a bit more clear ;)

1ste: yea, i followd the doccument ;)

2de: wel, some posts ago i told my vcd was also not working.
but i could fix this allready, this is working perfect now, i can convert to vcd & svcd.
but when i put it in 700mb. the quality is not that good, as i saw divx (xvid i never saw :) ) movies.

so, becouse the svcd is working, i tink it's somthing with the codec. so i went to my synaptic package manager. and installed some divx & xvid stuff, but i don't know if it was the right, so, if the problem is there, maybe you know what i need to instal :)

thanks / tack :)

greetings

Elena

---

### Post by TLE on 2007-01-06
It probably is a codec issue. Try and have a look at [this page]("https://help.ubuntu.com/community/RestrictedFormats") that should get you up and running with both Xvid and DivX. I would however still recommend Xvid for a first try since it is better intergrated into Linux.

---

### Post by Elena678 on 2007-01-06
i tink it's okei now, i switched from avi to ogg, and now i can convect it also to xvid. i don't know if it realy gonne work, becouse it is still bussy, but i hope so, so thanks for all the help

greetings

---

