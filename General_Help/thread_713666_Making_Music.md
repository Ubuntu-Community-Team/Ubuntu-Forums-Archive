---
title: "Making Music?"
date: 2008-03-03
forum: General Help
---

### Post by Trurl on 2008-03-03
I've recently become interested in making my own music within Ubuntu. I've checked out some other threads, but haven't seen anything recent and I'm not sure what the state of things is.

I'm a complete neophyte in this area, and all I've got is standard Gutsy. 

So, where do I start?

---

### Post by Th3Professor on 2008-03-03
Ubuntu Studio

---

### Post by Drunky on 2008-03-03
I would upgrade to Ubuntu Studio first.

Enter:```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```at a terminal.  This is from [Ubuntu Help: UpgradingFromGusty wiki help page.]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy")

This will upgrade to Ubuntu Studio.  This is a full upgrade, not just a desktop or theme.

Why Ubuntu Studio?

Well, on a topical level it has a good foundation of musical and graphical programs already installed for you.

Additionally, and on a more fundamental level, it uses the real-time kernel.  The real-time kernel is optimized to minimize latency between when you play the music, when you hear the music, and when the music is recorded to hard disk.

Also, processes are re-prioritized so that things like moving your mouse shouldn't take precedence over recording music, this means getting music recorded to the hard drive shouldn't suffer any gaps because your computer thought it more important to update the cursor position.

---

### Post by Trurl on 2008-03-03
Thanks for the info.

Are there downsides to Studio (and can it be run in virtualbox)? And once I've got it, where do I get started? I don't have any external devices or a fancy sound card or anything, I was just hoping there was a simple way to learn the ropes...

Is there an alternative to upgrading to studio, just to play around with the software first? 

Thanks again...

---

### Post by altonbr on 2008-03-03
Ubuntu Studio is (in basic terms) a new realtime kernel for serious audio and video capturing performance; a collection of audio, video and graphical editing software; a different theme (login window, wallpaper, controls, etc.). So no, you do not have to install Ubuntu Studio and can in fact install just the programs using: 

```
sudo apt-get update && sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

Just be careful, as it installs a lot of software, so make sure you have 1) enough space 2) enough bandwidth or 3) enough time if you're on a slow connection.

As for the specific programs that Ubuntu Studio uses, check out the Wikipedia article: [http://en.wikipedia.org/wiki/Ubuntu_Studio](http://en.wikipedia.org/wiki/Ubuntu_Studio)

---

### Post by Th3Professor on 2008-03-03
> **Trurl said:**
> Thanks for the info.

Are there downsides to Studio (and can it be run in virtualbox)? And once I've got it, where do I get started? I don't have any external devices or a fancy sound card or anything, I was just hoping there was a simple way to learn the ropes...

Is there an alternative to upgrading to studio, just to play around with the software first? 

Thanks again...

You said you don't have a fancy sound card. If it's an old one, this might help:
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

Here's Ubuntu's /community/Sound page:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

Ubuntu's Troubleshooting Sound page:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If you have an older computer and don't want to use:
the Ubuntu Studio package
...which includes graphics and video apps (potentially unnecessary apps)
the "linux-rt" real time kernel...

...then (if you have an older computer) you might consider this:
[https://help.ubuntu.com/community/LowEndSystemSupport](https://help.ubuntu.com/community/LowEndSystemSupport)
(Talks about: using a lightweight desktop environment, replacing heavy apps with light ones (if needed at all,) and optimizing the performance of the apps you do keep.)

---

### Post by dwasifar on 2008-03-03
You need to download and install the "Klapaucius" package.

No, not really.  But I couldn't think of a better way to comment on your excellent choice of handle.

---

