---
title: "Upgraded 22.04 to 22.10, now Bluetooth speakers won't connect"
date: 2022-12-30
forum: General Help
---

### Post by ephemerian on 2022-12-30
I've just updated my system from Jammy to Kinetic. As far as I can see, the update went smoothly enough but ... now I have no sound. Specifically, the only output device I have is `Dummy Output`, and in particular my Edifier Exclaim Bluetooth speakers, which were working just fine in 22.04, don't connect any longer.

If I go to the Bluetooth tab on Settings, I can see my device listed as paired, but when I click on the `Connection` toggle the toggle goes briefly on then immediately back to off.

If I remove the Edifier device and then re-pair it, pairing seems to work but I get the same behaviour on connection, and still no sound device listed.

I'm not sure where to look for additional diagnostics to try to find out what's going wrong in the BT connection process. Would appreciate any suggestions!

---

### Post by ephemerian on 2022-12-30
Actually, it appears to be even worse. Not only is the Bluetooth sound not working, if I plug-in a set of normal, wired headphones Kinetic does not even see those as a sound device! 

Argh. I thought we were past all these kinds of problems on Linux :(

---

### Post by ephemerian on 2022-12-30
This [AskUbuntu answer]("https://askubuntu.com/a/1438019/13799") has helped me get the basic sound devices back. Still no Bluetooth connection to my speakers though.

---

### Post by ephemerian on 2022-12-30
For the benefit of others in the future, I managed to solve this.

First I ran [FONT=Courier New]bluetoothctl[/FONT] in a terminal, then [FONT=Courier New]list[/FONT] to see my devices, then [FONT=Courier New]connect <the device id>[/FONT]. This gave an error message 

[FONT=Courier New]Bluetooth connect failed: br-connection-profile-unavailable.[/FONT]

Searching for solutions to that, I read suggestions that the Bluetooth controller didn't have the right dependencies. I apt installed [FONT=Courier New]libspa-0.2-bluetooth[/FONT] (description includes "This package contains a plugin to make Bluetooth audio devices such as speakers and headsets available to the PipeWire server."). For good measure, I also trusted the Edifier device in [FONT=Courier New]bluetoothctl[/FONT]. After rebooting (may not be necessary, I could maybe have got away with restarting the [FONT=Courier New]pipewire[/FONT] service) I have sound on my Bluetooth speakers again.

---

### Post by thiagoms832 on 2023-03-07
This worked for me! I had uninstalled pulseaudio from Ubuntu and then installed it again but it came missing the bluetooth library you mentioned. Thanks for the solution.

---

### Post by helliondarklord2 on 2023-09-23
> **thiagoms832 said:**
> This worked for me! I had uninstalled pulseaudio from Ubuntu and then installed it again but it came missing the bluetooth library you mentioned. Thanks for the solution.


I got this... still no output device available in the sound settings in settings
$ bluetoothctl
Agent registered
[onn cd bmbx gy]# 


I restarted Ubuntu and still no output available in the drop down. WHen I pull my headphones out is goe to realtec speakers (Onboard speakers)

I hope we can get this resolved

Hellion DarkLOrd

EDIT:: I didn;t see what I was quoting and now I'm trying the PulseAudio stuff.

---

### Post by dragonfly41 on 2023-09-24
Nobody seems to mention Bluetooth Manager (GUI) which I use on Ubuntu 20.04.
I use it for Bose speakers, Headphones, Logitech Keyboard and Mouse, Mobile phone, Galaxy etc.

---

