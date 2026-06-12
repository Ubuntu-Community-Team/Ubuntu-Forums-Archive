---
title: "Sound isn't working"
date: 2008-04-27
forum: General Help
---

### Post by sonshadowcat on 2008-04-27
When I installed kubuntu 8.04 last night, everything was working fine. I decided to reinstall due to some problems which I couldn't solve and now my sound refuses to work.

The only thing I did differently was install the kubuntu restricted drivers( hoping I could now play dvds, I still can't) and not install mp3 support through amarok. Sound was working fine before but now I get nothing anywhere, not in amarok, not in mplayer, not in firefox. 

I looked to see if I could install the xine plugin for mp3 support but it's greyed out so I can't.



Any help would be greatly appreciated.

---

### Post by ryanhaigh on 2008-04-27
To get mp3 support as well as java, flash and a bunch of very useful apps just install kubuntu-restricted-extras. More info here including a link to enable dvd playback.

As for sound that is a separate issue, did you have to do any special configuration last time you installed ubuntu. Can you provide the output of lspci from the terminal.

You might want to look here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by nerdtank on 2008-04-27
this may sound simplistic, but I had the same kind of problem after my Adept upgrade from Gutsy... Turns out alsamixer mutes the front channel of my sound card on every reboot !

Open a console -> alsamixer -> Move to Front (and I believe Surround) and trigger the Mute on/off with the "m" key...

"Fixed" it for me...

---

### Post by sonshadowcat on 2008-04-28
ryan: I didn't do anything special since installing kubuntu so that can't be the reason. And lspci gives me the wrong info, it says I have an audigy2 when I have an audigy4. The system settings says the correct info though. It also has HDA Nvidia which is also set as the main in alsamixer, can that be a reason for this problem?

I also followed that link you gave me and did everything except installing the alsa drivers since I didn't know what to put down for my driver.




Nerd: That worked the first time, but it stopped working after I restarted.



I just reinstalled just to see what would happen. After a fresh install, the sound does not work.



Edit: I figured it out I believe, it seems my motherboards onboard sound was being selected as default. I had forgotten about onboard sound and selected my audigy as primary and now it works...so far.

---

