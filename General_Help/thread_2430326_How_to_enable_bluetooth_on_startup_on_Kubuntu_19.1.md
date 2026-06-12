---
title: "How to enable bluetooth on startup on Kubuntu 19.10"
date: 2019-10-30
forum: General Help
---

### Post by Buuntu on 2019-10-30
Having a hard time enabling bluetooth on startup on 19.10.  I edited /etc/bluetooth/main.conf so that it has the lines:
```

[Policy]
AutoEnable=true
DiscoverableTimeout = 0

``` 
Yet I still have to go to "Bluetooth Adapters" and manually select "Enable" every time I log on.

---

### Post by #&amp;thj^% on 2019-10-31
First 19.10 is a point release, and bound to have a few bugs for some.
I can see how that has worked on older Versions of Buntu, I have this for mine:
I install these first:
```
sudo apt install pulseaudio pulseaudio-utils pavucontrol pulseaudio-module-bluetooth
```
and my edit to "**/etc/bluetooth/audio.conf**"
```
sudoedit /etc/bluetooth/audio.conf
```
Then I add this:
```
This section contains general options
    [General]
    Enable=Source,Sink,Media,Socket
```
Then I restart the service with:
```
sudo service bluetooth restart
```
This will/should start by default in a2dp (high fidelity) mode.
If not let me know, there is a few other tricks here.
EDIT: if this dose not work for you include this please:
```
dpkg --status bluez | grep '^Version:'
```

---

