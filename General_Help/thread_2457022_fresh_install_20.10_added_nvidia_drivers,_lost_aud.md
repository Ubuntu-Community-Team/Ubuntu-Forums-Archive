---
title: "fresh install 20.10 added nvidia drivers, lost audio"
date: 2021-01-24
forum: General Help
---

### Post by harold95 on 2021-01-24
so after a fresh install i installed nvidia drivers.

somehow, rather than using my on board intel audio, its trying to use the hdmi audio the card has on it.

i don't use the hdmi port at all.

is there a way to reset the audio back to my on board audio?

after the fresh new install, i had made sure to test it, and it did work just fine. but the nvidia driver install messed that up.

---

### Post by CelticWarrior on 2021-01-24
Your screenshot show a "dummy output" only, meaning it hasn't detect *any* audio device. Why do you think *"[COLOR=#000000]its trying to use the hdmi audio"[/COLOR]*[COLOR=#000000] when it isn't even there[/COLOR][COLOR=#000000]?

> [/COLOR][COLOR=#000000]after the fresh new install, i had made sure to test it, and it did work just fine. but the nvidia driver install messed that up.[/COLOR][COLOR=#000000]
This statement doesn't match up with reality. Here are a few thing to consider before further troubleshooting:
Since at least the 20.04 release Nvidia drivers and other proprietary drivers are typically installed automatically during the OS installation just by selecting the "install third-party drivers, codecs, etc." option. Of course, users are free to not select that option and later install the Nvidia drivers as it used to be before this became an option. Should you assume this is what you did? If so, how exactly have you installed the Nvidia drivers, what are your card model and drivers version? Have you kept Secure Boot enabled or disabled it?
Installation of Nvidia drivers does NOT result in the issue you're reporting, there must be something else at play here.[/COLOR]

---

### Post by zebra2 on 2021-01-24
alsamixer at prompt and see what you have.

---

### Post by harold95 on 2021-01-24
> **zebra2 said:**
> alsamixer at prompt and see what you have.

i've attached what alsamixer see's

none of my applications see anything but the "dummy"

i have jacked up the volume in alsamixer across the board, yet i still have no audio.

thanks!

---

### Post by grahammechanical on 2021-01-24
I do not use Lubuntu so I give you this link from the Lubuntu developers for PulseAudio. That is the utility I suggest you load and may be there you can make some adjustments. Try both Input and Output tabs. In Ubuntu it is System Settings>Sound to get similar functionality.

[https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html](https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html)

Regards

---

### Post by harold95 on 2021-01-24
> **grahammechanical said:**
> I do not use Lubuntu so I give you this link from the Lubuntu developers for PulseAudio. That is the utility I suggest you load and may be there you can make some adjustments. Try both Input and Output tabs. In Ubuntu it is System Settings>Sound to get similar functionality.

[https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html](https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html)

Regards


attached what pulse audio see's in mixer.

i have allot invested in this install.  but if i had to, i could start over again, wipe it and this time choose to install the 3rd party drivers, if that would solve it. i didn't see that option the first time.

---

### Post by CelticWarrior on 2021-01-24
You ignored what I posted before but here's some more relevant info:
Installing or not installing Nvidia drivers - regardless of the method - has nothing to do with the internal onboard audio. Two completely different and independent devices. Nvidia drivers may be needed - not a given - for enabling HDMI audio output for some cards but most older ones typically work as well with the open-source driver nouveau.

Still it would be interesting to know your hardware specifications and how and what version of the Nvidia drivers you installed. There's a possibility that you screwed things up when doing it but that's not the driver's installation fault.

There's really no point in poking Pulseaudio or other tools when you have only a "dummy output". That means NOTHING is being detected, period. Why this happened remains to be understood. End of story.

---

