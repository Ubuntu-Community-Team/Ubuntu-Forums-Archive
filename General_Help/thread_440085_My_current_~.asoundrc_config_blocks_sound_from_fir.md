---
title: "My current ~/.asoundrc config blocks sound from firefox"
date: 2007-05-11
forum: General Help
---

### Post by LuisGMarine on 2007-05-11
Hello guys,

I got this wonderful ~/.asounrc from a guy in the #alsa channel, the purpose of this ~/.asoundrc config is to get my onboard nvidia sound card to produce software mixing + 5.1 surround sound speakers.  However , since upgrading to this, I've noticed that this blocks my sound from firefox, specially flash.

I've done everything out there that I think is humanly possible to get aoss working with firefox, but like I said to no avail.  So I was wondering if a more experienced user, here can maybe look at this ~/.asoundrc  config and figure out why its blocking sound from firefox.  Also keep in mind that when I use a default ~/.asoundrc ( nothing but a blank file ) I get sound from firefox, but it flickers.  The only decent sound that I get is when I run firefox as root, and that seems to fix all the sound problems that my regular users has.  Also when I create a new account, with all default setting, my firefox runs like a charm.

All I'm really looking foward from this is to get 5.1 surround sound (payed close to about $200 dollars for these speakers for them not be used ), and at least get the sound working in firefox without it flickering.  I'm not so concerned about dmixing, but I guess that would be a nice thing to have .... in the long-run.

Here is my config:
```
#This asoundrc is for snd_intel8x0 based cards. 
#It will allow the following:
#
#	upmix stereo files to 5.1 speakers.
#	playback real 5.1 sounds, on 5.1 speakers,
#	allow the playback of both stere(oupmixed) and surround(5.1) sources at the same time.
#
#
#Certain codecs for this card need certain tweaks
#Please run 'head -1 /proc/asound/card0/codec97#0/ac97#0-0' to find out your codec
#Read any codec specific comments throughout this file.
#
#
#Please try the following commands, to make sure everything is working as it should.
#
#	To test stereo upmix : speaker-test -c2 -Ddefault -twav
#	To test surround(5.1): speaker-test -c6 -Dplug:dmix6 -twav
#
#
#It may not work out of the box for all cards. If it doesnt work for you, read the comments throughout the file.
#If it still doesnt work with your setup, please speak to me (wishie) in #alsa on irc.freenode.net

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

# Uncomment the following section if you have an ALC655 codec. It routes the audio to the correct speakers.
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

# change default device:
pcm.!default {
     type softvol 
     slave.pcm "duplex"
	control {
		name "Software Master"
		card 0 
	}
}

# for aoss
pcm.dsp "duplex"
pcm.dsp0 "duplex"
pcm.dsp1 "duplex"
```

---

### Post by marsm on 2007-06-02
Sorry, I don't know a lot much about this matter, but maybe this helps:

[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Firefox.2C_Mozilla.2C_RealPlayer.2C_Skype_.26_Co](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Firefox.2C_Mozilla.2C_RealPlayer.2C_Skype_.26_Co)

You might want to ask about this issue over at #gentoo, the folks there usually are very knowledgable.

*Push*

[You magically solved my '_No_ video/audio player is playing _any_ file for _any_ user'-problem with this magical line: *apt-get vlc-plugin-esd mozilla-plugin-vlc* as mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=428134]](http://ubuntuforums.org/showthread.php?t=428134])

---

