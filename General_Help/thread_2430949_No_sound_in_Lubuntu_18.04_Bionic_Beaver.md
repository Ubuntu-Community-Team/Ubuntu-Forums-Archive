---
title: "No sound in Lubuntu 18.04 Bionic Beaver"
date: 2019-11-09
forum: General Help
---

### Post by iconoclast12 on 2019-11-09
I have Lubuntu 18.04 installed on an Atomic Pi and I'm having some issues with my audio.. I first noticed this was an issue right after the operating system finished installing. In my volume control panel, the only output device that was available (and what it was set to) was analog audio. I'm on HDMI, since that's the only video output on this device (I also want to and NEED to use HDMI). So, the first thing I did was google "no audio in Lubuntu 18.04" and found that several others were having the same issue. First things I tried, were starting the alsamixer in terminal to check my audio settings, default card, etc.. Checked volume control for all the obvious things like mute, low volume, etc.. It's not anything silly like this.. I then tried killing and restarting the services numerous times, for both alsa and pulseaudio.. No luck.. I then took things a step further and listened to the advice I was getting in online searches, so I removed alsa and pulse audio via the terminal (I don't remember what the exact commands were as I did this a few days ago but they were rm and purge commands for alsa and pulseaudio that I found in ubuntu forums). It looks to have uninstalled it, because I now no longer have a volume icon in my task bar, nor do I have the option of even opening the volume control anymore.. The problem, now, is that I can't re-install the audio drivers.. When I run the sudo apt-get commands to download and install alsa and pulse audio drivers, I get a message saying something along the lines "Already newest version no changes made".. So, it looks as if I've uninstalled my audio drivers, in an attempt to fix them, but now I can't re-install them because it seems the operating system is confused and thinks they're still installed...

What can I do here? Will upgrading to 19.04 fix my problem and re-install the audio drivers? Should I just wipe the drive and start over? Because, I don't want to waste hours or days trying to get audio working if I re-install of the OS will just fix the problem..

---

### Post by CatKiller on 2019-11-09
> **iconoclast12 said:**
> In my volume control panel, the only output device that was available (and what it was set to) was analog audio. I'm on HDMI, since that's the only video output on this device (I also want to and NEED to use HDMI). 

OK, so whichever chip provides audio over the HDMI isn't being automatically detected.

> So, the first thing I did was google "no audio in Lubuntu 18.04" 

...which isn't the issue you're having: you *have* audio, just not using the device you want to use.

> and found that several others were having the same issue. First things I tried, were starting the alsamixer in terminal to check my audio settings, default card, etc.. Checked volume control for all the obvious things like mute, low volume, etc.. It's not anything silly like this.. I then tried killing and restarting the services numerous times, for both alsa and pulseaudio.. No luck.. 

Well... no. None of that would help.

> I then took things a step further and listened to the advice I was getting in online searches, so I removed alsa and pulse audio via the terminal (I don't remember what the exact commands were as I did this a few days ago but they were rm and purge commands for alsa and pulseaudio that I found in ubuntu forums). 

That advice would have been 100% pure unmitigated nonsense. Removing packages doesn't *change* anything. I mean, it *breaks* stuff, because you no longer have important packages, but reinstalling them makes you no better off than you were before - and probably worse off because you broke everything. Linux is not Windows.

> It looks to have uninstalled it, because I now no longer have a volume icon in my task bar, nor do I have the option of even opening the volume control anymore.. The problem, now, is that I can't re-install the audio drivers.. When I run the sudo apt-get commands to download and install alsa and pulse audio drivers, I get a message saying something along the lines "Already newest version no changes made".. So, it looks as if I've uninstalled my audio drivers, in an attempt to fix them, but now I can't re-install them because it seems the operating system is confused and thinks they're still installed...

Well, yes, you've broken it. The things you're trying to reinstall aren't the same as the things you removed, because you copied some random commands off the Internet that you didn't understand and now can't remember what you did.

> What can I do here? Will upgrading to 19.04 fix my problem and re-install the audio drivers? 

No.

Upgrading a working system sometimes fails. Upgrading a broken system will either give you an upgraded broken system or a broken upgraded system.

In any case, new users shouldn't be using the guinea pig releases and should be using the Long-Term Support releases.

> Should I just wipe the drive and start over? Because, I don't want to waste hours or days trying to get audio working if I re-install of the OS will just fix the problem..

A new install takes about 20 minutes. A bit less if you've done it before, a bit longer if you're reading everything or have specific requirements.

Whether that's the right solution for a given user depends on whether they'll get anything out of playing around with a broken system. For some people, the experience is worthwhile, or having the existing system working again is more important than having any old working system, or it's just a tiny fix. For others, a rapid nuke-and-reinstall is the quickest, easiest option.

---

### Post by iconoclast12 on 2019-11-09
Okay, well you've cleared up some of my questions, but how do I fix it? Is there seriously no way to re-install audio drivers? Is there a way to fix it easily wothout re-installing the OS? Do I just need to start over?

---

### Post by CatKiller on 2019-11-09
> **iconoclast12 said:**
> Is there seriously no way to re-install audio drivers? Is there a way to fix it easily wothout re-installing the OS?

A whole bunch of packages likely depended on the packages you purged (which you can't remember), which *wouldn't* be "suggested" or "required" by those packages and so wouldn't be automatically installed. 

The drivers are part of the kernel; they're still there. You've just mucked up being able to configure or access them. As well as goodness-knows what else. 

Reinstalling the *lubuntu-desktop* meta-package *might* pull in the dependencies and dependencies of dependencies and so on that you ripped out, or it might not. 

> Do I just need to start over?
It's up to you. A reinstall would ultimately have taken less time than posting here. Fixing it will help you learn about the command-line history and package management, and the audio stack, but you'll be out of action for longer. 

Poking things till they break, then trying to fix it again, and occasionally giving up and reinstalling is how I, and a lot of people here, started their Linux adventures. 

The most important lesson - don't run random commands that you found on the Internet without first understanding what they do - I'd say you've already learned now. There's no shame in a reinstall, but you might find the process of fixing things again interesting; only you can answer that one.

---

### Post by iconoclast12 on 2019-11-09
For whatever reason, updating from 18.04 to 19.04 seems to have fixed my audio problem.. HDMI device now shows up in the volume control panel and my volume slider is back..

*shrug*

I'm satisfied.

---

