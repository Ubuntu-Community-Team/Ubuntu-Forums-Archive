---
title: "headers &amp; sense"
date: 2008-02-26
forum: General Help
---

### Post by odd1here on 2008-02-26
**[SIZE="5"]HI[/SIZE]**\\:D/

i humbly request guidance:

using the realtime kernel of gutsy for ubuntustudio, am regularly updated with standard distro.

& sideways my sound while trying to build alsa modules.

i have linux-headers-2.6.22-14-rt source 

is same as kernel-2.6.22-14-rt/ using 
uname -r

an problem:

when building alsa, make install can't find stuff (.ko) in acore to build modules.
:-k
it ask me where is it!??!
i look where it directs. 
is not there either.

acore is Empty!

where it go!?

why it not there!?

dunno..

so i come here, seek revenge!
j/k


CRS (can't remember ****) if there is something i could run to get everything i don't have.
like maybe, apt-get install allthestuffineedtocompilestuffinthefuture -annotbreakthestuffigotworking

thx for time i need lot's, cuz is slow.


is good:
[http://www.onsetaudio.com/Grym-KILL_SPACE.mp3](http://www.onsetaudio.com/Grym-KILL_SPACE.mp3)
&
[http://www.dubstep.com.ua/mp3/Komonazmuk_Feb_2008_Mix.mp3](http://www.dubstep.com.ua/mp3/Komonazmuk_Feb_2008_Mix.mp3)

---

### Post by odd1here on 2008-02-26
> The file /lib/modules/2.6.22-14-rt/build/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel

anyone know which package this is?

---

### Post by odd1here on 2008-02-26
okay, i look at code and code says:

or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.22-14-rt/build).

so i run:

./configure --with-cards=intel8x0,mia --with-oss=yes --with-sequencer=yes --with-kernel=/usr/src/linux-source-2.6.22-2.6.22/

it no workie :confused:

so i run:

./configure --with-cards=intel8x0,mia --with-oss=yes --with-sequencer=yes --with-kernel=usr/src/linux-source-2.6.22-2.6.22/


it no workie :confused:

./configure --with-cards=intel8x0,damnit --with-oss=yes --with-sequencer=yes --with-kernel=dir usr/src/linux-source-2.6.22-2.6.22/

it no workie :confused:

./configure --with-cards=intel8x0,tohell --with-oss=yes --with-sequencer=yes --with-kernel=dir, usr/src/linux-source-2.6.22-2.6.22/

it no workie :confused:


./configure --with-cards=intel8x0,notsmartenuff --with-oss=yes --with-sequencer=yes --with-kernel=usr/src/linux-source-2.6.22-2.6.22/



i like ubuntu but sound was easier with regular debian.
i quit linux for long time cuz would rather be a thief than confused.

is ubuntu made confused?

ubuntustudio comes with echomixer which is for echo cards, which makes me think i installed ubuntustudio wrong.
which would then mean there is wrong information everywhere
on installing ubuntustudio into/over/onto ubuntu.


i still like ubuntu, but i lose all confidence an think i should be smart enough to be able to do this.

---

### Post by odd1here on 2008-02-26
i could post IP and you could take over an fix it? :lolflag:

---

### Post by odd1here on 2008-02-26
maybe is command for:

apt-get install Everything..

?whatya think??


-sorry am schizo and crzy-

---

### Post by odd1here on 2008-02-26
in person i am not this way, 

i reach point long ago about interwebs.
my point is:
_i don't care._

became lackadaisical about internet. 
and  ever sense i don't care about spelling grammar puncuation or any kind of etiquette.
future is gone. cuz we are here. and we don't have much going for us now, cuz its all industry driven materialism. with little sense of community...

so

i just fire and fire and fire and fire until i tick off someone to help me. then go on my merry way.

it's all smiles

---

### Post by odd1here on 2008-02-27
okay..

going to assume  this is wrong forum heading.
 i posted in.

or i made no sense at all.

or more than likely i look like a real uncompassionate jerk.

i can't figure this out.

---

