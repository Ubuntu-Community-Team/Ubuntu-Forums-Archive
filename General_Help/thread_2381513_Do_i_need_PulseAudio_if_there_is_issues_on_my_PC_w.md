---
title: "Do i need PulseAudio if there is issues on my PC with it?"
date: 2018-01-01
forum: General Help
---

### Post by michael14 on 2018-01-01
So I ran into static issues on my speakers and headphones on my PC and running Pulseaudio -k seemed to clear it up.. I'm just wondering would there be any issues with running 

sudo apt-get remove pulseaudio

I made a topic of this on here earlier like a week ago and never got a single reply.. here is the video of the static i have been having.. [https://youtu.be/iirmn9KKz7k?t=46](https://youtu.be/iirmn9KKz7k?t=46)

Its the GA 970A DS3P FX rev 2.1 Motherboard. I just want my Audio to work like it did in Windows. Any ideas please somebody reply to this and let me know if I could use Alsa without pulseaudio perfectly fine and have everything work like it would in windows.

---

### Post by michael14 on 2018-01-01
I found more info about my Audio device in the BIOS.. It says its HD Audio Azalia

---

### Post by Yellow Pasque on 2018-01-01
> I'm just wondering would there be any issues with running
sudo apt-get remove pulseaudio

See #2 here: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

>  running Pulseaudio -k seemed to clear it up.. 
By default, pulseaudio respawns itself. So unless you disabled that, you were still using pulseaudio for output.

> Any ideas please somebody reply to this and let me know if I could use Alsa without pulseaudio perfectly fine and have everything work like it would in windows.
I don't think anyone can give you a definite answer to this without knowing what exactly is causing the issue. You can try a LiveUSB of Lubuntu 16.04.1. It came without pulseaudio (though if you install and upgrade Lubuntu, it installs pulseaudio so sound will work in Firefox).

---

### Post by michael14 on 2018-01-01
> **Temüjin said:**
> See #2 here: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)


By default, pulseaudio respawns itself. So unless you disabled that, you were still using pulseaudio for output.


I don't think anyone can give you a definite answer to this without knowing what exactly is causing the issue. You can try a LiveUSB of Lubuntu 16.04.1. It came without pulseaudio (though if you install and upgrade Lubuntu, it installs pulseaudio so sound will work in Firefox).

So would my best bet to be to deal with it, or get a cheap pci or pcie sound card and switch off the Azalia sound device? I noticed there was an option on it labelled "Auto"

---

### Post by Yellow Pasque on 2018-01-01
If it was me, I would try and troubleshoot it before spending money. Looking at your original report, if running that set of commands fixes the issue until reboot, maybe just put them in a startup script. Is it necessary to delete the config files every time, or does killing/restarting pulse work?

Other ideas:
- If you have a spare USB stick (and the bandwidth), try Lubuntu 16.04.1 to see if it happens without pulseaudio
- [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by cruzer001 on 2018-01-02
I once had a unit with audio static and dumb luck lead me to a fix.  It turned out to be a bad audio jack that would feed back thought the audio system.

The fix:  HDA Jack Retask.

Install it in terminal:
```
sudo apt install alsa-tools-gui
```

Then go to Sound&Video in your main menu and pull up HDA Jack Retask.

In the very first box change from whatever its set to; to "Headphones" or "Speakers" (I don't remember which one worked for me).

May work for you.  Good luck

---

