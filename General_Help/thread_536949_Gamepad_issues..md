---
title: "Gamepad issues."
date: 2007-08-28
forum: General Help
---

### Post by nrgenova on 2007-08-28
Alright, so my gamepad has always run straight from the default install of Ubuntu. It is a cheap USB Logitech something or other. No problems.

Yesterday, I forced an X server reset with ctrl+alt+backspace after X froze up while playing a game on the pSX emulator. Ever since then, my gamepad has not been functioning. I have tried modprobbing every driver I could think of that it might need, but no dice. Sometimes I can get the buttons to work, but the D-pad and the joysticks still have no response.

I think something broke when I reset X. I remember something random broke last time I reset X too. Ubuntu doesn't like resetting X.

Anyone have any idea? I can't find anything on this.

Edit: In the recent past, i've been having the same problem when modprobbing the sidewinder module for my gameport. It always seems to 'block' my usb gamepad from being read.

---

### Post by nrgenova on 2007-08-28
I don't know what caused the problem initially, but jscalibrator was the culprit. Ran an apt-get remove jscalibrator, and the gamepad is working fine.

---

