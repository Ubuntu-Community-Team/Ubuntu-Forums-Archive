---
title: "No Sound or any hardware detected post installation of PulseAudio."
date: 2021-02-01
forum: General Help
---

### Post by amol7 on 2021-02-01
Hello.

For recording audio into Audacity I had to install PulseAudio. (To get the best input). And After that I get no sound from my speakers.
My speakers aren't even detected.
(Image attached)

I have tried solutions suggested in the following forums
[LIST=1]
[*][https://itectec.com/ubuntu/ubuntu-ubuntu-16-04-audio-not-working-correctly/](https://itectec.com/ubuntu/ubuntu-ubuntu-16-04-audio-not-working-correctly/)
[*][https://unix.stackexchange.com/questions/401196/ubuntu-no-sound-from-speakers-headphones-jack-detected-even-when-no-headphones](https://unix.stackexchange.com/questions/401196/ubuntu-no-sound-from-speakers-headphones-jack-detected-even-when-no-headphones)
[*][https://unix.stackexchange.com/questions/579486/alsa-pulseaudio-and-intel-hda-pch-with-no-sound?rq=1](https://unix.stackexchange.com/questions/579486/alsa-pulseaudio-and-intel-hda-pch-with-no-sound?rq=1)
[*][https://unix.stackexchange.com/questions/143865/how-to-enable-both-built-in-audio-output-and-hdmi-audio-output-with-pulseaudio?rq=1](https://unix.stackexchange.com/questions/143865/how-to-enable-both-built-in-audio-output-and-hdmi-audio-output-with-pulseaudio?rq=1)
(This one I didn't try but I still bookmarked it)
[*][https://linuxforums.org.uk/index.php?topic=13070.0](https://linuxforums.org.uk/index.php?topic=13070.0)
[*][https://www.quora.com/How-do-I-fix-Linux-Mint-16-04-sound-problem](https://www.quora.com/How-do-I-fix-Linux-Mint-16-04-sound-problem)
[*][https://ubuntuforums.org/showthread.php?t=2370636](https://ubuntuforums.org/showthread.php?t=2370636)
[/LIST]

Please let me know what more information is needed.

Thank You in advance.

<Please expect a delay in response due to different time zones.>

---

### Post by tea for one on 2021-02-01
Your image does not look like [COLOR="#0000FF"]pulseaudio[/COLOR]?

Pulseaudio has 5 tabs:- **Playback : Recording : Output Devices : Input Devices : Configuration**

Which version and flavour of Ubuntu are you using?

Please open a terminal and enter:- ```
pavucontrol
```

What is the result?

---

### Post by ajgreeny on 2021-02-01
The pulseaudio-volume-control (package ***pavucontrol***) hence the suggestion from **tea for one**, should look like my screenshot and gives you a dropdown box where you can choose yoiur output device, ie speakers or headphones in the Output Devices tab.
As you can see there are many tabs to look through and play around with settings, but keep a note of what you've changed as you may need to restore the settings to their default.

---

### Post by amol7 on 2021-02-02
> **ajgreeny said:**
> The pulseaudio-volume-control (package ***pavucontrol***) hence the suggestion from **tea for one**, should look like my screenshot and gives you a dropdown box where you can choose yoiur output device, ie speakers or headphones in the Output Devices tab.
As you can see there are many tabs to look through and play around with settings, but keep a note of what you've changed as you may need to restore the settings to their default.

> **tea for one said:**
> Your image does not look like [COLOR=#0000FF]pulseaudio[/COLOR]?

Pulseaudio has 5 tabs:- **Playback : Recording : Output Devices : Input Devices : Configuration**

Which version and flavour of Ubuntu are you using?

Please open a terminal and enter:- ```
pavucontrol
```

What is the result?

I'm using 16.04LTS Ubuntu.

That image was from the System settings, to show that my speakers are not detected. Here are the images from the pavucontrol dialog box.

---

### Post by tea for one on 2021-02-02
Did you ever have sound?

Please post the following:-

Make, model, age of your PC
Which speakers do not show up - external, usb, built in to the monitor or anything else.

If you have a new PC, then using software almost 5 years old (Ubuntu 16.04) is not appropriate.

16.04 will be EOL (end of life) in Aril 2021 so you may want to think about upgrading.

---

### Post by amol7 on 2021-02-02
> **tea for one said:**
> Did you ever have sound?

Please post the following:-

Make, model, age of your PC
Which speakers do not show up - external, usb, built in to the monitor or anything else.

If you have a new PC, then using software almost 5 years old (Ubuntu 16.04) is not appropriate.

16.04 will be EOL (end of life) in Aril 2021 so you may want to think about upgrading.

I use a HP Laptop, 15-ac170tu and it is 5 years old.
These have in-built speakers which do not show up. And yes I always had sound until I installed PulseAudio.

---

### Post by tea for one on 2021-02-02
That's a bit unusual - the addition of pulseaudio generally provides more benefits rather than loss of sound.

Have you read the sound troubleshooting info:- [https://ubuntuforums.org/showthread.php?t=1885240](https://ubuntuforums.org/showthread.php?t=1885240)?

Sound is always tricky to solve remotely and your system will be out of date soon.
Therefore I would recommend that you download an Ubuntu 20.04 iso, make a USB bootable disk and test your sound with newer software.

---

### Post by amol7 on 2021-02-03
> **tea for one said:**
> That's a bit unusual - the addition of pulseaudio generally provides more benefits rather than loss of sound.

Have you read the sound troubleshooting info:- [https://ubuntuforums.org/showthread.php?t=1885240](https://ubuntuforums.org/showthread.php?t=1885240)?

Sound is always tricky to solve remotely and your system will be out of date soon.
Therefore I would recommend that you download an Ubuntu 20.04 iso, make a USB bootable disk and test your sound with newer software.

Funny Thing, I was going through one of the guides mentioned in the link you have posted.
One of the steps is to kill PulseAudio first then restart it.

I tried killing the PulseAudio but here's the result

```
killall pulseaudio; pulseaudio -k  ; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*pulseaudio(1096): Operation not permitted
pulseaudio(1221): Operation not permitted
pulseaudio: no process found
E: [pulseaudio] main.c: Failed to kill daemon: No such process
rm: cannot remove '/home/amol/.pulse*': No such file or directory
```

So I did what was said next, I entered the code to start PulseAudio

```
killall pulseaudio; pulseaudio -k  ; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*pulseaudio(1096): Operation not permitted
pulseaudio(1221): Operation not permitted
pulseaudio: no process found
E: [pulseaudio] main.c: Failed to kill daemon: No such process
rm: cannot remove '/home/amol/.pulse*': No such file or directory
```

and Viola! The Speaker Icon immediately darkened and now I can hear audio through the speakers!
So for now all is good. I just need to check if it works once I reboot the system.

Update: The PulseAudio doesn't start with a reboot of the system.

Many thanks.

---

