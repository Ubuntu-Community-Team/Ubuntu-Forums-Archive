---
title: "[SOLVED] Volume Control not working"
date: 2008-05-18
forum: General Help
---

### Post by melenor on 2008-05-18
My volume control doesn't work i change the volume but it doesn't effect any of the sounds or music. Also my volume control on keyboard and mouse don't seem to work anymore either, so i am unable to change sound from mouse, keyboard, and tray. the keyboard and mouse volume seem connected but the tray volume icon doesn't change no matter what i do with the keyboard or mouse.

---

### Post by ryanhaigh on 2008-05-19
You could try changing the device that the volume-applet controls, on my systems I use front and PCM.

---

### Post by melenor on 2008-05-19
That seemed to work but for some reason looking at the name the one that worked was the motherboard nvidia but yet i have the speakers connected to Audigy sound card. i still can't get the mouse or keyboard volume to work.

---

### Post by ryanhaigh on 2008-05-19
You could try making sure that the keyboard shortcuts have been setup properly in system>preferences>keyboard shortcuts.

---

### Post by melenor on 2008-05-19
how do i tell if the shortcuts have been set properly, Volume down is 0xae, and Volume up is 0xa2

---

### Post by ryanhaigh on 2008-05-19
Click where the shortcut is defined to change it, then press the relevant key on your keyboard.

---

### Post by melenor on 2008-05-20
alright i did that the only one that changed was the volume down and it still doesn't seem to affect the volume applet which is set to "Audigy 1 ES [SB0160] (Alsa mixer)" switch the device around i found that the volume on keyboard and mouse effected "NVidia CK804 (Alsa mixer)" but on that device i had no sound anyway. also the volume applet effects "PCM Front" on "Audigy 1 ES [SB0160] (Alsa mixer)" but keyboard and mouse effect "Master" on "NVidia CK804 (Alsa mixer)" so even if i got both to work on same device they would both control a different type of volume meaning that i need to get the Volume Applet to work with Master volume not PCM Front and get the keyboard and mouse volume controls to work on "Audigy 1 ES [SB0160] (Alsa mixer)". Thank you everyone

---

### Post by melenor on 2008-05-21
I need to find a peferences for which volume the buttons on mouse and keyboard control, switch which device it affects volume.
and i need to find out how to make the volume applet change the master volume.
thanks.

I was able to find it by going into my sound options and double checking them, somehow a few of the options got turned around.
Thanks Everyone.

---

