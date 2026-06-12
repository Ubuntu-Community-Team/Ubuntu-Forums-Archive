---
title: "Microphone not working in 7.04 Feisty Fawn"
date: 2007-07-19
forum: General Help
---

### Post by PaulDazzling on 2007-07-19
I had problems getting the Microphone to work, but it now does for Skype.  Thought I would post this in case it helps others.

I have standard Ubuntu 7.04, head phones and microphone plug into sound card.

Still can't get the microphone to work in the "Sound Recorder", but that can wait.

To get the microphone working in Skype

Right Click on the Volume icon, 
Choose option 'Open Volume Control'
_In Volume Control_
Select Edit>Preferences

_In Volume Control Preferences_
Tick the item 'Capture' so that it is on.
Press Close

_In Volume Control_
On the Recording Tab make sure that Capture is not muted (no cross on the microphone) and the sliders are near the top.

Close the Volume Control.

_Back in Skype_
get to the Options screen.  (crtl+O)
I had to change the Sound In/Out/ringing  settings from default to SB Live 5.1 (hw:live,0).
When I did this the test sound and test call both worked fine.  Sound and Microphone.

Hope this helps

---

### Post by Lazarenko on 2007-07-20
Hello, dude. Thanks for advice! That was really hard to find out about capture :-D
I got my mic working in Skype... Skype is only I need the mic for... but I still can not get good sound quality. I made a test call... and I heard only some crap... real noise. Actually, in Windows it worked very good, sound card is not so bad. I am out of Microsoft ****, I quit...but I really need to talk in Skype, especially for business. I did not find solution in Google. I am just wondering if you have some news? How to improve sound quality? Please help!

---

### Post by Lazarenko on 2007-07-21
Hey, I played also with "Input Source", selected "Mic", to ensure only mic is my input source and turned off boost. It now works much better than in windoz. He-he. I love Linux!

---

### Post by thesoothsayer on 2007-07-21
My microphone suddenly stopped recording. I have a AD1986A chip and it was working fine on Feisty, at least until last weekend. 

Suddenly, I couldn't get it to work today. When I try it in Skype, I get a clicking sound after the opposite side answers the call and all sound functionality (including playback) dies. I can hear the dialing and ringing before that. Playback only works again after removing and inserting the sound drivers modules after it stops working in Skype. 

Sound recorder, krecord and Audacity both draw blanks, with sound recorder giving an error message "Your audio capture settings are invalid. Please correct them in the Multimedia settings." Audacity has no error message but doesn't record anything either. krecord gives the following message:
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Setting "mic boost" to max only produces a static sound most of the time. Sometimes, I can hear a faint echo in the headset if I speak into the mic loudly but usually there's nothing with no amount of shouting or tapping on the mic of any help.

Recompiled the latest Alsa RCs but no joy.

Anyone experienced the same thing recently? Or have any suggestions for me to try?

Edit: Just wanted to say I tried suggestion from #1 but that doesn't seem to do anything for me.

Edit2: Just found out that the latest stable release from alsa were out a month ago. Recompiled and now audacity can record but the rest are giving me the same problem as before and after skype crashes the sound, recording stops working until a reboot.

---

### Post by thesoothsayer on 2007-07-22
Got my sound working properly again with recording and all. 

Configuration is posted in this thread.
[http://ubuntuforums.org/showthread.php?t=314383&highlight=feisty+sound&page=2](http://ubuntuforums.org/showthread.php?t=314383&highlight=feisty+sound&page=2)

---

### Post by b.m on 2007-07-22
I have a similar problem.

After installing Feisty (empty disc, no upgrades, plain 7.04 disc, with up-to-date upgrades), everything worked fine except for the microphone. Believing that it had something to do with my onboard audio, I disabled it (on an Asus P5B Deluxe) and installed a standard Soundblaster Audigy 5.1. 

My audio quality is much better, BUT no microphone yet.

On the volume control I set evrything on playback to max volume, on recording I have "Line In" unmuted, on switches, IE598 is NOT checked, and on Options, "Shared Mic/Line in"  is set to Mic.

With these settings, I can hear good microphone feedback.

Key disablers of microphone feedback:
* muting "capture" on Playback (obviously)
* selecting "microphone" instead of "Line In" on the Recording tab will drastically reduce the audio quality, but I still get feedback
* checking "IE598" on "switches" tab will completely mute it
* changing "shared Mic/Line in" to "line" from "mic"  will also mute it.


Even though I can get microphone feedback, I had no luck in recording audio with any application (sound-recorder, Audacity, Sound Recorder, arecord), nor with Skype (which is my goal).

I have been going back and forward on this one for two weeks, I am completey out of ideas. Any light?

thanks!!

---

### Post by bach on 2007-07-23
I have the same problem. My microphone does not work with Skype, even though I get microphone feedback through the speakers. Hints and suggestions are welcome. (I am running Ubuntu 7.04 and I have already played with alsamixer.) Thanks.

---

### Post by aswinms on 2007-07-24
> **PaulDazzling said:**
> I had problems getting the Microphone to work, but it now does for Skype.  Thought I would post this in case it helps others.

I have standard Ubuntu 7.04, head phones and microphone plug into sound card.

Still can't get the microphone to work in the "Sound Recorder", but that can wait.

To get the microphone working in Skype

Right Click on the Volume icon, 
Choose option 'Open Volume Control'
_In Volume Control_
Select Edit>Preferences

_In Volume Control Preferences_
Tick the item 'Capture' so that it is on.
Press Close

_In Volume Control_
On the Recording Tab make sure that Capture is not muted (no cross on the microphone) and the sliders are near the top.

Close the Volume Control.

_Back in Skype_
get to the Options screen.  (crtl+O)
I had to change the Sound In/Out/ringing  settings from default to SB Live 5.1 (hw:live,0).
When I did this the test sound and test call both worked fine.  Sound and Microphone.

Hope this helps
got it.. "Capture" that's the most important thing.. thanks a ton paul.. cheers!

---

### Post by 11touche on 2007-07-27
Thanks a LOT!
Got Line-In to work on my old SBLive! on Audacity
That "capture" thing was the key. 
GRRREEATT!! :P :guitar:

---

### Post by gustavosenise on 2007-07-27
Hello fellows,

My microphone still doesn't work! I don't know what else to do!
I've changed everything was suggested!
Any ideas, please?

Thanks in advance!
:)

---

### Post by ugm6hr on 2007-07-27
> **gustavosenise said:**
> Hello fellows,

My microphone still doesn't work! I don't know what else to do!
I've changed everything was suggested!
Any ideas, please?

Thanks in advance!
:)

Post the ouput from:
```
amixer
```

And post a screenshot(s) of the controls with:
```
alsamixer
```

If your sound card works (i.e. you can hear sound), and there is no hardware fault with the microphone, it will almost certainly be an issue with the Capture setting.

---

### Post by gustavosenise on 2007-07-27
amixer :

Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [on]
  Front Right: Playback 65 [100%] [30.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [off]
  Front Right: Playback 65 [100%] [30.00dB] [off]
Simple mixer control 'Aux-In',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 35 [100%] [35.00dB] [on]
  Front Right: Capture 35 [100%] [35.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'iSpeaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 65
  Mono: Playback 0 [0%] [-35.00dB] [off]
______________________

alsamixer: attached!

_____________________

My sound card seems to work fine and my Capture setting seems to be ok!!

Thanks for your help!

---

### Post by ugm6hr on 2007-07-27
Couple of thoughts... but it is going to be trial (and error) I'm afraid:

Have you tried changing Input Source to Mic (instead of Front Mic)?

The amixer output suggests that Mic is muted (off), but alsamixer screenshot shows unmuted... is this true, or did you change the setting between the 2 commands?  Make sure Mic is unmuted.  If the settings are correct as they are, it might be necessary to change setting in amixer (will need to do a bit of research to recall how).

Have you made sure that the "Sound Device" is selected as "HDA ATI SB" rather than default in whatever program you are trying to use (what are you trying to use)?

If that doesn't work, then I'll think some more...

---

### Post by gustavosenise on 2007-07-27
Have you tried changing Input Source to Mic (instead of Front Mic)?

 [COLOR="Red"]Yes[/COLOR]

The amixer output suggests that Mic is muted (off), but alsamixer screenshot shows unmuted... is this true, or did you change the setting between the 2 commands? Make sure Mic is unmuted. If the settings are correct as they are, it might be necessary to change setting in amixer (will need to do a bit of research to recall how). 

[COLOR="Red"]It is ok! It was unmuted between the 2 commands, but now is ok![/COLOR]

Have you made sure that the "Sound Device" is selected as "HDA ATI SB" rather than default in whatever program you are trying to use (what are you trying to use)? 

[COLOR="Red"]I am trying to use skype, but the microphone doesn't work with any software. The selected "Sound Device" was the default one, but then I changed to the "HDA ATI SB" but  the problem persists. I still can hear sounds but can't record! errrrrgggggg

Thanks 4 your help dude!![/COLOR]

---

### Post by ugm6hr on 2007-07-27
> Thanks 4 your help dude!!
I haven't solved anything yet!  

If you've tried both Mic and Front Mic (unmuted at the time, obviously) in the Input Source, with HDA ATI SB as Sound Device, and Capture on, then I'm not sure what's going on.

You sure the mic works (i.e. not a hardware fault)?  Is it internal or external?  Perhaps it's worth trying an external mic and repeating the above.

If I think of amything else, I'll post again.

---

### Post by gustavosenise on 2007-07-27
Oh dude! You will not believe that!

I am using a Compaq HP Desktop. It has 2 plugs entrance in its front side, for headphones and microphones. But the microphone doesn't work in this entrance!! I tryed to plug in the back of my PC, with an entrance different from the one in the front - the entrance in front is pink and in the back is blue. I think microphones entrances were always pink, am I wrong?

Well, the problem is solved!!

Thanks 4 your time!

---

### Post by joeldi on 2007-08-03
I'm on Dapper, so that could be my problem.  When i try to load sound recorded I get 

"Your audio capture settings are invalid. Please correct them in the Multimedia settings."

And there is no capture setting in the volume control.  only Volume, Line-in, Microphone, In-Gain and Digital-1.

---

### Post by ugm6hr on 2007-08-04
> **joeldi said:**
> I'm on Dapper, so that could be my problem.  When i try to load sound recorded I get 

"Your audio capture settings are invalid. Please correct them in the Multimedia settings."

And there is no capture setting in the volume control.  only Volume, Line-in, Microphone, In-Gain and Digital-1.

If you are going to use a pre-existing thread - at least give some useful information:
[http://ubuntuforums.org/showpost.php?p=3089492&postcount=11](http://ubuntuforums.org/showpost.php?p=3089492&postcount=11)

I am assuming that your sound works too...

---

### Post by joeldi on 2007-08-04
Heh.  
It appears I have a problem.

```

$~> amixer
amixer: Mixer default load error: Invalid argument
$~> alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument
$~>

```

---

### Post by ugm6hr on 2007-08-05
> **joeldi said:**
> Heh.  
It appears I have a problem.

```

$~> amixer
amixer: Mixer default load error: Invalid argument
$~> alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument
$~>

```

Do you have any sound at all?  Or is it just the microphone that is a problem?  If you have no sound - did you ever have sound?  Have you installed any updates fro Ubuntu?

Give the output from:
```
uname -r
```

What hardware are you running?  If it's anything like mine - it might be a problem with the kernel update - read this for more info: [http://ubuntuforums.org/showpost.php?p=2869640&postcount=12](http://ubuntuforums.org/showpost.php?p=2869640&postcount=12)

---

### Post by joeldi on 2007-08-06
Yes, sound works fine in general.

I installed linux off the 6.06 LTS CD, and uname -r returns
2.6.15-23-386

---

### Post by 5-HT on 2007-08-06
*edit, already suggested

---

