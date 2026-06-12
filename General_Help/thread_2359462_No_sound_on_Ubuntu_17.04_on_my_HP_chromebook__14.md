---
title: "No sound on Ubuntu 17.04 on my HP chromebook  14"
date: 2017-04-24
forum: General Help
---

### Post by metadax on 2017-04-24
Hi everyone,

I would like to know how to get sound on my HP chromebook 14 with Ubuntu 17.04. When I go to Settings > Sound, it doesn't detect the sound card. I've tried to uninstall ALSA and pulseaudio and reinstall them, didn't work either. 
Something that you should know, I have a ppa launchpad with the url "http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu" that never seem to work (always impossible to find), so I don't know how to get it to work.

What should I do?

Thanks in advance.

---

### Post by RobGoss on 2017-04-24
Hello and welcome to the forum, Have you checked to see if anything was muted?

Run the following command and post the results using the code tags
```
 lspci 
```

Yon can also run this from the terminal

```
 alsamixer
```

Make sure the levels are at the highest point

---

### Post by metadax on 2017-04-25
lspci results : 

00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
01:00.0 Network controller: Intel Corporation Wireless 7260 (rev c3)

And for alsamixer, I have this and I don't know if it's muted or something.

[IMG]http://i.imgur.com/NtlYtaJ.png[/IMG]

---

### Post by widewi on 2017-04-25
same for me with the board below. only the audio hdmi was recognised, the other options including analog 5.1. were not there. I ended up reinstalling ubuntu 16 and audio works fine again. I can post the full ALSA Information Script v 0.4.64 output if wanted, yet I personally need no support on this.
===
Firmware Version:  2101   
Board Vendor:      ASUSTeK Computer INC.
Board Name:        M5A78L-M/USB3

---

### Post by RobGoss on 2017-04-25
When you run the live installer do you have sound?

---

### Post by metadax on 2017-05-03
No

---

