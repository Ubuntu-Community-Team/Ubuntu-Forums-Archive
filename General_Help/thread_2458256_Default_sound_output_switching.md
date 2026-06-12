---
title: "Default sound output switching"
date: 2021-02-20
forum: General Help
---

### Post by RobGoss on 2021-02-20
Hello I am having issues with my sound output it keeps changing every time I reboot my machine. and I have to set it to the correct output. Is there anyway to set it to a default settings so it will not change on restart. Thanks so much

I am using Ubuntu mate 20.04 and I also notice it doing it also with Ubuntu 20.04

---

### Post by CatKiller on 2021-02-20
PulseAudio's terminology for the default device is "fallback device." Whether audio streams should be moved to a new device when it appears is also a module that you can choose to enable or not.

It's trivial to set the default audio device in KDE's Settings, but I understand that Gnome's is more limited.

---

### Post by RobGoss on 2021-02-20
> **CatKiller said:**
> PulseAudio's terminology for the default device is "fallback device." Whether audio streams should be moved to a new device when it appears is also a module that you can choose to enable or not.

It's trivial to set the default audio device in KDE's Settings, but I understand that Gnome's is more limited.

Hello Cat, thank you for your fast reply

I'm not sure what you mean.....

---

### Post by CatKiller on 2021-02-20
> **RobGoss said:**
> I'm not sure what you mean.....

And I'm not sure which part you're having trouble with.

If Gnome's Settings widget has the ability to change the default device, and they haven't called it "Set Default," they'll likely have called it "fallback." If it *doesn't* have the ability, PulseAudio has its own (kinda janky) GUI configuration tool that will let you set the fallback device.

Separately, you can tell PulseAudio never to automatically change away from the fallback device. The configuration is just a text file, and you just comment out the line that loads the *automatically switch* module.

---

### Post by RobGoss on 2021-02-20
> And I'm not sure which part you're having trouble with.

Well the problem I have is when I boot my machine I have to change the output to the correct on as you can see here in the screen shot it's currently set to my microphone settings

I have to change it every time I reboot my machine. Is there something I need to change?

Thank you

---

### Post by RobGoss on 2021-02-20
Got it I was able to set it as fallback from pulse audio control thank you so much my friend really appreciate it

Now let's see if I can do the same for Ubuntu

Edit: Got the sound working in both Ubuntu mate and Ubuntu thanks so much

---

