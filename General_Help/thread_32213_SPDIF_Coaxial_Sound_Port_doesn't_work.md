---
title: "S/PDIF Coaxial Sound Port doesn't work"
date: 2005-05-06
forum: General Help
---

### Post by nascent16 on 2005-05-06
I have just installed Ubuntu and one of my top priorities is sound output. I've installed ALSA and it seems to be working alright as my sound card is producing sound through the headphone and speaker jacks, but my SPDIF digital out port does not work. This is a problem as this is how I get surround sound from my computer to my stereo. Does anybody know how to get sound out of a digital out port?


Soundcard: 
Integrated onto ASUS P4C800 Deluxe, ALSA mixer says its a Intel ICH5 card with a Analog devices AD1985 chip.

I believe I have successfully set up ALSA as the base layer with OSS emulation and ESD running on top of it too. I don't understand all of it, but I followed the how-to on this forum and got everything over to ALSA, but still no sound out of the digital out.

Let me know if there's any other information you might need.

Thanks,
Justin

---

### Post by nascent16 on 2005-05-06
I found a solution to this problem. On sound cards with multiple outputs there is apparently a card number and a device number. In the sound How-to, the code in the /etc/asound.conf is set to device 0. On my particular system it was actually supposed to be device 4. I found this by typing
```

 aplay -l

```
in the terminal. As you can see the first device is device 0, but my digital out is device 4. So in /etc/asound.conf i changed
```

pcm "hw:0,0"

```

to

```

pcm "hw:0,4"

```

and that fixed all my problems.

This post should probably be included with that how-to, but I don't think I can move a thread once I've created one. 

Justin

---

### Post by DancingSun on 2005-08-31
What kind of soundcard to you have?

I have a on-board Realtek ALC850 CODEC on a nForce4 Ultra chipset motherboard.

I've been trying to get the SPDIF out to work, but so far unsuccessfully.  My SPDIF output connection is an odd one.  It looks like a regular 3.5mm jack, and it is used for line-in devices while also acting as a digital output connection.  I bought both a 3.5mm mono and a stereo jack to coaxial phono jack converter, but it doesn't seem to work, I get no sound from the speakers and the dolby digital light on my Altec Lansing speakers did not turn on.

---

### Post by KFausBN on 2005-09-11
Hallo, 
I also have had problems with my spdif.
Now I have something like a solution, cause of this thread.
Possible, someone has the same Problem:

GA-7N400 (nForce2 with Realtek ALC650)
Sound only by speaker no sound by optical spdif (but light on).

After I read in this thread about, 
> pcm "hw:0,0"

I changed 
> pcm "hw:0,0"
to
> pcm "hw:0,2"
now every sound goes to spdif.

Still vlc wrote
> [00000245] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
[00000257] alsa audio output error: write failed (Broken pipe)

but it works fine :-)

My current .asoundrc in my home directory:

[INDENT]> pcm.nforce-hw {
    type hw
    card 0
}

pcm.!default {
    type plug
    slave.pcm "nforce"
}

pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,2"
        period_time 0
        period_size 1024
        buffer_size 4096
        rate 44100
    }
}

ctl.nforce-hw {
    type hw
    card 0
}
[/INDENT]

Hope this will help (cause I need hours for this change of Number).

Greetings
  Karsten

---

### Post by chipito on 2007-05-25
THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU 

I WAS GOING MAD WITH THIS ONE TOO !!! :popcorn: :popcorn:

i have a DFI LANPARTY NF4-SLI-DR Deluxe with NVIDIA CK804 and was having the same problem (ubuntu 7.04): the sound was only playing thru spdif in TOTEM player, and nowhere else

so, just got to my home dir and edited .asoundrc like KFausBN said and it worked RIGHT AFTER I SAVED THE FILE !!!!

i was searching all over the net for about 3 days to a total of 10 hours and finally got a solution thanks so much, now everything works 

i was thinking that it was something with the pcm "hw:0,0" part, because the SPDIF exit is on 0,2 , but i didnt know where to edit it

well, gotta go hear some mp3 now on xmms ;)

---

### Post by zatmenie on 2007-08-08
This all sounds exactly like my problem, and I'm really keen to try your solution, but I can't for the life of me fine the "asoundrc" config file that you spoke of in my home directory or anywhere else!

:confused:

---

### Post by etitor on 2007-08-09
> **zatmenie said:**
> This all sounds exactly like my problem, and I'm really keen to try your solution, but I can't for the life of me fine the "asoundrc" config file that you spoke of in my home directory or anywhere else!

:confused:

The file name is not "asoundrc" but ".asoundrc", with the single dot as the first character. This kind of "dot files" are meant to be less visible to the user (for example, in order to see them in Nautilus you have to turn on their visibility by typing Ctrl+H).

---

### Post by zatmenie on 2007-08-10
Thanks for the tip. But I did realise that it should be an invisible file (or folder?). I just can't find it.  guess I need the exact path. I'm running Feisty Fawn 7.04.

---

### Post by etitor on 2007-08-11
> **zatmenie said:**
> Thanks for the tip. But I did realise that it should be an invisible file (or folder?). I just can't find it.  guess I need the exact path. I'm running Feisty Fawn 7.04.

Don't worry then. ALSA is supposed to be functional without any .soundrc file, so you may well have to create it from scratch if it doesn't exist yet.

Do you want to be sure whether it already exists or not? Type this in a terminal:

```
ls ~/.asoundrc
```

The shell will tell you one of two things: the name of the file (if it exists) or a warning message (if it doesn't).

---

### Post by Spartan.II.117 on 2007-08-11
can someone post the contents of that file? i need to create one but when i just supply the hw:0,* it breaks alsa

---

### Post by zatmenie on 2007-08-13
Well that definitely explains why I couldn't find it - it doesn't exist. Any advice on how to create it would be greatly appreciated.

---

### Post by Spartan.II.117 on 2007-08-13
new versions of alsa dont need it unless you want "advanced features". this link may have one that will work for you: [http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo](http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo)
or you can try piping data directly to your spdif using your program sending to alsa 0,1

---

### Post by zatmenie on 2007-08-13
Well I definitely feel like I'm making progress, but still can't quite get there. I'm using the motherboard sound device which has S/PDIF output (that works fine in Windows). aplay -l gives the following information...
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Any advice on how to configure that example ALSA configuration file on [http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo](http://www.mythtv.org/wiki/index.php/DigitalSoundHowTo) for this setup?
Or better yet, any simplier way to go would be helpful too.

---

### Post by Spartan.II.117 on 2007-08-13
is that the entire printout for aplay -l?

---

### Post by zatmenie on 2007-08-13
Yes

---

### Post by Spartan.II.117 on 2007-08-14
that only shows an analog output:  "card 0: NVidia [HDA NVidia], device 0: **ALC880 Analog [ALC880 Analog**]" i would do some reasearch on the nvidia board and see if kernel modules need to be loaded first

---

### Post by zatmenie on 2007-08-14
I was afraid of that. Compiling software and finding kernel modules is coming to the limits of my expertise in Ubuntu ](*,)

---

### Post by Spartan.II.117 on 2007-08-14
same here, just compile as much as you can find out about your on-board sound card and put it into google with ubuntu first, if you need more help, post all the info here and I'll see what i can find.

---

### Post by zatmenie on 2007-08-15
OK, well thanks for your help. For now I'm going back to analogue (which works fine in 8 channels). I wish I had more time to work on this. :mad:

---

### Post by klemens on 2007-08-25
guys you are the best!

I have an Audigy 2 ZS platinium pro and had also probs with spdif not working.
I used the asoundrc posted before and changed a few thinks as follows

pcm.Audigy2-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "Audigy2"
}

pcm.Audigy2 {
type dmix
ipc_key 1234
slave {
pcm "hw:0,4"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

ctl.Audigy2-hw {
type hw
card 0
}

Hope it will help others 2.

Important is that my .asoundrc file wasn't in /etc/.asoundrc but in my /home/"your home folder"/.asoundrc without the config. In this document is a link 2 asoundrc.asoundconf delete this line and add it there.

---

### Post by vivichrist on 2007-09-13
OK my .asoundrc looks nothing like that. And I have an .asoundrc.asoundconf 
not much in the .asoundrc:

[HTML]# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/blabla/.asoundrc.asoundconf>[/HTML]

But the asoundrc.asoundconf looks like:

[HTML]# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card CK804
defaults.ctl.card CK804
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off[/HTML]

what can I do here?

---

### Post by nosegoblin on 2008-03-15
> **nascent16 said:**
> 
Soundcard: 
Integrated onto ASUS P4C800 Deluxe, ALSA mixer says its a Intel ICH5 card with a Analog devices AD1985 chip.


Let's bump this old thread as I've been fighting the whole day with this same issue now and have the exact same motherboard as you. So far I have only achieved to play music with xmms through coaxial spdif but nothing else. VLC keeps my 5.1 speakers silent all the time and the funny thing is that the Yamaha home theater amplifier keeps blinking between the digital/analog sign over and over again and the 6 speaker signs blink simultaneously on and off. When I view the messages from the VLC while playing a video file with AC3 sounds, it prints the following message over and over again as long as I keep the video playing:
> alsa debug: recovered from buffer underrun
main debug: audio output is starving (258043), playing silence
main debug: audio output is too slow (-55047), trashing 32000us
main debug: audio output is too slow (-87028), trashing 32000us
main debug: audio output is too slow (-119024), trashing 32000us
main debug: audio output is too slow (-151022), trashing 32000us
main debug: audio output is too slow (-183020), trashing 32000us
main debug: audio output is too slow (-215017), trashing 32000us
main debug: audio output is too slow (-247015), trashing 32000us
main debug: audio output is too slow (-279013), trashing 32000us
main debug: audio output is too slow (-311011), trashing 32000us
main debug: audio output is too slow (-343008), trashing 32000us
main debug: audio output is too slow (-375006), trashing 32000us
alsa debug: recovered from buffer underrun


Could you or somebody else help me with this? I have read through many different guides in the Internet but I haven't yet found the st00pid n00b edition which would solve my issue. :) Anyways, currently my system status is as follows:

> 
$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #
This I believe tells that the device 4 is the one I'm trying to get to work. I have also verified that the IEC958 is enabled from the alsamixer, which by the way messes the music in xmms pretty bad if i change the IEC958 playback source from AC-link to A/D converter. 

The home/xxx/.asoundrc file is as follows and probably not configured correctly:
> pcm.card0 {
    type hw
    card 0
}

pcm.!default {
type plug
slave.pcm "card0"
}

pcm.card0 {
type dmix
ipc_key 1234
slave {
pcm "hw:0,4"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

ctl.card0 {
    type hw
    card 0
}


Any help is appreciated as I'm running out of ideas (and nerves).

---

### Post by RaZoR1394 on 2008-03-22
I have problems with this as well. I have a DFI lanparty NF4 Ultra-D with a Karajan 7.1 audio module. I've added the ~/.asoundrc file with the contents provided in the beginning of the first thread by nascent16. I've also connected the coax cable from the Karajan module SPDIF coax to my Pioneer receiver's COAX 1 (DVD/LD). I'm simply not getting any sound at all from the receiver. Both the Karajan module and the Pioneer receiver works fine otherwise. I've tried several apps; Mplayer, Totem, VLC and Rhytmbox with different kinds of sources (x264/mkv, xvid/avi, mp3, mp4/avc, etc) and none works. I have an Audigy 4 as well and have blacklisted It's module and the only visible soundcard is the CK804 (Karajan 7.1). I've tried cranking up everything in alsamixer and also tried different switches with no results.

edit:

Even if I do get sound through my receiver I'm wondering if I will still be able to hear everything or if I'm just better of with my Audigy 4 with analogue S750 speaker set.

---

### Post by nosegoblin on 2008-03-23
Some status update (Like anybody would care :rolleyes:) 

I'm still trying to find what is wrong but I have made some progress and I believe my current sound issues have something to do with VLC. I have tried loads of different configurations in the past few days and finally I removed the .asoundrc file and completely removed all alsa files with synaptics package manager and reinstalled them back after a reboot (except the .asoundrc that I do not currently have at all). Now I'm in the following situation with different progams:

XMMS: 
Options > Preferences > Alsa 1.2.10 output plugin [libALSA.so] selected as output plugin and it is configured to use hw:0,4 as the audio device and "use software volume control" is enabled. After this MP3s could be played through the SPDIF link. 

mplayer: 
 With the following commands I'm able to play videos with 5.1 sounds:
mplayer testmovie_ac3.avi -ao alsa:device=spdif -ac hwac3 -vo x11 


VLC:
Playing the same movie with VLC with Audio > Audio device > "A/52 over S/PDIF" selected will make my Yamaha amplifier flipping between pcm/digital constantly but and all I can hear is a loud click every now and then (Maybe once in minute or so). If I change the audio device to Stereo, the sounds can be heard but it is not 5.1. It's now only in stereo.

---

### Post by nosegoblin on 2008-03-23
I'll continue my monologue just in case somebody else finds some use for my findings. There actually was something wrong with the VLC and instructions fixing this issue can be found from [http://forum.videolan.org/viewtopic.php?f=13&t=34083&st=0&sk=t&sd=a&start=30]("http://forum.videolan.org/viewtopic.php?f=13&t=34083&st=0&sk=t&sd=a&start=30") . Now my audio issues have turned another way around though. Now only the ac3 sound works and all other remain silent everywhere. For example I'm not able to play MP3s with XMMS anymore. I'll continue my researches.

---

### Post by wavesound on 2008-05-18
Hi All
I have the same problem here on an HP box with vista on it.
Spdiff works in vista but no in Ubuntu 8.


I get this on testing the digital device:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.


This on fist boot.
Any ideas?

Cheers
Bob

---

### Post by learnincurve on 2008-05-28
There's something weird with the nf4 sound devices. I have to set my output device to analog to get s/pdif output. I think the hw output devices must be switched somewhere, as analog is hw:0,0, whilst digital should be 0,2 .

I discovered this completely by accident after banging my head on the wall for ages trying to get didgital out to work from the 0,2 device.

Just in case this helps anyone :-)

---

### Post by ferdies on 2008-06-25
Hope someone can help me...Been trying to solve problems for days but to no avail.

I have posted in mythtv and Linuxmce but no help has been offered. Hopefully, you guys can help me.

I have no sound on Live TV...Other features of Linux MCE like watching DVD, music do have sound.

I already followed some of the instructions from these sites: 
[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound)
[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF)

Since I am using Digital Coax/SPDIF for my sound system (solved this problem based on this [http://forum.linuxmce.org/index.php?topic=5539.0](http://forum.linuxmce.org/index.php?topic=5539.0))


Some details:
linuxmce@dcerouter:~$ uname -r
2.6.22-14-generic

I have this output:
----------------------
linuxmce@dcerouter:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
---------------------------

linuxmce@dcerouter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
--------------

Any idea on what to put in the MythTV frontend?

On Mythfrontend Utilities/Setup->Setup-General go to the Audio page and set your audio device as
 Audio output device        = ALSA:default
 Passthrough outputdevice   = default
 Enable AC3 to SPDIF passthrough   check
 Enable DTS to SPDIF passthrough   check


My .asoundrc in /home/mythtv contains the following:
-----------
cm.IntelHDA-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "IntelHDA"
}

pcm.IntelHDA {
type dmix
ipc_key 1234
slave {
pcm "hw:0,1"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

ctl.IntelHDA-hw{
type hw
card 0
}

----------------------


I also have asound.conf in /etc/
---------------
pcm_slave.convert48k {
        pcm "spdif"
        rate 48000
}

pcm.spdif_playback {
        type plug
        slave convert48k
}

pcm.asym_spdif {
        type asym
        playback.pcm "spdif_playback"
        capture.pcm "plughw:0,1"
}

pcm.asym_analog {
        type asym
        playback.pcm "plug:dmix"
        capture.pcm "plughw:0"
}
pcm.!default asym_spdif
--------------


My sound in /etc/modprobe.d contains:

----------
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0
--------------------

Please advise if I still need anything or I am overdoing it.  I need to have sound for my live TV in MythTV. Thanks.

---

### Post by OmeuNOME on 2008-07-05
hi!

I have the same problem, and solve it editing the file alsa-base in /etc/modprobe.d and add "options snd-hda-intel position_fix=1 model=auto" in the bottom of the file.

do in terminal:

> sudo gedit /etc/modprobe.d/alsa-base

add in the bottom:

> options snd-hda-intel position_fix=1 model=auto

save and in the terminal:

> alsa force-reload

now, execute in terminal

> alsamixer

unmute devices and test the sound 


hope it help other users ;)

---

