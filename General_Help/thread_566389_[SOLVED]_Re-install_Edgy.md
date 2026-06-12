---
title: "[SOLVED] Re-install Edgy?"
date: 2007-10-03
forum: General Help
---

### Post by squirage on 2007-10-03
Hi,

Does anybody know of a way to re-install ubuntu to try and back track out of a problem?

I have no sound, and alsa says I have no sound device after I tried every fix I could locate.

I did have sound once so I was thinking that starting from scratch my be the only way left to proceed.

I am toying with the idea of just throwing in the LiveCD and going through the install proceedure again. 

I can't seem to find any info or guides, and was just wondering if that was the absolute worst thing I could do.

Thanks.

Sean.

---

### Post by zero-9376 on 2007-10-03
maybe try the live cd if you have sound then use 
lsmod | grep snd
in the terminal to determine what modules/drivers are being used.
dont install just reboot back into your current install and do the same, see if the list is the same.
also how is alsa telling you you dont have any sound device? what do you get from the command 
aplay -l

---

### Post by strabes on 2007-10-03
Why are you using edgy? It was not a very good release. Feisty has been out for 6 months and gutsy comes out in two weeks. You should install a recent version of ubuntu and see if your sound works. Chances are it will.

---

### Post by squirage on 2007-10-03
Hi and thanks for responding,

zero-9376,

From my hard drive,

```
lsmod | grep snd
snd_timer              27529  1 
snd                    66924  1 snd_timer
soundcore              11232  1 snd
snd_page_alloc         12040  0 

aplay -l
aplay: device_list:222: no soundcards found...
```

From the LiveCD
```
lsmod | grep snd
snd_hda_intel   20116  1
snd_hda_codec  164608  1  snd_hda_intel
snd_pcm_oss   47360  0
snd_mixer_oss   19584  1 snd_pcm_oss
snd_pcm   84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm, snd_timer
soundcore   11232  1 snd
snd_page_alloc   11400  2 snd_hda_intel,snd_pcm

aplay -l
**** List of PLAYBACK Hardware Devices****
card:0 Intel [HDA Intel], device:0 HDA Generic [HDA Generic}
Subdevices 1/1
Subdevice #0 : subdevice #0
```

So obviously something in one of my attempted "fixes" really messed things up. I don't remember the links to my other posts about this but I'll try to edit them in or add another post.

strabes,

  I got a CD of Edgy from the Keir Thomas book put out by APRESS. My thoughts were that bugs and support would be all figured out for that version. It has become clear on this forum that almost everything is related to Feisty and many are beginning to look ahead to Gutsy.

  I did not know that Edgy had received any bad reviews. I think I will give Feisty a try.

Thanks for the info.

Sean

---

### Post by squirage on 2007-10-03
I have now installed Feisty and as of yet I don't have sound.

This is what I've done thus far.
```

 lsmod | grep snd

snd_hda_intel          21912  1 

snd_hda_codec         205056  1 snd_hda_intel

snd_pcm_oss            44544  0 

snd_mixer_oss          17408  1 snd_pcm_oss

snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss

snd_seq_dummy           4740  0 

snd_seq_oss            32896  0 

snd_seq_midi            9600  0 

snd_rawmidi            25472  1 snd_seq_midi

snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi

snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              23684  2 snd_pcm,snd_seq

snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

So that looks promising. And then:
```

soundcore               8672  1 snd

snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
```

And then:
```

 aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

  Subdevices: 1/1

  Subdevice #0: subdevice #0
```

Although the device names are not too familiar, at least I have something.

My other sound threads [http://ubuntuforums.org/showthread.php?t=566365](http://ubuntuforums.org/showthread.php?t=566365) and [http://ubuntuforums.org/showthread.php?t=564031](http://ubuntuforums.org/showthread.php?t=564031)

Those show all the things I did to no avail.

Next I took a look at:
```

lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

        Subsystem: Toshiba America Info Systems Unknown device ff01

        Flags: bus master, fast devsel, latency 0, IRQ 21

        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]

        Capabilities: <access denied>
```

And that was as it should be.

The next step was to check for specific drivers with the ALSA project.

They send me here [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
to check for my specific chipset, card.
```

modinfo soundcore

filename:       /lib/modules/2.6.20-16-generic/kernel/sound/soundcore.ko

alias:          char-major-14-*

license:        GPL

author:         Alan Cox

description:    Core sound module

srcversion:     45750F13477CBA5B6F36F46

depends:        

vermagic:       2.6.20-16-generic SMP mod_unload 586 
```

According to this I don't need to recompile the Kernel. This may have been my problem last time.

Typing this:
```

alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

So do I need to load alsa-utils again? I'm not sure what next.

---

### Post by zero-9376 on 2007-10-03
ok well it looks like sound is working to me, maybe you have things muted, sometimes with some chipsets the pcm and other mixers get 'mixed up', i would install gnome-alsamixer (or use just plain alsamixer from command line) and see if anything is muted that shouldn't be

apart from that you may want to try changing the preferences in system-soud to use ESD, well thats what i use and it works when the autodetect doesn't

---

### Post by squirage on 2007-10-04
Hi zero,

  Yes, that is what has been so frustrating. Everything looks like it's there and should be working, but it isn't.

I'm not sure why but alsamixer no longer works:

> 
Code:

alsamixer

alsamixer: function snd_ctl_open failed for default: No such device



The settings in sound preferences are interesting. They are all set to auto detect except for Sound Capture under** Audio conferencing **says Test Sound and Device under **Default Mixer Tracks** says HDA Intel (Alsa mixer).

Of the other settings, aside from autodetect, I have the option to select Si3054 Modem, ALC861VD Analog, ALSA, ESD, and OSS. 

Just for fun I tested all the settings under **Sound Events**. Autodetect, Si3054 Modem and OSS all gave me the Testing Pipeline Window. The first two boxes in the bar are orange but no sound. For ALC861VD Analog, ALSA, and ESD get the warning ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server
```

So I'm not sure what is up. I will try installing gnome-alsamixer and go back and look at my BIOS again, last time I did not see any settings for the sound chip.

I am also thinking of trying to compile the 1.0.14 alsa files again. I assume that those things might have been taken out with the upgrade to Feisty.

The last thing that puzzles me is that I have no alsamixer but in synaptic it shows I have all of the alsa-utils etc installed. Not to mention gstreamer and other things that get mentioned. But I see that the alsa version is 1.0.13, this is why I thought maybe 1.0.14 was taken out by the upgrade.

Sorry I'm rambling here, I just woke up. My thoughts are perhaps I should completely remove all that stuff and then re-install.

But first I'm going, to try and compile 1.0.14 and then double check the BIOS when I reboot.

Thanks again.

---

### Post by squirage on 2007-10-04
ARRGH!  ](*,)

Went through the compilation steps (again) from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and re-booted. While I was compiling I did notice that I started in the wrong directory (i.e. still in home :oops: ) but I corrected that.

Checking out the BIOS, I still don't see any thing to enable the chipset, unless having the System Beep disabled is the problem. I guess I should have tried that for the hell of it.

So I boot up, no sound, and now I'm back to the red symbol on my volume control. And opening the volume control gives:
```
No colume control GStreamer plugins and/or devices found
```

and sure enough in preferences I'm back to having only ALSA, ESD, and OSS.

Now```
cat /proc/asound/card0/codec#* | grep Codec 
```
Returns:```

cat: /proc/asound/card0/codec#*: No such file or directory
```
And ```
alsamixer
```
Still produces:```
function snd_ctl_open failed for default: No such device

```

On the bright side lsmod | grep snd, lspci -v, and modinfo soundcore all seem to return something acceptable.

And I almost forgot ```
aplay -l
```
Returns ```
aplay: device_list:204: no soundcards found...

```

What makes this particularly frustrating for me is that I really do like Linux. I think there is  a lot of great stuff in there and it boggles my mind that something so basic as sound coming out of the speakers should be so hard.

By the way sound does work in Vista, so it has nothing to do with broken hardware. So I'm left with the question, why did sound ever work at all? And secondarily, if I can't get it back following the specific guide for my device type, what the hell do I do?

Okay now I'm just ranting. Sorry.

It's a good thing that I'm self employed, because I would be fired for the amount of time I've spent on trying to fix this instead of being productive.

I'll keep trying. What I lack in talent I make up for in tenacity.

Thanks again.

---

### Post by zero-9376 on 2007-10-04
ok so i found i bug on launchpad and it looks as though some people have had success
[https://answers.launchpad.net/ubuntu/+question/5455](https://answers.launchpad.net/ubuntu/+question/5455)
do you have a /home/yourusername/.asoundrc file, if so apparently deleting that might help

someone on there also points to 
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

your last post is a little confusing, i thought you had already installed fiesty, and you mention not having alsamixer but you report that it gives you alsamixer: function snd_ctl_open failed for default: No such device. Must be the tiredness ;P

---

### Post by zero-9376 on 2007-10-04
yeah its not going to be a bios setting if its working in edgy/vista

whatever you have done has broken it more i think because you have not devices listed with aplay -l which is a step backwards

if you can reboot back into your old kernel/alsa then you should be able to use 
alsamixer -c 0
where the 0 denotes card 0 which you should see when you run aplay -l

---

### Post by squirage on 2007-10-05
Hi zero-9376,

  Sorry to take so long getting back to you.

Yeah BIOS doesn't seem to be it, but Edgy never really worked that well.

I think my oldest kernel is 10, I have to say that it never occurred to me to boot into an old kernel. I'll keep that in mind for next time something goes wrong.

What I was trying to say about alsamixer was that at some point I could type that in and get the mixer panel, now I cannot.

I did some more searching and hit upon another thread that really helped a lot. I then made my own little how to thread based on what I did.

It is over here [http://ubuntuforums.org/showthread.php?p=3482677](http://ubuntuforums.org/showthread.php?p=3482677)

Thank you so much for your help, it greatly reduced my frustration to have some one respond to my plight.\\:D/

---

