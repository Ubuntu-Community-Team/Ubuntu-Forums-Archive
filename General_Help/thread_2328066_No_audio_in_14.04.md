---
title: "No audio in 14.04"
date: 2016-06-17
forum: General Help
---

### Post by jeff162 on 2016-06-17
I've been going around trying to solve a no audio problem in Ubuntu 14.04.

At first I thought it was codecs but it turns out that's not the issue. I get no audio from any video or audio file in any player. I was messing around with kxstudio repositories but later uninstalled them and I was pretty sure I got rid of it all. Still, something got changed and I have no sound. alsamixer shows everything's fine. 

That clonking sound plays when the laptop boots but when I login I get nothing. I setup another user and the audio worked fine in that user. I'm kinda lost here and can't find any good info.

What are the steps I need to take to get my user profiles audio working again?

---

### Post by speartip on 2016-06-17
If the Audio worked fine after you added a user, then your problem must be a simple configuration problem.
This might sound basic, but try installing pavucontrol, "pulseaudio volume control" and check nothing is muted or set too low.
Also when you uninstalled kxstudio, did you check what other packages where uninstalled? It might be worth installing it again to see if your audio then works, then check what it wants to remove when you uninstall it.

---

### Post by jeff162 on 2016-06-19
I installed pavucontrol and I set the speaker output as fallback. That got .mp3s playing in rhythmbox with audio but there's no audio in vlc or any other app I tried. As a sidenote I have to kill rhythmbox, vlc and mpv in the terminal or they just run and run in the background.

I tried reinstalling the kxstudio repos, and ran apt-get update and apt-get upgrade. Here's the terminal output on what I installed:

```
The following packages were automatically installed and are no longer required:  libmowgli2 libquvi-scripts libquvi7 libsdl2-2.0-0 libva-glx1
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  libpulse0 pulseaudio
The following packages will be upgraded:
  alsa-base kxstudio-repos libgphoto2-6 libgphoto2-l10n libgphoto2-port10
  libjack-jackd2-0 libpulse-mainloop-glib0 libpulsedsp libqt5webkit5
  libqt5webkit5-qmlwebkitplugin linux-sound-base numix-icon-theme
  pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils
  python-imaging python-pil python-serial
18 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 13.1 MB of archives.
After this operation, 3,528 kB of additional disk space will be used.

```

There's still no audio except in rhythmbox.

I still have a mental block when it comes to dependencies so any aid is appreciated there. I don't really know if the problem is there or somewhere else.

---

### Post by speartip on 2016-06-19
OK. 2 things to try.
1st. 2 packages are not being upgraded. libpulse0 & pulseaudio. Run:
```
sudo apt-get dist-upgrade
```
to update those packages. Then in your home folder, view hidden files, go into the .config folder & delete the pulse folder & any files relating to pulse.
Then Reboot. Your pulse folder will be re-created. See if you now have sound.

2nd. Failing that, log into the guest account & check if sound is working correctly there, & report back.

---

### Post by jeff162 on 2016-06-20
> **speartip said:**
> OK. 2 things to try.
1st. 2 packages are not being upgraded. libpulse0 & pulseaudio. Run:
```
sudo apt-get dist-upgrade
```
to update those packages. Then in your home folder, view hidden files, go into the .config folder & delete the pulse folder & any files relating to pulse.
Then Reboot. Your pulse folder will be re-created. See if you now have sound.

2nd. Failing that, log into the guest account & check if sound is working correctly there, & report back.


I did the dist-upgrade and deleted the pulse folder. I have sound again!! Thank you!!

---

