---
title: "ICE1712 cards do not work with Breezy"
date: 2005-10-15
forum: General Help
---

### Post by drucer on 2005-10-15
Hi,

I just want to report that ICE1712 chipset based sound cards do not work with Ubuntu Breezy Badger. You get audio only from your left speaker and the sample rate is screwed.

Many professional audio cards used in recording studios (like M-Audio) use this chipset.

Note also that ALSA supports this card 100%, so it is in fact a problem with Ubuntu.

---

### Post by speckman on 2005-10-17
i have an maudio 1010 which uses an ice1712.

off of the initial install, i can get sound with esd and alsa.  esd sounds great.  alsa is choppy and unuseable (i need it cause i make music)

---

### Post by reet on 2005-10-17
I have the M-Audio Audiophile 2496. No problems playing sound using alsa after a fresh install. Applied a little "multiple sounds at once" trick as per [this thread]("http://ubuntuforums.org/showthread.php?t=32063") and away I went.

Perhaps you might check all your sound settings before accusing the operating system of a fault?

---

### Post by drucer on 2005-10-17
[QUOTE=reet]I have the M-Audio Audiophile 2496. No problems playing sound using alsa after a fresh install.[/QUOTE]

So, it worked for you perfectly out of the box after a fresh install? Let me be clear, you were able to get perfect sound out of Gnome, Totem mediaplayer and all the other applications?

[QUOTE=reet]Applied a little "multiple sounds at once" trick as per [this thread]("http://ubuntuforums.org/showthread.php?t=32063") and away I went.[/QUOTE]

A _little_ trick? So you were not able to get perfect sound after a fresh install? Your post is confusing.

[QUOTE=reet]Perhaps you might check all your sound settings before accusing the operating system of a fault?[/QUOTE]

I've checked the sound settings several times, but no help. ICE1712 cards have 100% open source drivers, so the way I see it, these cards should work out of the box without any extra steps. I've seen distributions that are able to configure these cards perfectly out of the box - I don't see why Ubuntu couldn't do the same.

EDIT:

Checked out your link - it's pretty ugly hack (software mixing) if you've got ICE1712 chipset based sound card. These cards are capable of doing hardware mixing saving some serious CPU utilisation if configured properly.

---

### Post by speckman on 2005-10-17
My linux guru friend, Brad, came over here and fixed at least some of the problems I was having with this ice1712.  He installed **totem-xine**, replacing **totem-gstreamer**.  This is how I got my ice1712 to work with hoary too.  Actually, I haven't tried out jack yet, so I'm not sure if this is an overall solution.

---

### Post by idn on 2005-10-25
So is the problem with gsteamer? If it works with totem-xine but not totem-gstreamer I would have thought so. Have you managed to get it working?

---

### Post by glenby on 2005-10-27
I have a terratec dmx6 fire  -same chipset.
installed 5.10 from download cd - there is sound sort of.
I installed the codecs etc - tried both xine and gstreamer too.
playback rate is less than half it should be.
go into the alsa mixer and change the internal clock speed doesnt do anything unless you pick the last option - then you get raving chipmunk sounds.

I re-installed from scratch 5.10 from cd - same deal.
the card worked perfectly under suse 9.2

So far I reckon this is the best distro I've seen in terms of neatness and direction (not fully of bloat and rubbish). not being able to use the sound tho is causing me major problems - looking at other distro's.

---

### Post by glenby on 2005-10-27
mplayer works when talking directly to alsa - so does xmms.
I cannot get totem xine to work at all.
I now also have a screwed up volume control.

hmmmm


still working at it.

---

### Post by idn on 2005-10-28
Cool, well let me know how you are getting on, I would prefer to get this card over a soundblaster, but only if I get good quality sound out of it. I wouldnt want to switch to suse :)

---

### Post by StormBlast on 2005-10-28
I have Audiophile 2496 and have a bunch of problems with sound in hoary causes by ALSA's dmix plugin. Now, in breezy, it solved, but gstreamer ALSA output still buggy - same problem, only left channel with crappy sound by default.
I've solved this problem now - open Multimedia System Selector, choose Custom as output and type below:
```
alsasink device=plug:dmix period-size=1024
```
Click Close button.
All gstreamer based apps (Totem, Rhythmbox, Banshee, Quod Libet and so on) sounds ok now. Enjoy!

---

### Post by idn on 2005-10-28
Cool, and the sound is of good quality

---

### Post by GameGod on 2005-10-28
I have the answers to both the questions in the original posts.

I have an M-Audio Revolution 7.1 and experienced both of these problems (it uses ice1724), but a quick googling answered them both.

First, the problem of the audio coming out of only one channel is fixed by simply changing the volume, at least on my card. If I turn up the volume of DAC 1 or 2 using alsamixer or the gnome audio applet, the audio magically comes out of both channels.
Bug in the driver? Yes. Easy to fix, yes. Is it annoying? Not really, just have a little patience and adjust your volume when you boot up your PC, piece of cake. :)

Second problem:
Audio playing back at a funny rate. Fire up alsamixer (or the gnome mixer), and find the "Multitrack Rate Locking" option. Set that to "off" (hit m in alsamixer). Set "Multitrack Rate Reset" to "off" as well...
If you're still having problems with the audio playing back at a funny rate, try playing with those two settings.

Lastly:
I was annoyed by the fact that I couldn't control the volume of both my left and right stereo channels at the same time (*that's* annoying)... So I whipped up a little script to let you do that.
Instructions, etc are [on my site]("http://santoni.ca/albert/linuxtweaks.html").

Enjoy!

(And have a little patience... Linux is a hell of a lot better than it used to be, and you'd be surprised how useful Google is...)

---

### Post by idn on 2005-10-29
Cool thanks for the reply, ok you have convinced me to get an MAudio card :). I have been wanting to venture away from sound blaster for a while. Dont think I will get the surround sound one as I dont think I will use it, I have a really nice stereo amp, and 99% of the time I play music not watch moveis. 

Just out of interest, why do you need a while loop in your script? Cant you just run it once on startup?

Cheers,

---

### Post by glenby on 2005-10-29
glenby here again - 
when I enabled the crappy onboard ac97 audio - things worked much better - still rubbish but better.

I dont think the problem is ubuntu - I have now just installed suse10 - same problem exactly - I think alsa have done something which is being propogated through all the distro's.

some words of help - if your card is ultra slow or super quick, try changing etc/esd.conf
in the defaults add -r 44100 at the end (after nobeeps)
this sets the card rate to 44100 - sounds better.
also alsamixer is handy.

I want to go back to ubuntu *wails*

---

### Post by idn on 2005-11-05
Hey thanks for the info, waiting for the next pay day to get the card :) That sucks, you should report a bus with alsa, you should go to ubuntu! Although I have alwasy liked suse, especially know they are not officially supporting KDE :)

---

### Post by ozverell on 2005-11-09
I've made ```
alsasink device=plug:dmix period-size=1024
``` changes, so Totem playing Ogg now sounds ok. 

But Gnome still sounds through only one channel and every action that causes sound is slowed down. Playing in Gnometris with sound turned on is just insufferable because of lags.

---

### Post by iban on 2005-12-03
I had exactly the same problem. My Audiophile 24/96 worked out of the box with  hoary and doesn't with breezy. The only difference i've seen is in ESD connection. ESD now works directly on ALSA, whereas ESD used to work on OSS-emulation interface. To came back to old system, just add **libesd0** package with synaptic (**libesd-alsa0** will be automaticly removed) . Hope it helps.

---

### Post by Stonekeeper on 2005-12-23
Thanks for the tips guys! I've got a Delta Audio 1010LT card and i had all sorts of odd problems. My biggest problem right now is that the motherboard has a Realtek ALC850 chip that i can't seem to access (I want to use it for VOIP). It's enabled in the bios but I seriously cannot get ubuntu to see it. I checked the modules loaded and I got this:
---------------------------------------
snd_ice1712            56388  6
snd_ice17xx_ak4xxx      4224  1 snd_ice1712
snd_ak4xxx_adda         6144  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              9216  1 snd_ice1712
snd_ac97_codec         72188  1 snd_ice1712
snd_pcm_oss            46368  0
snd_mixer_oss          16128  4 snd_pcm_oss
snd_pcm                78344  4 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_i2c                 5376  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6784  1 snd_ice1712
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  17 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  4 snd
---------------------------------

Is the onboard chip being ignored somehow because the ac97 driver is being used by the 1010LT?

Thanks for any help!

---

### Post by Stonekeeper on 2005-12-28
After a bit more research it would seem the PCI sound modules didn't update with the last kernel version. Anyone else seen this?

---

### Post by pioni on 2006-01-07
Same errors here. My Audiophile 2496 refuses to play sounds in stereo and at correct speed. I'm hearing left speaker only and the sounds are played at half speed. I tinkered with alsamixer a while and got XMMS to play sounds correctly, but now volume controls do not work and all Gnome sounds are always muted. The only working volume control is the Gnome mixer slider in the upper right corner and it's changing volume on the left channel only.

Fresh install of Breezy. Why is this always this hard? :confused: Is there something I could do to fix this or am I forced to use another distro?

---

### Post by firekat on 2006-01-26
I am having similar problems with a Audiophile 2496 as well.  I tried a bunch of what was mentioned to no avail.  I did re-install the alsa file that someone else had replaced with an earlier one.  That early one did not work for me.  Using the custom setting made the right speaker louder than the left (where all the system sounds were coming from) the left did have some output but not in balance with the right.

I tried the "test" button on a number of settings in the multimedia panel.  When I went to the ALSA it started outputting sound equally on both channels with good fidelity but it was broken up with a staccato.  But it was playing much better than previously.

Has anyone gotten any further with all of this?

---

### Post by pioni on 2006-02-18
Has anyone got M-Audio Audiophile 2496 working correctly in _any_ Linux distribution? It has to work somewhere, because every recent distribution seems to have driver for it. I just tried BLAG 30002 and it was a lot worse than Ubuntu. It recognized the card, but could not play _anything_, at any speed from either speaker. 

I'd gladly help, if I knew how. I have a computer on which I can do fresh installs whenever I can, so I'm going to try find a distribution in which this card does work and then try to figure out what Ubuntu is doing wrong and that other distribution is doing right. If you have any clues of what might help, please tell us! 

I know, I probably should buy a card that is properly supported. If I don't find a distribution in which this M-Audio card works, this was be the last product from M-Audio I'll ever buy. But is there a high quality card that is 100% supported under Linux, OSX (both Intel and PowerPC) and Windows, preferrably Firewire or USB 2.0? 24bits and 96kHz, stereo in, stereo out is the minimum.

---

### Post by drucer on 2006-02-19
*Has anyone got M-Audio Audiophile 2496 working correctly in _any_ Linux distribution?*

You bet! M-Audio cards are very well supported under Linux! In fact, M-Audio and RME Hammerfall cards are recommended for Linux pro-audio. Why? Because hardware manufacturers of these cards gave specs to Linux audio developers so they were able to develop ALSA drivers that support these cards 100%. So, this is just a problem with Ubuntu.

StudioToGo! distribution (Debian based) supports these cards out of the box. So does Agnula (Linux audio distribution) and Planet CCRMA (Fedora based audio distribution).

Check out also Ardour (Digital Audio Workstation application) page for hardware recommendations:

[http://www.ardour.org/requirements.php](http://www.ardour.org/requirements.php)

"Audio interface

For high-end use, the RME Hammerfall series and the M-Audio Delta series are both recommended choices. These devices are well-supported under Linux, have excellent hardware designs, and work well in more or less every respect. "

I have M-Audio Delta 66 and enjoy pro-quality audio on my LFS (Linux from scratch) system. Unfortunately I can't do that with Ubuntu. BUT I'm sure future Ubuntu releases will support this card out of the box. It shouldn't really be this hard - this card is 100% ALSA supported after all. We need to see Envy24Control application on Ubuntu.

If you're more interested, I suggest you to read Linux audio mailing list messages. You will see that the majority of Linux musicians use these cards.

---

EDIT: One note - if you are going to try Agnula Live CD - remember to adjust the volume after it has booted, because default volume levels are set to zero.

---

### Post by pioni on 2006-02-19
Thanks for the info, Drucer! I can now confirm that the problem is indeed in Ubuntu, not in the card. I just installed Fedora Core 4 and after all updates, the card works perfectly. On a fresh FC4 install before installing the updates the card was recognized, but not working. I got the same "recognized but not working" result in CentOS 4.2 and BLAG 30002 as well.

Now that I finally verified that the problem is in Ubuntu, is there anything I could do to help fix the problem in Ubuntu? Are there some settings or files I could compare? 

We could get this working before Dapper is released and it'd be great to have this card properly supported in Dapper default install. But before trying to fix this I guess we should find out if it's fixed already. Has anyone tried this card on latest Dapper FlightCD? Did this card work properly in Hoary?

---

### Post by pioni on 2006-02-19
I installed Dapper Drake Flight CD 4 that was released today and same exact problem still exists. Same computer, same configuration, same symptoms. I guess this card has never worked correctly in Ubuntu.

You're absolutely right when you say that THIS SHOULD NOT BE THIS HARD! But, how can we fix it? The card is supported and working in Linux, no doubt about that. The problem is indeed in Ubuntu, no doubt about that either. What I'm starting to doubt is if I can ever get this to work under Ubuntu or am I just forced to use other distributions that do not have this problem. :cry:

---

### Post by pioni on 2006-02-19
Oh well, now it's working a bit better in latest Dapper... Here's how:

1. Open console.
2. Open alsamixer as root
3. Scroll to right (with cursor keys) until you find "Multi Track Rate Locking". Switch that ON by pressing M key. 

Now the sounds are played at the correct pitch and from both speakers. I'm not yet sure if it's in stereo, as I don't have any files I could test it with.

Is it any way possible that this could get fixed before Dapper release?

---

### Post by pioni on 2006-02-19
Well, all this of course doesn't help at all in Breezy. I know, because I've tried. Still, in my opinion, this should be plug and play. It's 2006, not 1996!

---

### Post by monchichi on 2006-02-19
hmm, i've never had problems with my m-audio delta cards in ubuntu.

make sure you set up an .asoundrc and unlock multirate track locking with a mixer.

---

### Post by knalle on 2006-02-19
[QUOTE=monchichi]hmm, i've never had problems with my m-audio delta cards in ubuntu.
make sure you set up an .asoundrc and unlock multirate track locking with a mixer.[/QUOTE]

please post your .asoundrc file, i have this card as well and has crackles and pops

---

### Post by drucer on 2006-02-21
Knalle, check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=132988&highlight=ice1712](http://www.ubuntuforums.org/showthread.php?t=132988&highlight=ice1712)

Someone has posted ICE1712 .asoundrc file contents there.

Pioni, thanks for raising this issue in Dapper forum! Hopefully Dapper will support ICE1712 out of the box.

---

### Post by craig552 on 2006-03-09
I got my Audiophile 2496 working in Breeezy. I used Automatix to install ALSA again. 
[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix)
Audio out is great, haven't tested input yet.

---

### Post by tkiesel on 2006-03-18
Someone had said that the Delta line using the ICE1712 chipset supported hardware mixing.

Not according to [the ALSA Project]("http://alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio").  They don't list hardware mixing for any of the ICE1712 cards.

I still love my Delta 410, despite the (minor) headaches.

---

### Post by longship on 2006-03-30
[QUOTE=knalle]please post your .asoundrc file, i have this card as well and has crackles and pops[/QUOTE]

First, get your .asoundrc working.  Here's a simple one that just works:

```
pcm.ice1712 {
  type hw
  card 0
}

ctl.ice1712 {
  type hw
  card 0
}

```

Of course, if you are using two cards, change card # appropriately.

Also, if you do not have envy24control (in alsa-tools) you aren't going to be able to take full advantage of these cards.  Unfortunately, alsa-tools package is not available in Breezy.  However, you can download the 1.0.9 version from Linux From Scratch as a tarball and compile it.  This is known to work with Breezy.
[http://www.linuxfromscratch.org/blfs/view/svn/multimedia/alsa-tools.html](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/alsa-tools.html)

envy24control gives you access to the internal patchbay and all the mixer controls as well as full control of the S/PDIF configuration and the DACs.

This app works for all ice1712-based sound and may also work with ice1724 cards as well.

Instructions for setting up envy24control to play PCM stuff through HW Out 1 and 2 as a stereo pair.  This means that "H/W Out 1" will be left channel and "H/W Out 2" will be right channel.

Run "envy24control".  You'll be looking at several tabs across the top of the window.
[LIST=1]
[*]Go to "Profiles" Tab - Here we are going to begin a "Listening" profile.
[LIST]
[*]Click on the top Profile, labelled "1".
[/LIST]
[*]Go to "Monitor Mixer" Tab - We're going to configure the card to play PCM sound.
[list]
[*]Set "Left" level on "PCM Out 1" to full *on* and "Right" level to full *off*.
[*]Set "Left" level on "PCM Out 2" to full *off* and "Right" level to full *on*.
[*]Either set all the rest of the sliders to full *off*, or enable the "Mute" buttons on the rest of them.
[/list]
[*]Go to the "Patchbay / Router" Tab where we will route the sound to the correct outputs.
[list]
[*]Under "H/W Out 1" and "H/W Out 2" select "Digital Mix L" and "Digital Mix R", respectively.
[/list]
[*]Go to the "Hardware Settings" Tab where we will configure the card for PCM output.
[list]
[*]Under "Master Clock" and within the "Rate State" box disable "Locked" (button is off).
[*]Also disable "Reset" (button is off) within the same box.
[/list]
[*]Go to the "Analog Volume" Tab where we will set the DAC levels.
[list]
[*]Set both sliders to a level about 2/3 the way up.  You can fine tune these later.
[/list]
[*]Go the the "Profiles" Tab
[list]
[*]Note that Profile "1" is still selected.
[*]Press the "Save active profile" button.  This saves your settings as preset number "1".  Remember, this is your "Listening" profile.
[/list]
[/LIST]

Now, you should be able to play PCM sounds on the card.  You can have envy24control up while you mess with things.  Remember to resave your profile if you make adjustments.

Bear in mind that this card is different than most.  It does not provide amplification, so all the sliders on the "Monitor Mixer" Tab only can attenuate the signal, not amplify it.  That's why I have you put them full on.

Good luck.

---

### Post by samoht on 2006-05-27
@longship: Great :)

The next problem: gnomes mixer-applet can only handle one pcm-device a time but ice1712 splits the stereo-signal in two seperate channels (HWOut 1 / 2).

My solution: create a virtual pcm-device with ALSAs "softvol-plugin"...

asound.conf:
```

pcm.ice1712 {
  type hw
  card 0
  }

ctl.ice1712 {
  type hw
  card 0
  }

pcm.!default {
  type plug
  slave.pcm "softvol"
  }


# softvol - Volume Control
pcm.softvol {
    type softvol
    slave.pcm "ice1712"
    control {
        name "PCM Volume"
    card 0
    }
}


# OSS to softvol:
pcm.dsp0 {
  type plug
  slave.pcm "softvol"
  }

ctl.mixer0 {
    type hw
    card 0
}

```

Now select "PCM Volume" in the applets properties. Ready.

Greets,
Thomas

---

