---
title: "bluetooth won't pair"
date: 2017-03-17
forum: General Help
---

### Post by HC48 on 2017-03-17
Good morning.
 I have a PC with 14.04 LTS and a laptop with 12.04. My bluetooth paired on both computers with a vibro speaker (via usb pluggable) but would not pair with my new Akai ABT-52 SYDNEY speaker. Both computers saw the new device but wouldn't pair. I use a usb plugable to get bluetooth and have installed and reinstalled Bluetooth, Bluetooth support, Bluetooth manager, Bluetooth transfer, Bluetooth device setup and Pulse Audio Volume Control.
Previously my vibro speaker paired and worked fine but since I have tried to enable pairing with the new Akai speaker it no longer pairs either. I did 'sudo gedit /etc/bluetooth/main.conf and changed '#Remember powered=false ' to 'Remember powered=true' as advised in one forum. Here are the packages as they appear in synaptic:

[ATTACH=CONFIG]274187[/ATTACH][ATTACH=CONFIG]274188[/ATTACH]

(I hope I did that right.)
My new device (Akai speaker) comes with a PIN (1234) but Bluetooth manager tells me to use 0000. It lists it as ABT-52 Headset 00:1D: 1F:64:01:F3 . What options should I try in Bluetooth manager to pair with this device? Only the options 'proceed without pairing' and 'Don't connect' in setup allow me to add the device. 
Bluetooth manager also sees my vibro speaker but, when switched on at the source, when I try to switch it on using the bluetooth applet at the top of my screen a padlock appears briefly and it switches off. When both devices are off at the source I can switch them to ON in the applet menu.
Both devices appear in the applet list but not in the sound settings even when they are on.
Can you please advise me what I can do now? 
I can use the terminal but am not comfortable with it. I am more comfortable using synaptic or simply the logitec store.
Thank you for any help.

---

### Post by HC48 on 2017-03-17
I have solved this problem:"Previously my vibro speaker paired and worked fine but since I have  tried to enable pairing with the new Akai speaker it no longer pairs  either." by uninstalling Bluetooth manager, removing my devices and starting from scratch using bluetooth settings. I think Bluetooth manager was creating interferences when I used its setup.

---

### Post by HC48 on 2017-03-20
I have solved the problem. In fact it was a missing point in the instructions on the speaker. I just had to hold the blue led button down for a couple of seconds for it to connect!):P

---

