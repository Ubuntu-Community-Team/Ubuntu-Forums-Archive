---
title: "Leadtek Winfast TV2000 XP Expert (CX23880) sound MADNESS"
date: 2008-01-15
forum: General Help
---

### Post by LeDechaine on 2008-01-15
Ok, fresh Ubuntu 7.10 installation. I remember I have a TV Card (haha) so I search for a program/daemon (or whatever you call this in linux) to watch TV. I find TVTime. I open the program, and I can watch TV! I find it really nice that I didn't even had to type commands in the terminal to view TV. I scan for channels, and I have them all!

But the problem is: **I have no sound.**

I put the volume to the max in TVTime. I also put it to the max in the sound configuration menu. I set it to mono/stereo/sap. *Nothing.*

These commands:
```
v4lctl volume mute off
v4lctl volume 65535
```
..seems to be useless for me.

Note that I also have XawTV, and that there is **no volume bar** in the options. I just can move my mouse over and the cursor changes, but I don't even know if this makes any difference.

My TV Card is plugged in my Audigy 2 AUX2 sound card input. So I open the Alsa Mixer GUI, and put *everything* to the max. All i receive is "noise" from the **Line In 2** + **Aux** + **Aux2** + **Analog Mix** inputs. Well, i think.

"*I think*", because when I messed with all these "sliders", I heard noise (precision: just white noise, no voice/music/etc), but I just rebooted, and now, I hear absolutely **nothing** coming from these 4 inputs. Absolutely everything is to the max, absolutely nothing is muted.
*(And **yes**, my sound card works well, i'm now currently listening to songs with XMMS through ALSA.)*

I also note that the card works well in Windows. Image **and** sound. All I have to do in windows is to "unmute" the **Aux** sound card input in the mixer. But I sometimes also have to "unmute" the volume of the TV card **itself**.

So, any ideas?
The only idea **I** have for now is to go in windows, unmute the TV card (if it's muted, but i'm 90% sure it wasn't), and go back to ubuntu + TVTime to "see" if I finally "hear" something, 'cause I haven't found any (working) way of unmuting this TV Card in linux yet. But i'm really unsure about that, anyway, i'll test later.

Like I said: Any ideas?
Thanks in advance!

---

### Post by LeDechaine on 2008-02-01
Update: Back to "normal" i.e.: noise from Line In 2 + Aux + Aux2 + Analog Mix. But still no sound.
Got back to XP yesterday and the card wasn't muted, too.

I'm starting to think that if time is money, buying another TV Card or even a TV will actually make me *save*. According to the posts in the forum this card is just a ******* nightmare in ubuntu anyway. After all, it's a **Win**fast, not a **Lin**fast...

Whatever, if you can help me, let's go.

---

### Post by LeDechaine on 2008-02-11
Hmm... Maybe this can be related..
In /etc/tvtime/tvtime.xml:
```
<option name="MixerDevice" value="/dev/mixer:line"/>
<option name="AudioBoost" value="-1"/>
```
(is it?)

More: Yesterday I found that the cx8800 module I use for listening to TV is buggy and for this reason ksoftirqd is using ~20% CPU when the module is loaded. Sad. But whatever, if anyone knows the "card" and "tuner" values for a TV2000XP Expert card, tell me! (or just the minimum and maximum "card" and "tuner" values of the cx8800 module (or bttv or whatever working module for this card, ***if one compatible module exists, at least***), so I can check them ALL by hand, at worst...)

For now the only problem is that I have **no sound**. Card is working #1 with **card=5** and **tuner=43** (automatic configuration), but no sound. I don't know if there is sound coming from the TV Card audio output, and I don't care. The sound quality of this is near AM Radio. I want this card to output sound from its AUX output, which is plugged right in my PCI audigy 2 card AUX2 Input.

Any help/info appreciated. Else i'm gonna buy another card, hoping it's not as crappy as this one.

---

### Post by LeDechaine on 2008-03-18
Nevermind, the problem is my Audigy 2 sound card, scrapped drivers makes my sound card AUX input useless.

Waiting for a new one then..

---

### Post by seiyachan on 2008-04-24
QUICK FIX, work for my winfast tv2000 expert, there was no sound in tvtime as well. by doing this, the problem is fixed!

1. open (double click) the Volume Control from the system tray.
2. choose from the menu, edit-->preferences-->find "Aux" and check the box
3. unmute the Aux playback in Volume Control.
4. Sound out of the tv box!

hope it helps! :)

---

### Post by seiyachan on 2008-04-24
Yet, I am another problem, I am in Australia, there are 6 channels available for analogue TV. 

1. ABC
2. Seven
3. Nine
4. Ten
5. SBS
6. a community channel.

I have configured all frequencies for the channels in stationlist.xml for tvtime. 2,3,4 have no problem at all. however for 1,5,6, once I switch to the channels, it blinks a still from the channel and the screen goes blue like no signal, but i am sure it does get the signal. anyone knows the reason?

---

### Post by seiyachan on 2008-04-24
ok, found the answer.... in "stationlist.xml".....

<station name="ABC" active="1" position="2" band="Custom" channel="64.25MHz" finetune="0" norm="SECAM" audio="auto"/>

change the "norm" to PAL and now all is fine.

<station name="ABC" active="1" position="2" band="Custom" channel="64.25MHz" finetune="0" norm="PAL" audio="auto"/>

---

