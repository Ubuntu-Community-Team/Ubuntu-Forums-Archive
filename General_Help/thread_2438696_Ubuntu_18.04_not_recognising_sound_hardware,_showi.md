---
title: "Ubuntu 18.04 not recognising sound hardware, showing dummy output"
date: 2020-03-16
forum: General Help
---

### Post by mrsean on 2020-03-16
[COLOR=#000000]Here is my alsa setup, please advise as I have removed and reinstalled ALSA and also installed generic sound drivers for ubuntu:[/COLOR]

[http://alsa-project.org/db/?f=508f12...7429dd21ed8501]("http://alsa-project.org/db/?f=508f122eccfc3630e4428f07787429dd21ed8501")

[COLOR=#000000]Now ubuntu 18.04 not seeing my built in sound card on ASRock FM2A55M-DGS (5.1 CH HD Audio (Realtek ALC662 Audio Codec))[/COLOR]
[COLOR=#000000]Problem started because I could only get stereo 2 channel with default ubuntu install, so tried to get Realtek drivers so I could access full 5.1 surround sound.[/COLOR]

---

### Post by Yellow Pasque on 2020-03-16
> so tried to get Realtek drivers 

1. Remove the Realtek drivers by running make uninstall in the appropriate directory. For instance, if you used your Downloads folder:
```
cd ~/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa
sudo make uninstall
```
2. Reinstall the linux-modules packages:
```
sudo apt-get install --reinstall linux-modules-`uname -r` linux-modules-extra-`uname -r`
```
3. Reboot. 
Is sound back?

---

### Post by mrsean on 2020-03-16
Step 1.

sean@ubuntuPC:~/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa$ sudo make uninstall
[sudo] password for sean: 
rm -rf /include/sound
rm -f /snd*.o /persist.o /isapnp.o
rm -f /sbin/init.d/alsasound
rm -f /etc/rc.d/init.d/alsasound
rm -f /etc/init.d/alsasound

Step 2. reinstall the linux modules packages.

Step 3. Rebooting....

[SIZE=4][B]Thanks Yellow Pasque now sound settings show both hdmi and line out again.
Line Out is still only Analog Stereo Output, is it possible to use the full potential of this output, on windows it is 5.1 Surround Sound?[/B][/SIZE]

---

### Post by wildmanne39 on 2020-03-16
For users that may try the commands in the above post please be aware that the commands are dangerous if done in the wrong directory or with certain options you could wipe out your entire system.

---

### Post by Yellow Pasque on 2020-03-16
> **mrsean said:**
> Line Out is still only Analog Stereo Output, is it possible to use the full potential of this output, on windows it is 5.1 Surround Sound?

Can you run the alsa info script again? Are you playing actual surround sound sources or are you trying to create a surround effect by copying output to the rear speakers?

[QUOTE=wildmanne]For users that may try the commands in the above post please be aware that the commands are dangerous if done in the wrong directory or with certain options you could wipe out your entire system.[/QUOTE]

Sorry about that. I've edited it to be more specific. Hopefully, it's (a little) better.

---

