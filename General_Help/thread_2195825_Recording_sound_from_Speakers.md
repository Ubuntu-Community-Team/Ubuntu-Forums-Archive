---
title: "Recording sound from Speakers"
date: 2013-12-26
forum: General Help
---

### Post by daniell59 on 2013-12-26
I would like to record the sound coming out of my speakers. Using sound recorder I am able to record sound with the microphone. Is is possible to use sound recorder to record sound coming out of the speakers? I tried different imputs. Nothing has worked.

Ubuntu 12.04 64

---

### Post by Unterseeboot_234 on 2013-12-26
There is a Gnome applet, either sound-recorder or audio-recorder. I found sound-recorder on these Ubuntuforums board. So, I googled 'ubuntu sound-recorder' and see the same applet with both of the names I'm mentioning.

---

### Post by Dennis N on 2013-12-26
Audio recorder will do it. Use this ppa:

[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

---

### Post by ajgreeny on 2013-12-26
Try audio-recorder, not in the standard repos but available from [https://launchpad.net/~osmoma/+archive/audio-recorder/+packages](https://launchpad.net/~osmoma/+archive/audio-recorder/+packages) which very easily lets you choose to record the sound either from your mic or from the soundcard audio-output, as  shown in my screenshot..

You can do it with sound-recorder as well but it is a bit more involved; you need to start recording with the sound-recorder application, then go into pulseaudio-volume-control and choose "Monitor etc etc" (exact wording depends on your hardware, I think).  Only when actually recording do you get the choice of hardware to use as the recording input with sound-recorder, but the audio-recorder package sorts all that out for you quickly.

---

### Post by daniell59 on 2013-12-27
You can do it with sound-recorder as well but it is a bit more involved; you need to start recording with the sound-recorder application, then go into pulseaudio-volume-control and choose "Monitor etc etc" (exact wording depends on your hardware, I think).  Only when actually recording do you get the choice of hardware to use as the recording input with sound-recorder, but the audio-recorder package sorts all that out for you quickly.[/QUOTE]

I appreciate the link. It is confusing to me. I don't have a clue on how to install it.
Any additional assistance will be appreciated.

---

### Post by Habitual on 2013-12-27
[Record what comes out of your speakers]("http://www.bournetoraiseshell.com/article.php?story=20101116231547304&query=speakers") it's a little dated, but may still work.
[ ]("http://www.bournetoraiseshell.com/article.php?story=20101116231547304&query=speakers")

---

### Post by Dennis N on 2013-12-27
> **daniell59 said:**
> 
I appreciate the link. It is confusing to me. I don't have a clue on how to install it.
Any additional assistance will be appreciated.

NOTE: Audio Recorder needs pulse audio to be installed to work. The tag on your post says Lubuntu, but at the end of your post I see "Ubuntu 12.04 64". IF you are really using Lubuntu, it does not have the pulse audio package installed by default. In that case, the procedure below will also install the pulse audio sound package if it is not already present on your system. Ubuntu 12.04 already has it by default, so no problem. 

Installation:

Use the terminal: 
First, add the ppa (some useful information about audio recorder is shown first): 
```
sudo add-apt-repository ppa:osmoma/audio-recorder
```
Second, update the software sources:
```
sudo apt-get update

```
Third, Install:
```
sudo apt-get install audio-recorder
```

---

### Post by daniell59 on 2013-12-27
The tag on your post says Lubuntu, but at the end of your post I see "Ubuntu 12.04 64". 
 Sorry for the mistake. I have Ubuntu 12.04 64.

---

