---
title: "problems in laptop"
date: 2008-05-19
forum: General Help
---

### Post by jacklsw2008 on 2008-05-19
i've just installed ubuntu 8.04 a few days ago in my hp nx5000 laptop.

everything's okay except for a few issues that i encountered:
1. when i test the lid's button, the screen goes blank as what i choose in power management. but then when i release the lid button, the screen won't go back to the system and it hangs there, i'll have to force shut down the system.

2. if i restart the computer from xp and log into ubuntu, ubuntu can't shut down/restart properly and it hangs without completely shutting down the system. not a big issue as i can completely shut down win xp and starts ubuntu.

3. I have a 4-port usb hub. ubuntu can detect my hub but can only utilize 1 of the port at a time. if i plug in more than 1 device into the hub, it won't detect anything at all.

4. when package manager is downloading and i open a video file to play, the screen goes blank and the system hangs.

i hope i could get some explaination to what's happening in my laptop.

im running under intel centrino 1.6Ghz and 1GB RAM. my graphics ard is intel 82852/82855 GM/GME graphics controller.

---

### Post by abhiroopb on 2008-05-19
> **jacklsw2008 said:**
> 
1. when i test the lid's button, the screen goes blank as what i choose in power management. but then when i release the lid button, the screen won't go back to the system and it hangs there, i'll have to force shut down the system.

1. What have you selected in power management? And do you keep it held down? Or do you press it, release, (screen is black), and then you press it again at which point it appears to do something but remains black?

> **jacklsw2008 said:**
> 
2. if i restart the computer from xp and log into ubuntu, ubuntu can't shut down/restart properly and it hangs without completely shutting down the system. not a big issue as i can completely shut down win xp and starts ubuntu.

2. So if you restart XP ubuntu starts-up but does not shutdown properly?

> **jacklsw2008 said:**
> 
3. I have a 4-port usb hub. ubuntu can detect my hub but can only utilize 1 of the port at a time. if i plug in more than 1 device into the hub, it won't detect anything at all.

3. No idea, have you tried plugging the hub into a different port in your computer?
Please open a terminal (Applicantions>Accessories>Terminal), type in lsusb and post the output.

> **jacklsw2008 said:**
> 
4. when package manager is downloading and i open a video file to play, the screen goes blank and the system hangs.

4. what were you downloading? or is this for everything? Try opening a terminal and input: 
```

sudo apt-get install conky

```
and then try playing a video file (NB: you can use the terminal to install things using the command "apt-get install")

---

