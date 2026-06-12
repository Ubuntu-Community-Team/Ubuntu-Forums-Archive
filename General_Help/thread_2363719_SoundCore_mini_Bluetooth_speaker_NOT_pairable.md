---
title: "SoundCore mini Bluetooth speaker NOT pairable"
date: 2017-06-13
forum: General Help
---

### Post by antnh6 on 2017-06-13
[ATTACH=CONFIG]275623[/ATTACH]

I just bought a SoundCore mini bluetooth speaker and have been trying to pair it with my Ubuntu Unity for two days to no avail. I am pretty new to Ubuntu (2 wks). I used to have the bluetooth thingie that came with the system (whose icon was next to the wifi signal), but now it's gone and replaced with Bluetooth Manager from Bluez I believe, probably because I have tried installing/uninstalling stuff as advised in old posts . One weird thing that happens when I try pairing the speaker is that the Manager asks to confirm or deny some six-digit number before letting me proceed to the next step. Then there is a connection for like 3 seconds as I can see three bars showing up right next to my speaker icon before "Failed to add device".  Please help!

---

### Post by aromo2 on 2017-06-13
I had a similar issue with an Ultimate Ears Bluetooth speaker. Only way to get it working again was installing the most recent Bluez from [http://www.bluez.org/download/](http://www.bluez.org/download/)

In my case, somehow Bluetooth broke to the point that not even re-installing the same version, or deleting its config directories would fix it.

---

### Post by jeremy31 on 2017-06-13
I would see if you can pair to it using terminal
```
bluetoothctl
```
Then you can type
```
power on
scan on
```
Hopefully it will find your headphones and show the MAC address, replace {MAC} in the following commands with the address- use capital letters
```
pair {MAC}
trust {MAC}
connect {MAC}
```
Then use CTRL + d to exit the terminal app and if the headphones paired, see if they show in sound settings

---

### Post by antnh6 on 2017-06-13
Thanks so much guys.:p:p It was indeed a problem with Bluez. I tried installing it and found out that I was missing a bunch of dependencies, then I installed them by following this post [http://rrbluetoothx.blogspot.ca/2016/04/rr-bluetooth-compile-bluez-539.html](http://rrbluetoothx.blogspot.ca/2016/04/rr-bluetooth-compile-bluez-539.html). Then I run bluetoothctl, followed the above code and it is all up and running now. THANKS SO SO MUCH!

---

### Post by sup2069 on 2017-06-24
Bluez version was 2 behind on Debian 9 Stretch. Compiled new version and viola! Thanks! :D

---

### Post by daniele.pozzi76 on 2018-01-07
Hello, similar issue here, with Xubuntu 16.04 and bluetoothctl --version 5.37... No idea if installing Bluez 5.48 could solve something (and how to do it in the sound way).

First, trying to set my SoundCore through Blueman I got a system error which suggest me to install some libraries (*libdrm-amdgpu1 libdrm2 libegl1-mesa libgbm1 libgl1-mesa-dri libwayland-egl1-mesa* done... )

Then I tried the suggest procedure via bluetoothctl console. no problems to discover and pair the device, but impossible to connect it. Error message: 
```
[SoundCore mini]# connect XX:XX:XX:XX:XX:XX
Attempting to connect to XX:XX:XX:XX:XX:XX
Failed to pair: org.bluez.Error.Failed
Failed to connect: org.bluez.Error.Failed
```
I installed the libraries suggested (libdbus-1-dev libudev-dev libical-dev libreadline-dev glib2.0) and I download the [bluez-5.48.tar.xz]("http://www.kernel.org/pub/linux/bluetooth/bluez-5.48.tar.xz") file. I tried to compile it in the Home directory (everything well), however I don't know where I should build it to have it in the right path, and how to get rid of the old version without messing the system...

Could you please give me some suggestion?

Thank you very much!

daniele

---

