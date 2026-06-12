---
title: "[SOLVED] Switch Default Soundcard"
date: 2008-01-29
forum: General Help
---

### Post by ibuclaw on 2008-01-29
Hi, anyone know how to switch the default soundcard from A to B?

Or more specifically:
SiS from hw:0 to hw:1
USB Audio from hw:1 to hw:0

and furthermore setting it up so the USB Audio is the default output for most (if not all) sound producing programs.

Maybe blacklisting the SiS soundcard (if someone can give me a name for the device to put in the blacklist file)

I've tried asound-gtk, all it shows is "SiS" "default" and "PulseAudio." Neither seem to have a desired effect.

Or if someone know a program like that of KDE's soundcontroller, that would be great... I'd feel much better off having to type in "hw:1" and knowing that its gonna keep :D

Sorry for my vagueness, if you ask questions I will reply as best I can, thank-you

Iain

---

### Post by ibuclaw on 2008-01-29
Nevermind, I sorted it (sorry)
nano'd /etc/modprobe.d/alsa-base file with the configuration:
          options snd-usb-audio index=0
rebooted and now it's good, set asoundconf to "default" in the terminal
          $ asoundconf set-default-card default
and everything seems to be working under my Zoom.G2.1u pedal now! My I have a nice little temporary thing going until my RME HDSP card comes through ;-)

Iain

---

