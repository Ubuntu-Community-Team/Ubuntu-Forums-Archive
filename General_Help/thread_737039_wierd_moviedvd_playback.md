---
title: "wierd movie/dvd playback"
date: 2008-03-27
forum: General Help
---

### Post by imperius69 on 2008-03-27
hi, i have ubuntu 7.10 installed, the other day i wanted to watch a dvd but i could not, so i came here to forum to se a solution. found this link

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

i did what is said there but now i get a blue screen on the video area, sound is working telling me the dvd/divx is working, but no image!!! :confused:

while messing around installing new players like VLC i accidentally click 2 times on the movie, that opened 2 VLC windows.

While the first was blue, the second was showing the movie :confused:

Tryed this with the DVD and also the second VLC showed the movie while the first was blue (with only sound).

anyone else experienced this? why is this happening?  is there a solution? 

I have an acer aspire 1604LC with a ATI Mobility Radeon 9000 and compiz is turned off.

Thanks in advanced.

---

### Post by phrawzty on 2008-03-27
> **imperius69 said:**
> found this link

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

i did what is said there but now i get a blue screen on the video area, sound is working telling me the dvd/divx is working, but no image!!! :confused:

When you say that you "did was is said there", what do you mean, exactly ?  There are a number of independent groups of instructions on that page, each corresponding with a different version of Ubuntu.

Have you tried something other than VLC to play the movies - Gxine, for example ?

---

### Post by imperius69 on 2008-03-27
Thanks for the reply :)

i did for ubuntu 7.10

> 
In gutsy to get encrypted DVD playback to work i had to do the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh


yes, i have tried different players, toten xine, vlc and kaffeine

---

### Post by phrawzty on 2008-03-27
> **imperius69 said:**
> yes, i have tried different players, toten xine, vlc and kaffeine

What happened when you used different players - the same thing ?  Please be descriptive as possible - the more information the better !

---

### Post by imperius69 on 2008-03-27
ok, for example, with a divx movie: (btw sorry for my English)

if i open with totem i get blue screen but i get sound so movie is running, then if i open at the same time the same divx movie with VLC (open with VLC) ill get the movie image and sound.

This also works if i open 2 VLC windows.

For DVD's same thing, only difference is that i cant open 2 totem windows so i open 1 in totem then i open the DVD with VLC. The contrary is also true, if i open first in VLC i get no movie but sound yes, then if i say to totem to play dvd it will give me image and sound.

Same thing with kaffeine.

Bottom line is to watch movie i have to open a second windows in any player or elese i wont have image. 

One thing i notice in VLC when i choose "Deinterlace" (mouse right click menu) and choose one of the options then image gone blue screen again :confused: 

So my guess is something is turn off (or not working) when opening second window with movie but if i choose option that involves .... i dont know the word ... like it as to re-work image in screen, it gets on again and image becomes blue !!

again sorry for my English :(

Hope i made myself clear enough and thanks in advanced.

---

### Post by shadyedsan on 2008-03-27
sorry to butt in, but do you have the w32 codecs installed, along with the libdvdcss2 codec? it would make it easier if you did. i had a similar problem to yours and i solved it by installing automatix2 from their website [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) and go to easy direct installation and choose your version of ubuntu. as you have already indicated, you have vlc and totem installed so dvd's should work after you use automatix to install the win32 codecs and the libdvdcss2 codec and other stuff if you prefer :)

hope this helps

---

### Post by shadyedsan on 2008-03-27
> **shadyedsan said:**
> sorry to butt in, but do you have the w32 codecs installed, along with the libdvdcss2 codec? it would make it easier if you did. i had a similar problem to yours and i solved it by installing automatix2 from their website [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) and go to easy direct installation and choose your version of ubuntu. as you have already indicated, you have vlc and totem installed so dvd's should work after you use automatix to install the win32 codecs and the libdvdcss2 codec and other stuff if you prefer :)

hope this helps

forgot to mention that when you come to install it, use the default installer you are offered (gdeb package installer)

---

### Post by imperius69 on 2008-03-27
going to try it thanks, but, what is automatix2 ? and how do i know if i have libdvdcss2 installed?

thank you

---

### Post by shadyedsan on 2008-03-27
automatix2 is a program which allows you to install extras like ubuntu-restricted-extras and codecs which are sometimes not listed in the respostories, and also to make it easy to install codecs. normally libdvdcss2 is installed along with vlc player as they released that codec to decrypt dvd's on the fly. if you are able to open encrypted dvd's then you have libdvdcss2. the w32 codecs will allow you to view the divx files better :)

---

### Post by shadyedsan on 2008-03-27
> **shadyedsan said:**
> automatix2 is a program which allows you to install extras like ubuntu-restricted-extras and codecs which are sometimes not listed in the respostories, and also to make it easy to install codecs. normally libdvdcss2 is installed along with vlc player as they released that codec to decrypt dvd's on the fly. if you are able to open encrypted dvd's then you have libdvdcss2. the w32 codecs will allow you to view the divx files better :)

which version of ubuntu have you got installed by the way? if it's fiesty then there is a known problem with sound for playing dvd's

---

### Post by imperius69 on 2008-03-27
installed automatix2 and installed the w32 but still same problem :(

funny thing is when i finished installing ubuntu asked me to update, 300 megas of updates :o

is this something to do with automatix replacing files or was just coincidence?

---

### Post by imperius69 on 2008-03-27
> **shadyedsan said:**
> which version of ubuntu have you got installed by the way? if it's fiesty then there is a known problem with sound for playing dvd's

uibuntu 7.10

---

### Post by phrawzty on 2008-03-27
> **imperius69 said:**
> installed automatix2 and installed the w32 but still same problem :(

funny thing is when i finished installing ubuntu asked me to update, 300 megas of updates :o

is this something to do with automatix replacing files or was just coincidence?

It's worth noting that Automatix is not supported in the official Ubuntu repos, which means that it might do things to your system that are unexpected. :/

---

### Post by shadyedsan on 2008-03-27
wow, that never happened to my system!

i thought that may have solved your problem for viewing dvd's byt apparently not. might there be a hardware problem? what are the specs from the lspci output from terminal?

---

### Post by imperius69 on 2008-03-27
lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:09.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
00:09.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
06:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface


should i do the updates?

Radeon RV250 [Mobility FireGL 9000] ?? my vga is Ati Mobility Radeon 9000, drivers the same??

---

### Post by shadyedsan on 2008-03-27
ati graphics can be tricky to get working in ubuntu or linux in general because of the drivers. if you have an nvidia card it would have been easier probably. there is nothing to suggest that the other hardware is causing the problem.

what are the updates for? load up update-manager and it will tell you

---

### Post by imperius69 on 2008-03-27
well, 300 megas worth of updates, i gess everything lol
i saw there openoffice upgrade, bunch of gnome things, some other files even automatix update ...

my ati was working fine, i think, before installing the dvd thing i could watch divx movies, even compiz was working fine, i think :p im n00b in linux :(

---

### Post by shadyedsan on 2008-03-27
just general stuff for your system, not anything to do with automatix. if it was working fine with compiz and divx movies, and it still works then nothing has changed. of course not every system is the same so mixed results are expected. maybe others on this forum will be able to help if you post to the multimedia and video threads. i'm stumped on this one i'm afraid :(

---

### Post by imperius69 on 2008-03-27
well, no problem, thanks for your help :)

wasn't enough to have the wireless boot bug but now the movie watching bug :lolflag:

"Ubumtu Linux, an OS with Attitude - Can u handle it" 	:biggrin:

hahaha

---

### Post by shadyedsan on 2008-03-27
lol sorry i couldn't help further :mad:

:D

---

### Post by imperius69 on 2008-03-27
> **shadyedsan said:**
> lol sorry i couldn't help further :mad:

:D

but u did :) learned about automatix and installed picassa from it :) all good :)

---

### Post by haraldmilz on 2008-03-31
I had the same problem once. It was because of beryl or metacity OpenGL effects. Try going to System > Preferences > Appearence and disable any Visual effects you might have enabled. Try DVD playback again and let us know the result! KR, Harald

---

### Post by imperius69 on 2008-03-31
hi, sorry for the late reply, wasn't home

even with compiz off its the same, still need to open a second window to have the picture of the movie.

---

### Post by haraldmilz on 2008-04-07
Sad. Tried opening a bug in automatix? Maybe they can help further. Good luck. KR, Harald.

---

