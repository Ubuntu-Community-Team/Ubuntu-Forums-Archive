---
title: "hello - a problem with edirol ua 4fx usb device"
date: 2008-01-16
forum: General Help
---

### Post by bobbyk on 2008-01-16
hie all. i read all the posts on this matter but still i cant figure out whats wrong. i m working with ubuntu 7.10 in hebrew. i have an edirol ua 4fx usb sound card. i m trying to make it work so i can record stuff. when i hook it in the computer recognizes it - in syslog and in the sounds preferences. still' when i try to test it it doesnt make any sound - i hooked up a guitar to it but no good. i switched off the advanced driver on the device as written in a different ubuntu forum post but no good. maybe i m doing something wrong. if any one can help me online or via mail please let me knpw.
my msn - [email]haruvchik@hotmail.co.il[/email]

also - i have a creative zen touch mp3 player - icant find a driver for it. any advice?

roee harush

---

### Post by m.letcher on 2008-03-23
Re: Record music with Edirol-Roland UA-4FX USB sound card?? 

--------------------------------------------------------------------------------

I have the same question about getting Ubuntu recognizing the external UA-4FX box for midi in/out. I also use it as a second sound card and feed the internal Realtek card out through an external mixer to drive the stereo rig via the UA-4FX. My midi gear audio also routes into the mixer then the UA-4FX where the PC can record it directly via the USB. I'm not that familar with ALSA so it may not be too difficult. I also have a MOTU/USB micro-lite multi-port midi router that I'd like to drive as well since thats what I direct the sequencers out to to drive the external synths.

Sorry that this isn't an answer but rather a follow up question.

There was a thread on this back in 2006, but it didn't appear to have a solution.
[http://ubuntuforums.org/showthread.php?p=4573468](http://ubuntuforums.org/showthread.php?p=4573468)

---

### Post by karloskar on 2008-03-28
Have you tried to uncheck the "Advanced driver" option on the left side of the box?
That did the trick for me while using 7.10.

---

### Post by m.letcher on 2008-04-02
I'll try this today. Thanks very much. Yes the advanced switch was enabled, but not now.

---

### Post by m.letcher on 2008-04-04
I've been looking into this on another thread as well but did want to followup.

[http://ubuntuforums.org/showthread.php?p=4651540#post4651540](http://ubuntuforums.org/showthread.php?p=4651540#post4651540)


Re: Record music with Edirol-Roland UA-4FX USB sound card?? 

--------------------------------------------------------------------------------

Audio appears OK, though apparently the mode switch on the box itself needs to be in 'normal' ( not 'advanced' ) and power cycled. This is reported to disable the midi, but didn't for Vista. I don't have it getting recognized as a midi device yet. I saw some discussion that Gutsy snd-usb-audio has issues with 'slow' USB1.1 interfaces but that these are addressed with Hardy so I'll wait for release later this month.

"Supported" is kind of an open call for me to date, until I play with the audio somemore.There is a nice ALSA wiki page for the UA-4FX with suggestions for advanced mode.

I don't expect to find any help with a MOTU micro-lite ( USB to Midi IO ) box though it drives my sound modules. Too bad for MOTU, since I really like the UbuntuStudioAudio package and will probably finally shift from Sonar/Acid. I'll probably look for a ALSA compatable VST wrapper and go with my soft synths. 

Thanks for suggestions and recommendations.

---

