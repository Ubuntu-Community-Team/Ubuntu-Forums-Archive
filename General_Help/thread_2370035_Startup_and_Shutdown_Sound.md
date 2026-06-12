---
title: "Startup and Shutdown Sound"
date: 2017-08-29
forum: General Help
---

### Post by death-pro on 2017-08-29
Hi Everyone,

I want to change the startup and shutdown sound on Ubuntu 16.04 LTS. I changed startup sound but i can't change shutdown sound. Actually there is no shutdown sound as default i guess. How can i add shutdown sound ?

---

### Post by raleigh3 on 2017-08-29
Here is an example of playing a sound.

Not sure how you would play it on shutdown.

```
vlc --play-and-exit /usr/share/sounds/My_Sounds/Short_doorbell.wav
```

---

### Post by wheatpenny2 on 2017-08-29
How do you change the startup (log-in) sound? I can't seem to find an option for it in System Settings

---

### Post by death-pro on 2017-08-30
> **wheatpenny2 said:**
> How do you change the startup (log-in) sound? I can't seem to find an option for it in System Settings

```
cd /usr/share/sounds/ubuntu/stereo
sudo cp dialog-question.ogg dialog-question.ogg.old  # for backup that sound and this sound is startup sound on ubuntu 16.04 LTS as default.
sudo cp /your/sound/path/ .   # your sound that you want to add startup sound must be that name and file format "dialog-question.ogg". You can change your sound format to ogg with "audacity" program
```

---

### Post by death-pro on 2017-08-30
[https://askubuntu.com/questions/138282/how-to-enable-shutdown-sound-on-ubuntu-12-04-lts-and-up](https://askubuntu.com/questions/138282/how-to-enable-shutdown-sound-on-ubuntu-12-04-lts-and-up)

I tried this and I gave that file name "K01shutdownsound.sh" for gain high-priority (K01). but it still doesn't work. There is no sound when I shutdown the PC.

Can anyone help ???

---

