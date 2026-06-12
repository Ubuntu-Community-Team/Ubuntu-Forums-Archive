---
title: "Sound Suddenly Stopped Working"
date: 2022-02-06
forum: General Help
---

### Post by arius88 on 2022-02-06
I installed Lubuntu 20.04 a few weeks ago and am still struggling with various issues.  It's an old machine that has been sort of Frankensteined together, so I don't think Lubuntu is to blame. Most of the problems have to do with video playback (causes stuttering and freezing often, forcing me to hard reboot the machine).  But today I'm writing because of an audio issue.  The machine has at least two outputs for sound. One is a headphone jack located on the front of the machine. On the back of the machine are six more 1/8" audio in/out jacks. I have no idea what they all do.  Anyway, today I decided that I wanted to set the machine up so I can listen via speakers OR headphones, depending on the situation.  So I started plugging my headphones into random jacks on the back of the machine to try to figure out which one was an audio output.  None of them worked, but one cut the sound off from the "headphones" output on the front when I plugged into it. (Turns out this one is a Line Out, according to my Alsa Volume Control interface.) I unplugged the Line Out, the Headphones came back on, I plugged it back in, the Headphones turned off. (The Line Out never gave me any sound at all.) Here's the kicker: I did that twice, and the second time, the Headphones never came back on. I have no sound at all now.  I've tried various combinations and rebooted my machine several times and nothing works. I can't listen to audio on this machine at present.  As you can imagine, that is extremely frustrating as my primary uses of a computer are a) watching videos and b) making music. I tried "sudo Alsa force-reload" and that didn't fix it.  Right now I've got an audio file playing. No sound from speakers and headphones, of course. When I open up Alsa Volume Control, under "Playback" I can clearly see the sound playing, with the volume meter leaping up and down. BUT when I scroll over to "Output Devices," there seems to be a problem. I don't know what it's supposed to look like when it's working, as this interface is new to me. But what I have is two options - "Line Out (plugged in)," and "Headphones (plugged in)" - and both are greyed out. The output volume is stuck at 89% and cannot be moved up or down. If I unplug one or the other, they disappear from the menu. So the machine is reading that the speakers and headphones are THERE, but there seems to be no communication between the program playing the audio and the devices.  Suggestions?  UPDATE: This issue has been resolved. I installed a program, can't find it now, but it was called "sound" or something super basic like that. Once I installed it, there was an option to unmute volume. I literally had to press one button and my sound came roaring back to life and I now have way more options to control it. I'm a little afraid to try using that Line Out jack again, but will take another stab later.

---

### Post by arius88 on 2022-02-06
P.S. I apologize for the huge block of text... is there a way to keep my paragraphs and other formatting when posting comments? If so, I can't figure it out.

---

### Post by guiverc on 2022-02-06
re: stuttering & freezing.

Are you using swapfile? or swap partition?  I'll provide some references

- Swap Lubuntu (21.04 & Up) - [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)
- How to create a swapfile in Lubuntu 20.04 & 20.10 - [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

Lubuntu from 18.10 up uses the `calamares` installer; which didn't handle *swap* automatically before 21.04 (*but did allow the user to manually set it up*), though even from 21.04 upwards it doesn't let you select your own size (*but that's easily changed post-install anyway*).  If your machine is *light* on RAM, swap makes a *huge* difference.

With regards audio - I've found how boxes behave with regards audio ports front and back can be box/hardware/firmware specific.  I have boxes that treat front & back ports as if electronically the same port (*I believe they are*) so I can have audio out of both, but on other boxes I can only use one port (ie. front or back) as the other gets disconnected on connection of a cable; with others of course letting the OS itself controls how each get used (output out one, both etc).  Having explored this with multiple OSes; it's the same on these boxes regardless of what OS is used; be it windows, GNU/Linux (inc. Lubuntu) or even a BSD.

Rather than using ALSA, have you tried Pulse Audio?   I particularly like `pavucontrol` (ie. Pulse Audio Volume Control).  [https://manual.lubuntu.me/lts/2/2.5/2.5.2/pulseaudio_volume_control.html](https://manual.lubuntu.me/lts/2/2.5/2.5.2/pulseaudio_volume_control.html)) finding it easier to deal with.

FYI:  with regards spacing; I'm just leaving a blank line between paragraphs, ie. hitting ENTER twice.

---

### Post by arius88 on 2022-02-07
Thanks for the response, guiverc.  I have no idea what a "swap" is, but I'll check out the link you provided.  Pulse Audio is what I was using before I installed "Sound." Actually it's still what I'm using for the most part, as in order to use Sound I currently have to open up Discover (btw it took me about 3 weeks to figure out this is where you "Discover" the Software Centre...), search until I find Sound, then press "Launch" or whatever, because the program isn't showing up in my bottom-left menu thingy.  That's really weird. I am also pressing enter twice to create new paragraphs. This is the 4th paragraph, ie. But when I press "submit reply" and look at my message, it is all one giant run-on paragraph.

---

