---
title: "still no sound."
date: 2007-08-06
forum: General Help
---

### Post by hallbrian on 2007-08-06
Hi am new to ubuntu. been a slackware for sometime on an of with windows.
Got a new laptop the other week, which came with windows vista did not like it at all.

So went back to Linux and try something other than slackware.

Am liking ubunto very much, and i like the look and feel of gnome, ive always been a kde user.

Had i few problem with the wireless, took me some time to get that up and running, and the other problem i am having is with the sound (no sound at all) tried every thing still no luck. so here is my first post.

here is my audio device using lspci -v

Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at c0400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

all are unmuted in alsamixer.

Found this post when looking for solution in the forum. ( [http://ubuntuforums.org/showthread.php?p=3121894#post3121894](http://ubuntuforums.org/showthread.php?p=3121894#post3121894) )

This person had the same device as me. followed the advice given that seemed to work for him, did that and still no go.

Any help with this would be great.

Brian

---

### Post by r4ik on 2007-08-06
I hope this helps,

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by hallbrian on 2007-08-06
Thanks for that, yeah i see that post before, so try again did all step and all the different solution there didn't work.

Brian

---

### Post by ZipoTe on 2007-08-06
I suggest you to use alsaconf. It's a tool included in alsa-utils
[URL="http://www.alsa-project.org/alsa/ftp/utils/"]
http://www.alsa-project.org/alsa/ftp/utils/[/URL] download here.

Untar the file, and follow the instructions which are in the text file INSTALL. Then run alsaconf. 

Post here any trouble you have :)

---

### Post by hallbrian on 2007-08-06
Done that.

returned

brian@brian-laptop:~$ alsaconf
bash: alsaconf: command not found
brian@brian-laptop:~$ sudo alsaconf
sudo: alsaconf: command not found

Cheers
Brian

---

### Post by ZipoTe on 2007-08-07
By default alsaconf is not in ubuntu, i don't understand why... you have to download it. In my previous post I linked the web page in where alsa-utils is.

Download, untar it and then via terminal go to the folder. Then:

./configure
make

After that, go to the folder called alsaconf and run it :)


_**offtopic:**_

Why don't they include alsaconf? in debian we have by default and lots os sound problems can be solved with it.

---

### Post by hallbrian on 2007-08-07
Yeah thats what i did, keep getting errors to install other stuff when i ./configure

./configure for alsa-utils 
Fatal error: Install alsa-lib package at first...

so downloaded the alsa-lib
./configure for alsa-lib
Fatal error: Install alsa-driver package at first...

so downloaded alsa-driver
./configure for alsa-driver that works but when i do make i get more errors
In file included from mixer.c:23:
../include/driver.h:50:26: error: linux/config.h: No such file or directory
make[1]: *** [../include/modules/mixer.ver] Error 127
make[1]: Leaving directory `/home/brian/downloads/alsa-driver-0.4.0/kernel'
make: *** [compile] Error 1

Think i may have to do a new install, been messing around with stuff and trying different things that have been posted in other forums, this may have messed it all up.

Can i do all this from the live cd, to test or do i need modules or something.

Thanks 
Brian

---

### Post by dragonwings on 2007-08-07
sudo asoundconf list
to get a list of soundcards you have ,take note of them

now
sudo asoundconf set-default-card (here is where you put your sound card name)


eg" for mine i put
sudo asoundconf set-default-card Audigy2

job done

---

### Post by hallbrian on 2007-08-07
yeah ok i tryed that still no look.
my asoundconf list show

SB (thats it)

But in alsamixer it show as
Card: HDA ATi SB
Chip: Realtek ALC861-VD

So i try them both
sudo asoundconf set-default-card SB
sudo asoundconf set-default-card HDA ATI SB

Both didnt work.
I did find one thing out dont sure if this makes any differance
When i did the second one HDA ATI SB i couldn 't access alsamixer, but when i did it SB i could..

Realy hope i can get this working dont really want to go back to vista.
I all so did the alsa-utils from live cd and got the same errors as before need to install the others first and get the errors.

Cheers
Brian

---

### Post by ZipoTe on 2007-08-07
ok, i have done some google work and i'm :shock:

you have to install ja-trans and gettex packages, then go to the folder alsa-utils and run:

make clean

then try to compile it again

---

### Post by hallbrian on 2007-08-07
Nope that didnt work. got and error with that too

ubuntu@ubuntu:~/alsa-utils$ make clean
make -C include clean
make[1]: Entering directory `/home/ubuntu/alsa-utils/include'
Makefile:6: ../Makefile.conf: No such file or directory
make[1]: *** No rule to make target `../Makefile.conf'.  Stop.
make[1]: Leaving directory `/home/ubuntu/alsa-utils/include'
make: *** [clean] Error 2

Thanks for all your help, seems that this card doesnt want to work.. :(

Cheers
Brian

---

### Post by hallbrian on 2007-08-07
ok thanks for that, still couldn't get the ./configure to any thing after installing thoses packages. but after some other stuff i got ut to work, i can now do alsaconf

this is what it showed
[IMG]http://www.brianhall.info/alsaconf.png[/IMG]

So i did the first one rebooted still no sound/all are umuted.

Cheers
Brian

---

### Post by ZipoTe on 2007-08-08
try running alsamixer and see if your card is selected ^^

---

### Post by hallbrian on 2007-08-08
Yeah its does

Card: HDA ATi SB
Chip: Realtek ALC861-VD

Just reinstall vista now, will be using ubuntu in virtualbox for the time being, till i can this sorted, at least this way i can still use ubuntu and do the things i need sound for.

Thanks for all you help, hope to get a fix for this soon, really dont like vista all that much.

Cheers
Brian

---

### Post by hallbrian on 2007-08-08
Alright,

Have done my reinstall to vista and have ubuntu install via virtualbox.
I have sound now, i use the setting in vistualbox to use windows sound.

Thing is when i now do alsamixer my card and chip are now different, is this because it the vistualbox settings or should it be the same, alsa now reads.

card: Intel 82801AA-ICH
chip: SigmaTel STAC9700,83,84

Cheers
Brian

---

### Post by ZipoTe on 2007-08-08
Did you install ubuntu again or planing to do? :neutral:

---

### Post by hallbrian on 2007-08-08
Sort of, i installed it in windows in virtualbox on virtual hard drive, choosing you windows sound.

Cheers
Brian

sorry you = use

---

### Post by ZipoTe on 2007-08-10
But if you want to solve the sound problem... virtualizing ubuntu won't help... or i'm wrong?:confused:

---

