---
title: "Ubuntu 13.04 x64 Audio Issues"
date: 2013-07-12
forum: General Help
---

### Post by Aydos on 2013-07-12
Hey guys I just bought a second hard drive and decided to do Windows and one and give Linux another go on the other since Steam has so many Linux games now and gaming was always my issue.

So far the system is running great except for a couple of audio issues.

1. This one is kind of hard to explain, but I have a USB 7.1 headset (Corsair Vengeance 1500). The sound comes out of the headset fine, but it is VERY LOUD. If I try to turn the volume down and I hit the 1/3 to half way mark (which is still very loud) the audio just drops off like it is muted. Any ideas on what is making it so loud and making it mute when it gets turned to this point? I know it did not do this with the same headset when I tried it on 12.04 over a year ago.

2. My other audio option is my monitor speakers over HDMI. For some reason in the sound settings the audio only comes out when I do Test Right and I get nothing from Test Left. Sounds like my MP3s might be in mono as well.

3. I swear I remember last time I ran Ubuntu on this system that if I unplugged my headphones audio swapped to the HDMI monitor and then if I plugged the USB in it went back to the headset just like in Windows, but it does not appear to be doing that now. Either I am mistaken that it worked in the past or something is wrong there as well.

Any help for any of the three questions would be greatly appreciated.

Thank you in advance.

---

### Post by Aydos on 2013-07-12
Would like to add that I installed PulseAudio Manager and went and looked at the sink.

The audio mutes at the 30% mark in there. 

Also, if I have the show volume turned on the sound levels think there is sound below 30%, but it is not actually coming out of the headset.

Finally, the sound at anything above 30% is blaring unlike and actual 30%

---

### Post by Aydos on 2013-07-13
Found a work around for at least the loud part.

When I open an app for the first time I need to go into sound settings and turn that application down by 75%.

Does not explain why it is so loud and why it mutes at a certain point, but it is something.

---

### Post by CatKiller on 2013-07-13
One thing that might help you identify the cause is running alsamixer at the same time as you change the volume. You'll probably find that you have a few volume controls displayed in there (Master, PCM, and so on) that get aggregated into one with the PulseAudio volume control.

With your second problem, it's possible to change the speaker mapping in Pulse's config file. I don't know the details, but that might help.

I can't really tell you anything about your third problem.

---

### Post by Aydos on 2013-07-14
How would I go about doing this.

I can only find the Gnome Alsa Mixer and it will not open.

I did not have these problems in Ubuntu 12.04 I could always try going back I guess.

ANyone else have any ideas?

---

### Post by CatKiller on 2013-07-14
> **Aydos said:**
> How would I go about doing this.

Open a Terminal.

Run **alsamixer** and select the sound device that you're interested in.

Fiddle with your normal volume control and watch the volume sliders go up and down in alsamixer.

See if anything particular happens at your magic 30%.

---

### Post by Aydos on 2013-07-14
> **CatKiller said:**
> Open a Terminal.

Run **alsamixer** and select the sound device that you're interested in.

Fiddle with your normal volume control and watch the volume sliders go up and down in alsamixer.

See if anything particular happens at your magic 30%.

Ok.

Sorry I did not originally get that you just wanted me to run alsamixer in the terminal.

Here is what I am seeing.

When my Ubuntu volume hits the 30% mark it is actually the 0% mark in Alsa.

Any ideas on how to sync them or remedy the issue?

---

### Post by CatKiller on 2013-07-15
> **Aydos said:**
> Any ideas on how to sync them or remedy the issue?

I'm afraid not. Both Pulse and ALSA have configuration files, but I have no real idea what you could put in them. You said that it worked in 12.04, though, so as a regression there might be a bug report about it with a workaround, or it might be worth filing a bug report yourself.

---

