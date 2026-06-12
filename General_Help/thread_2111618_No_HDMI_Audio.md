---
title: "No HDMI Audio"
date: 2013-02-02
forum: General Help
---

### Post by Kissell on 2013-02-02
When I do "aplay -l output" I can see my HDMI audio listed as "card 1".  However, when I go to SOUND SETTINGS I only see the Analog and Digital outputs from "card 0".  Nothing from card 1 shows up, so I can't select HDMI output.  

> 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by gavinjb on 2013-02-02
Not sure if this helps, but I had a similar problem in the past with an ATI Graphics Card and the problem was that I had not installed the propitiatory drivers.

What Graphics Card do you have that you are using the HDMI from?

---

### Post by Kissell on 2013-02-02
Huh...  I thought about that...  I don't need the proprietary drivers, my video is fine without them.

Whenever I try to install the proprietary drivers it breaks my system.

It's an ATI Radeon 6450 card.  And I've tried to install the drivers from their website, the latest 13.1, and it doesn't work.  After I install the drivers I no longer get any Unity interface.

---

### Post by Yellow Pasque on 2013-02-02
Try workaround #1 here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by gavinjb on 2013-02-02
That Sounds Familiar, I had the same issue where if I installed the Graphics Drivers sound worked through HDMI, but after rebooting the Graphics were messed up. In the end I went for having sound through the normal Jack Ports.

---

### Post by Kissell on 2013-02-02
I can't use any other audio output than HDMI.  It must be HDMI for this setup.

This sounded promising, but it made the computer unbootable.  

> 
Edit /etc/default/grub and change this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to this line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

Now run "sudo update-grub", then reboot your computer.

---

### Post by Yellow Pasque on 2013-02-02
It shouldn't make your computer unbootable unless you screwed up the syntax or used libreoffice to edit the file. Double-check it..

---

### Post by Kissell on 2013-02-02
I used "vi" to edit it from the command line of that machine.  It's just as shown here.

I'm just going to re-install the OS.

---

