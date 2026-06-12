---
title: "Hardy with Pulseaudio says no to 5.1"
date: 2008-04-27
forum: General Help
---

### Post by ArtPulse on 2008-04-27
Hey there! I used to listen to music perfectly on ubuntu gutsy with ALSA until I installed Hardy...

... Now I don't know if ALSA is playing, or audiopulse, or what does it do, or mean, the thing is i only have 2 channels: I have no subwoofer nor other 3! >.< btw I have a 5.1 system, that's 6 speakers >.<

Somehow I tricked gnome's audio preferences to use ALSA and apps like Songbird, or sound systems work fine, but some other applications have no configuration (like Last.fm applet for AWN), so they use Pulseaudio, and... and... there's no LFE nor Surround nor any of those knots or sliders at pulseaudio's config, just left-right!! =(

is this a downgrade or what? T_T I can only hear 2 speakers, they are tweeters almost, not speakers! that's why I need the sub woofer so badly! xP
(sub waffle, lol xP)

how can I have 5.1 with pulse audio?

btw i have a Creative SoundBlaster Audigy 2 ZS

Thanks!!

---

### Post by jocko on 2008-04-27
> **ArtPulse said:**
> Hey there! I used to listen to music perfectly on ubuntu gutsy with ALSA until I installed Hardy...

... Now I don't know if ALSA is playing, or audiopulse, or what does it do, or mean, the thing is i only have 2 channels: I have no subwoofer nor other 3! >.< btw I have a 5.1 system, that's 6 speakers >.<

Somehow I tricked gnome's audio preferences to use ALSA and apps like Songbird, or sound systems work fine, but some other applications have no configuration (like Last.fm applet for AWN), so they use Pulseaudio, and... and... there's no LFE nor Surround nor any of those knots or sliders at pulseaudio's config, just left-right!! =(

is this a downgrade or what? T_T I can only hear 2 speakers, they are tweeters almost, not speakers! that's why I need the sub woofer so badly! xP
(sub waffle, lol xP)

how can I have 5.1 with pulse audio?

btw i have a Creative SoundBlaster Audigy 2 ZS

Thanks!!

All application has to have a configuration somewhere. I have no idea where the Last.fm applet stores it's settings, but looking at the [wiki]("http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix") page (footnote 11) it seems like the last.fm applet use gstreamer, which means it looks for it's configuration where all other gnome apps do.
When you set the gnome sound preferences did you set it in both **gnome-sound-preferences** and **gstreamer-properties**? That should take care of all gstreamer apps (which as far as I know are the only ones that does NOT have their own settings).

And as pulseaudio just runs on top of whatever sound system you use (alsa or oss), it should be possible to set pulseaudio to respect your alsa configuration and use your default output, but I guess the default setting in pulseaudio somehow bypasses your alsa config... I guess this should be considered a bug or missing feature in pulseaudio...

---

### Post by ArtPulse on 2008-04-27
not good >.< I've checked on both and everything, everything is set to ALSA...

System sounds (or gnome sounds, let's say) are only using 2 channels... Songbird has no configuration about such stuff i believe, but it worked just fine with 5.1 from the begining.

is there any package I'm missing, maybe? any place where I can check which packages should I have?

---

### Post by jocko on 2008-04-27
> **ArtPulse said:**
> not good >.< I've checked on both and everything, everything is set to ALSA...

System sounds (or gnome sounds, let's say) are only using 2 channels... Songbird has no configuration about such stuff i believe, but it worked just fine with 5.1 from the begining.

is there any package I'm missing, maybe? any place where I can check which packages should I have?

Songbird is also a gstreamer application ([according to this]("http://www.songbirdnest.com/support/#13")), so it should work fine if you set everything to alsa. I don't think your problem is caused by pulseaudio, but perhaps by some alsa configuration.

---

### Post by ArtPulse on 2008-04-27
hm, so where can i edit alsa's config?... though i wonder i'd know what to do if it's a text file xP...

---

### Post by marcusfurius on 2008-04-27
I also had some sound issues with Hardy. What you could try is changing your sound preferences devices to ALSA over the new PulseAudio Sound Server (I think you have already done this?). I did this and it fixed my sound issues. You can do this as follows:
Select SYSTEM-PREFERENCES-SOUND
Now, on the Devices tab, change your devices from PulseAudio to ALSA (or an other one).
Next, edit the ~/.asoundrc file (create it if it doesn't exist): 
```

gksudo gedit ~/.asoundrc
```

Enter the following section: 

```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

This will play the surround output by duplicating the stereo output to all 6 channels (not only the front ones). 

To test it type in terminal: 

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```



Good luck.

---

### Post by jocko on 2008-04-27
> **ArtPulse said:**
> hm, so where can i edit alsa's config?... though i wonder i'd know what to do if it's a text file xP...

That's something I've never been able to figure out completely, but there is one way I know that may work.

**EDIT: Try marcusfurius' idea (above) first.**

The alsa settings are stored in on or two files in hidden your home directory: ".asoundrc" and ".asoundrc.asoundconf" (press ctrl+h to see hidden files).
If you have these files, remove them (or just rename them in case you want to undo this later).
Now open up a terminal and type:
```
asoundconf list
```This will give you the name of your soundcard, which you need in the next step:
```
asoundconf set-default-card *Name_of_your_card_here*
```This will generate new .asoundrc and asoundrc.asoundconf files, which may help you.
Note that I don't know if these will configure your card to use 5.1 sound as default (which I guess is what you want), as my integrated intel card only have 2 analog channels. Reload alsa by:
```
sudo /sbin/alsa reload
```If it works: Congratulations, if not, replace the new config files with the old ones.


** Edit2:** I think I figured out a way to get pulseaudio to respect ALSA settings.
```
 sudo gedit /etc/pulse/default.pa
```
Find this line:
```
#load-module module-alsa-sink
```
Remove the #, save the file and restart pulseaudio by:
```
pulseaudio -k
pulseaudio -C
```
This way pulseaudio uses whatever sound device is set as default in your alsa config instead of just using the hardware directly without any regard for your settings.
(If it doesn't work, just put the # back in front of that line)

---

### Post by ArtPulse on 2008-04-27
I've done everything =( yet... no... the last.fm applet still is using 2 channels... I had to create ~/.asoundrc, btw...

btw! after doing:
```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

... I can now say I have a config problem also xP I can't hear "Rear Right" and "Rear Left" comes out from the Rear Right speaker xP though I've done the correct configuration plugging this way on Windows with the Audigy2 drivers and wizard...

LFE is in the right place ;P

---

### Post by eguevaralopez on 2008-04-27
This might help I think... edit your daemon.conf at /etc/pulse/daemon.conf with your favorite editor. I'll use gedit here... ```
sudo gedit /etc/pulse/daemon.conf
```now look for this line: ```
; default-sample-channels = 2
``` it's near the end. Uncomment it (remove the semicolon) and change it to 6. It should look like this when you're done. ```
default-sample-channels = 6
```
I didnt do any of the fixes you guys talked about, just this, and it worked fine. Hope that does it!

---

### Post by ArtPulse on 2008-04-27
Hey! it's working! =D. Thank you a lot jocko for staying along this thread =) and i bet eguevaralopez's advice was useful too, I tried both (your edit and his advice) at same time so I can't tell, but it works now! =)

Thank you all! ^^ byeee =D

---

### Post by vprasaj on 2008-05-15
eguevaralopez, YES, thats it. Nice and simple. 
Don't forget to restart x.
You get stereo expanded over 5.1 sound system. 5.1 tracks (a/52, ac3) are not effected, so everything is O.K.

To control volume for all 6 channels, go to Volume control-->File-->Configure Device--> Playback:ALSA PCM on surround51:0 (your card) via DMA (PulseAudio mixer)
That did the job. For some reason mute is working just for front speakers, but volume for all.

Compared to my .asoundrc, this is really some improvement. :)

If anyone needs .asoudrc for previous ubuntu versions, this did the job (for non Reltech soundcards section bindings is not needed, I think...)

```

#For ubuntu 7.10 and 7.04
#Put this to file .asoundrc in your home directory
#Dont forget to restart alsa!!!!!
#"/etc/init.d/alsa restart"

# 6 channel dmix - output whatever audio, to all 6 speakers
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,0"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 4096
        }

# Uncomment the following section if you have an ALC655 codec (I have one...). It routes the audio to the correct speakers.
	bindings {
		0 0
		1 1
		2 4
		3 5
		4 2
		5 3
	}

     }

# upmixing - duplicate stereo data to all 6 channels
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }


# 'full-duplex' device for use with aoss
pcm.duplex {
     type asym
     playback.pcm "ch51dup"
     capture.pcm "hw:0"
}
# This is just master for all 6 channels
pcm.softvol {
   type softvol
   slave.pcm "duplex"
   control {
      name "Software Master"
      card 0
   }
}
# :)
pcm.!default {
    type             plug
    slave.pcm       "softvol"
}

# for aoss
pcm.dsp "duplex"
pcm.dsp0 "duplex"
pcm.dsp1 "duplex"


```

---

### Post by syyid on 2008-07-04
> **eguevaralopez said:**
> This might help I think... edit your daemon.conf at /etc/pulse/daemon.conf with your favorite editor. I'll use gedit here... ```
sudo gedit /etc/pulse/daemon.conf
```now look for this line: ```
; default-sample-channels = 2
``` it's near the end. Uncomment it (remove the semicolon) and change it to 6. It should look like this when you're done. ```
default-sample-channels = 6
```
I didnt do any of the fixes you guys talked about, just this, and it worked fine. Hope that does it!

Hi
I'm experiencing the same problem as the other poster (LFE gives me rear speakers saying rear-center :| )
But there is no daemon.conf in the pulse folder, only a client.conf
Also how do I know if I'm using pulse or alsa? (I'm using kubuntu 8.04 x64)

---

### Post by jocko on 2008-07-05
> **syyid said:**
> Hi
I'm experiencing the same problem as the other poster (LFE gives me rear speakers saying rear-center :| )
But there is no daemon.conf in the pulse folder, only a client.conf
Also how do I know if I'm using pulse or alsa? (I'm using kubuntu 8.04 x64)

As far as I know, kde still uses aRts as sound server, not pulseaudio.
So unless you have installed pulseaudio yourself, you don't have it.

---

### Post by chmavr on 2008-07-12
eguevaralopez it worked great!!!thankx a lot man!:):)

---

### Post by pohamala on 2009-06-09
Hello,

I have browsed web and found several threads telling on how to enable surround on Hardy. Well, I haven't managed and I would need help on trouble-shooting.

SW: Hardy (8.04) with latest updates, 64bit
HW: Asus M2N-DH with AMD x2 5200 ATI Radeon 2650

So far I have found the following places where people have made configuration changes
-> /etc/modprobe/alsa-base
-> /etc/pulse/default.pa
-> /etc/pulse/daemon.conf
-> .asoundrc
-> .pulse

I have tried to modify all of these, reboot in between etc. wo any remarkable progress. Alsamixer has only the following controls: Master, Headphone, PCM, Front, Line-in, CD, Microhone, IE958, Aux and Analog Mix. Whatever I try I can't get any rear or surround controls visible. Further, if I try to kill pulseaudio and run that with option -C and then list info, I can clearly see that only front channels are in use even default samples are set to ch6.

So, any advice? What should I do to get for example completely clean table i.e. get rid of hanging configurations? What other files to look that the ones above? Or even better, what to do to get surround working?

BTW HW is working as its working on WinXP side of dualboot.

Br Pekka

PS completely pissed on this sound issue - already struggled 2 months with that.

PS PS one odd thing to mention; PCM volume setting does not work over restart - volume levels are really low after start and if I adjust the up it will be low again after restart.

---

### Post by afrodeity on 2010-07-03
Love this thread. 

Been trying to figure out what is going on with my hardware in Lucid.

Sound periodically disappears and whenever I change any of the profile settings, eg btw analog and digital, I lose the card and have to either kill pulseaudio or reboot. Right now, its gone again, and I will probably regain control after a reboot.

So now I'm looking at the daemon.conf and also the asound.conf (.asoundrc) issues.

Tried an example configuration for Twinkle last nite and the app was working perfectly except for pulseaudio which hated the setup.

Too many variables it seems and me not knowing which are the right ones.

```

aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    Front speakers
surround40:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

My Pulseaudio daemon.conf
```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10
```

The Twinkle example config which worked, but now commented out and pulseaudio stuff added in my attempt to find a happy solution.
```

###################### /etc/asound.conf ##################################
#pcm.!default {
#       type plug
#       slave.pcm "asymed"
#}
#
#pcm.asymed {
#       type asym
#       playback.pcm "swmixer"
#       capture.pcm "mixin"
#}
#
#pcm.dsp0 {
#       type plug
#       slave.pcm "asymed"
#}
#
#pcm.swmixer {
#       type dmix
#       ipc_key 1234
#       slowptr yes
#       slave {
#               pcm "hw:0,0"
#               period_time 0
#               period_size 1024
#               buffer_size 4096
#               rate 48000
#      }
#}
#
#ctl.dmixer {
#       type hw
#       card 0
#}
#
#pcm.mixin {
#       type dsnoop
#       ipc_key 5978293 # must be unique for all dmix plugins!!!!
#      ipc_key_add_uid yes
#       slave {
#               pcm "hw:0,0"
# #              channels 2
#              period_size 1024
#              buffer_size 4096
#               rate 48000
#               periods 0
 #              period_time 0
#       }
#       bindings {
#               0 0
#               0 1
#       }
#}

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

---

