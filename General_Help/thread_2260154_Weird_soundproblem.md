---
title: "Weird soundproblem"
date: 2015-01-09
forum: General Help
---

### Post by stianovesen on 2015-01-09
Hello! I am totally new to ubuntu and I really like it so far, but I am having a really strange soundproblem and I am about to go crazy.
I am aware of the usual soundproblems that people are having with Ubuntu 14.04, but I simply can't find a solution to my problem.
I do have sound and I can seemingly watch videos and youtube without any problems, but when I'm listening to mp3's or playing a game my sound just disappears after a couple of minutes.
I have tried fiddling with the alsamixer and the pavucontrol, but there doesn't seem to be any problem at all, except that there's no sound. The only clue I really have is when i type pulseaudio in 
the terminal i get the message:

E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

My only option is to restart my computer and the sound is back.
I would appreciate any help I could get because I really don't want to go back to Windows.

Thanks in advance
Stian

---

### Post by stianovesen on 2015-01-09
I just realized something! I tried plugging in a headset when my sound disappeared and I have sound. This obviously means that my computer randomly switches to the headphones output device. I am still unable to get any sound in my laptopspeakers until I do a restart though. Has anyone encountered this issue or am I the only one?

---

### Post by mörgæs on 2015-01-10
Hi, welcome to the fora.
How does it work in a live boot of 14.10?

---

### Post by stianovesen on 2015-01-10
Hi and thank you! I haven't tried this but I will give it a try after the weekend.

---

### Post by Yellow Pasque on 2015-01-10
"Daemon already running" is the expected output for vanilla "pulseaudio" command. The next time this happens, try killing pulseaudio (it will automatically restart):
```
pulseaudio -k
```

> This obviously means that my computer randomly switches to the headphones output device.
I don't know if I would conclude that. Try the same experiment when your sound is playing correctly and it may automatically switch to playing headphones (aka automute), because sound devices are aware when you plug headphones or other devices in (aka jack sensing).

If you can't reproduce the issue in a Live media, I would try updating to latest ALSA module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

