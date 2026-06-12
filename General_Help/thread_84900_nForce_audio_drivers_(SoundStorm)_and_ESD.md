---
title: "nForce audio drivers (SoundStorm) and ESD"
date: 2005-11-01
forum: General Help
---

### Post by Teo on 2005-11-01
Hi,
I'm playing guitar and sound with nVidia drivers is much better than with OpenSource drivers so I have to use nVidia's nforce audio drivers (now 0306) :/.
In Breezy after installation of nVidia's driver I can't run ESD server - only OSS works. Without ESD I can't hear any system sounds etc... :/.

My motheboard is Abit AN7 with SoundStorm.

Is it possible to use OSS and OSS only for every single sound source in Breezy?
or
How to run ESD server and OSS nVidia's driver simultaneously in Breezy?

ps. In Hoary ESD server and OSS nVidia's driver works at a same time.

---

### Post by queenorych on 2005-11-01
that's the problem with oss.  Only one sound at a time.  Unless you have hardware mixing as in sblive.  as far as I know nforce does not.  See oss website though.  I think at least the commercial oss does some mixing.

The nforce sound driver from nvidia doesn't support alsa?  Are you sure there isn't a different driver?

If sound quality is important to you, do youself a favor and get an sblive.  Hardware mixing, works great with oss or alsa.  My old machine had an sblive, I hate this nforce4 audio.  Easy to distort (probably amp on board), no hardware mixing (sucks to get no sound to find usually esd has it locked), and no dsp (never used, but I like the feeling of being able to :-))

---

### Post by poptones on 2005-11-01
Nvidia's moherboard sound (ie soundstorm) DOES have hardware mixing - 32 channels of it. In fact. nvidia's sound has all the features (perhaps even more) than an sblive. And frankly, I have never liked sound blaster's products.

The reason you have had bad experiences with the motherboard sound on your system is that the open source drivers suck because nvidia won't release any specs on it. And the nvidia drivers don't work with alsa. 

I would also love to know how to get ubuntu (in my case, hoary) working with nvida's sound system. For me, sound has always been the worse feature of ubuntu.

---

### Post by Teo on 2005-11-01
[QUOTE=queenorych]
If sound quality is important to you, do youself a favor and get an sblive.[/QUOTE]
Can't do. I have had SBLive and I can tell that nForce2's SoundStorm gives better sound quality when recording (that's most important for me) :/.
SoundStorm does do HW mixing.

I'm thinking bout Audigy2 ZS but can't afford yet :(.

---

### Post by Dracontopes on 2005-11-01
Me votes for a how-to on nvidia soundstorm APU :KS:KS:KS:KS:KS (listening to sound from more than one app at the same time)

---

### Post by Teo on 2005-11-01
[QUOTE=Dracontopes]Me votes for a how-to on nvidia soundstorm APU :KS:KS:KS:KS:KS (listening to sound from more than one app at the same time)[/QUOTE]
??
I can listen to sound from more than one app on nVidia's SoundStorm drivers.
I even can record and play sound and listen to Rhythmbox at a same time (Fullduplex - I'm using it when plying a guitar with Gnuitar).

---

### Post by Arcadeoddie on 2005-11-02
Is there way you can show us how?
Please :D

---

### Post by Teo on 2005-11-02
[QUOTE=Arcadeoddie]Is there way you can show us how?
Please :D[/QUOTE]
In Breezy (console):
```
sudo CC=gcc-3.4
sudo export CC
sudo sh NFORCE-Linux-x86-1.0-0306-pkg1.run

```
After installation of nforce audio drivers:
```
sudo gedit /etc/libao.conf
```
change this: default_driver=esd
into this: default_driver=oss

Then go to: "System" -> "Preferences" -> "Multimedia Systems Selector" and set OSS for both.

Now you can do:
```
sudo modprobe nvsound
sudo modprobe nvnet ##when installing nforce network drivers
```

and disable loading ALSA (we don't need it any more coz' nforce audio drivers won't use it):
```
sudo mv /etc/init.d/alsa /etc/init.d/@alsa
sudo mv /etc/init.d/alsa-utils /etc/init.d/@alsa-utils
```
Don't forget to change GCC envoirment back to 4.0:
```
sudo CC=gcc-4.0
sudo export CC
```

Now restart your Linux-box.

ESD disappear but we have OSS and hw mixing.

ps. Use nvmixer

---

### Post by wylfing on 2005-11-02
But the original problem is unresolved -- you won't get any system sounds through OSS. If I knew how to get system sounds, I'd use the nvsound driver too.

---

### Post by Teo on 2005-11-02
[QUOTE=wylfing]But the original problem is unresolved -- you won't get any system sounds through OSS. If I knew how to get system sounds, I'd use the nvsound driver too.[/QUOTE]
YES. That's why I posted this Thread -  I'm asking how to use OSS to play every single sound in Breezy ie. system events.

---

### Post by poptones on 2005-11-03
[i]ESD disappear but we have OSS and hw mixing.

ps. Use nvmixer[/i]

I totally hosed my system yesterday trying to get the oss drivers from opensound.org to work. The installed ok and did in fact do hardware mixing, but none of the applications were able to "mix" with their own volume controls - changing the volume in xine just changed the volume for all the xine apps, xmms and anything else that happened to be open. And when I said "this sucks" and uninstalled the driver it left my machine so completely borked I gave up trying to fix alsa and just reinstalled.

OSS sucks bad. I'm going to put my eggs in the alsa basket until they get gstreamer to actually work as intended. Once that happens it won't matter if you use OSS or alsa, gstreamer can handle the mixing.

---

### Post by RAOF on 2005-11-03
[QUOTE=Teo]YES. That's why I posted this Thread -  I'm asking how to use OSS to play every single sound in Breezy ie. system events.[/QUOTE]
I don't think you can - I think that some of the gnome libraries are hardcoded to use esd.

On the other hand, if you can get ESD to work with OSS...

---

### Post by Dracontopes on 2005-11-03
[quote=Teo]text blabla

ESD disappear but we have OSS and hw mixing.

ps. Use nvmixer[/quote] 
So there is no need to do the other tihngs nvidia describes, like commenting out aliases and making new aliases etc? And the nvmiser settings are not saved: rebooting results in setting up nvmiser again :(

Anyway, sound is working now FINALLY, with ESD. I can listen to Totem en Rhythmbox on the same time. Yay! I din't know what I did, I just reset everything to the defaults and it worked :S

---

### Post by Arcadeoddie on 2005-11-03
Mine works now. Thank you very much and I will add this to my doco's.
Sound is very crackly like and old record player but i will look into this.
Unless someone has the solution

---

### Post by queenorych on 2005-11-03
tao.  Make sure esd is using oss.  You should have package libesd0 installed and not package libesd0-alsa

---

### Post by queenorych on 2005-11-03
Wow you guys are about soundstorm.  I just upgraded my computer from a PIII to an nforce4 SLI and just assumed that the crap for sound I have in my nforce4 is what all nforces had.

---

### Post by Teo on 2005-11-03
[QUOTE=queenorych]Wow you guys are about soundstorm.  I just upgraded my computer from a PIII to an nforce4 SLI and just assumed that the crap for sound I have in my nforce4 is what all nforces had.[/QUOTE]
SoundStorm is in nForce2's with MCP-T South Bridge only - ie. SoundStorm is in Abit AN7.
In other nForces there's some AC'97-like crap :(.

[quote=queenorych]Make sure esd is using oss. You should have package libesd0 installed and not package libesd0-alsa[/quote]
Yey!! At least ESD works with nVidia's OSS drivers in my Breezy. THX A LOT!! :)

---

### Post by _MiniMe_ on 2005-11-08
> SoundStorm is in nForce2's with MCP-T South Bridge only - ie. SoundStorm is in Abit AN7.
In other nForces there's some AC'97-like crap 

Does that mean that with all other boards I can get no hardware-mixing? I have an Asus A7N8X-E Deluxe and the Device-manager says that I have an an "NForce2 AC97 Audio Controller [MCP]"    (not MCP-T)

BUT: in the manual on the Asus driver cd it says:

"MCP-T southbridge integrated audio processor unit + Realtek ALC650 6-channel audio CODEC"  (nothing about "soundstorm")

Can anyone tell me if this chip can do do hardware-mixing? This would be really good to know before I try to install the drivers...

THX

---

### Post by wylfing on 2005-11-08
AC97 is a specification, not a brand or a chip. Realtek is the manufacturer of your audio chip, which conforms to the AC97 spec, and also to nVidia's nForce audio spec. I do believe it should do hardware mixing.

If you're feeling timid, there's little to fear when you're experimenting with this. It's not a "one way" kind of experiment. It's easy to switch back to ESD or ALSA.

---

### Post by poptones on 2005-11-08
Not if you install the drivers from opensound, it isn't. It shoudln't be one way, but as I said their installer totally hosed the sound config on my system and even reinstalling alsa didn't fix it.

---

### Post by _MiniMe_ on 2005-11-08
First of all, thanks for your replies!

> AC97 is a specification, not a brand or a chip
I knew that, I just asked because of the difference MCP <--> MCP-T...

Anyway, I tried it and it works. I can hear music with xmms and can watch a movie with xine. Both with sound. 

But there are also some not-so-good news:

- I can't record anything with the mic. Actually it didn't work before with ALSA, but with OSS (at least sometimes...)
- When I change the volume in xine, it changes the global volume...
- XMMS can't change the volume at all :( 

Is this normal? Can someone give me a hint how to solve that?

Sorry, but I have to say this:
The sound-problems I had were probably the most annoying problems since I've left windows and joined the linux-community. I've managed to solve most of the other problems (with a little help of course...thx to all!) and I'm a big fan of Ubuntu (after trying some other distros). But concerning the sound, there was (and is) always something that didn't work. Imho the current  "linux-sound-situation" really sucks...

---

### Post by poptones on 2005-11-08
What you describe is exactly what I got wiht the "official" opensound drivers from their website. Nice to know it wasn't just me...

Opensound isn't even "open" - it's proprietary and to use it you have to pay for a license or keep reinstalling every few months. I knew better than to think linux would ever get support for some "features" from a proprietary chipset vendor but I bought into it anyway... lesson learned.

Alsa is free, it's open and it works. I think ubuntu is reluctant to embrace alsa because they are behind gstreamer and once gstreamer is better developed it will be able to handle all that stuff in a very competent fashion. Gstreamer is a fantastic technology with great promise. Problem is it's not yet that developed and it probly won't be for a year or more.

---

### Post by _MiniMe_ on 2005-11-08
Ok, I've solved some of the problems. Actually its more a workaround than a solution... I've installed libesd0 so esd now works with oss. Then I configured xine and xmms to use esd. I can change the volume independently now. 

btw: is it safe to uninstall "ubuntu-desktop"??? (It's done automatically when installing libesd0)

The audio-recorder still doesn't work. I've tried to switch the input-device from oss to esd. That gave me the first big crash since I've installed breezy (only reset helped). But there is also good news: Teamspeak-Client works now!! Like the audio-recorder, it worked only once before (with oss as input-device) and then never again. I hope this time it keeps working (I'd still like to know why I could never record sth. with alsa...)

For now there is only Skype left for testing. I'll tell you if it works when I've done it. Maybe one day this thread helps somebody with similar problems...

---

### Post by _MiniMe_ on 2005-11-08
> I think ubuntu is reluctant to embrace alsa because they are behind gstreamer 
That's interesting... I always thought that gstreamer is build upon ALSA and not meant as replacement for it. But actually I don't know much about gstreamer, except that it is too slow when watching movies with totem-gstreamer (on an AthlonXP 2600+). 

btw: what is the difference between oss and the drivers from opensound? I think that there is one, otherwise you wouldn't have installed them...

---

### Post by _MiniMe_ on 2005-11-08
Ok, I've tested Skype and it works!!! Finally i can hear music while talking, now that's really cool...

BUT:

 next problem: the nvmixer forgets all settings after reboot. I found a description in the NVidia readme: [http://download.nvidia.com/XFree86/nforce/1.0-0306/ReleaseNotes.html](http://download.nvidia.com/XFree86/nforce/1.0-0306/ReleaseNotes.html)

it says:
> If you wish to have nvmixer audio settings automatically restored each time the nvsound driver loads, add the following lines to the configuration file:

install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound


and:

> For both 2.4 and 2.6 kernels, you should add the following code to /etc/rc.d/init.d/halt:

if grep -q "\(nvsound\)" /proc/modules && [ -x /usr/bin/nvmix-reg ]; then
/usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1
fi


Problem is, I don't know what configuration file is meant (in the first instruction). They are always talking about /etc/modules.conf or /etc/modprobe.conf. I only know /etc/modules, but that's not the right one I think... 

Maybe someone has already done that???

---

### Post by ThiAm on 2005-11-29
I think I have done somethink like this one week ago...
Just create a config file into /etc/modprobe.d, for instance nvidia.conf.
For more info on the config files type "info modprobe".

---

### Post by _MiniMe_ on 2005-11-29
Ok, I'll try that, thx a lot!

 Do you also know what the file /etc/rc.d/init.d/halt actually does? Or maybe where I can find it in ubuntu? It doesn't exist on my system. Of couse I could create it ( i.e. I would create "/etc/initd./halt"), but I thought maybe there already exists another file that does the same job and I just don't know it???

---

