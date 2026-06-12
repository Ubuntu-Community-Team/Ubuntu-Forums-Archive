---
title: "Blueman: Connecting Headset"
date: 2013-10-01
forum: General Help
---

### Post by SWGraphics291 on 2013-10-01
Im using Ubuntu 12.04 to connect my Jabra headset with my computer on blueman (Same as gnome-bluetooth). I can connect them easily, but when I answer a skype call all the sound goes to the built-in stereo in my computer. I would like to know how to make all of the sound go to my headset.

PLEASE DONT SAY USE gnome-bluetooth (I have a phone that will only work with blueman, not gnome-bluetooth).

---

### Post by tgalati4 on 2013-10-01
Does the Jabra/bluetooth audio not show up in Skype Audio Output preferences?

Use *gnome-bluetooth*.

---

### Post by SWGraphics291 on 2013-10-02
No my Jabra dos'nt appear in the skype audio prefrences.

---

### Post by tgalati4 on 2013-10-02
Post the output of /etc/bluetooth/audio.conf.  What bluetooth chip do you have in your computer?

```
lsusb | grep Bluetooth
```

---

### Post by SWGraphics291 on 2013-10-02
I used:

> ```
lsusb | grep Bluetooth
```

and got:

```
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

---

### Post by SWGraphics291 on 2013-10-02
This is whats in the file:

```
# Configuration file for the audio service

# This section contains options which are not specific to any
# particular interface
[General]

# Switch to master role for incoming connections (defaults to true)
#Master=true

# If we want to disable support for specific services
# Defaults to supporting all implemented services
#Disable=Control,Source

# SCO routing. Either PCM or HCI (in which case audio is routed to/from ALSA)
# Defaults to HCI
#SCORouting=PCM

# Automatically connect both A2DP and HFP/HSP profiles for incoming
# connections. Some headsets that support both profiles will only connect the
# other one automatically so the default setting of true is usually a good
# idea.
#AutoConnect=true

# Headset interface specific options (i.e. options which affect how the audio
# service interacts with remote headset devices)
[Headset]

# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true

# Maximum number of connected HSP/HFP devices per adapter. Defaults to 1
MaxConnected=1

# Set to true to enable use of fast connectable mode (faster page scanning)
# for HFP when incomming call starts. Default settings are restored after
# call is answered or rejected. Page scan interval is much shorter and page
# scan type changed to interlaced. Such allows faster connection initiated
# by a headset.
FastConnectable=false

# Just an example of potential config options for the other interfaces
#[A2DP]
#SBCSources=1
#MPEG12Sources=0
```

---

### Post by tgalati4 on 2013-10-02
Start changing these values one at a time.  Make a backup of the file first, then add comments as you change each one.  You might have to reboot between changes or reload the bluetooth stack after each change.

This one looks like a candidate to change:

#SCORouting=PCM

Set to:

SCORouting=PCM

```
sudo service bluetooth restart
```

Take careful notes of each change and document the behavior after the change.  You have to become the expert in this problem, since you have a unique use case and unique hardware.

You need to understand that bluetooth headset devices have profiles like HSP (headset profile--low fidelity, earpiece microphone, auto-answer calls, etc).  Then there is A2DP which is a high fidelity audio headphone protocol.  Since Skype uses high-fidelity codecs, it may only work with A2DP profile and your headset may not support A2DP.

Perform a search for *bluetooth a2dp* in the following link and read through many, many similar threads:  [https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)

Post the solution that finally fixes your problem.

One of many hits for the search above:

[http://askubuntu.com/questions/287254/ubuntu-13-04-bluetooth-a2dp-does-not-work](http://askubuntu.com/questions/287254/ubuntu-13-04-bluetooth-a2dp-does-not-work)

---

### Post by SWGraphics291 on 2013-10-02
My Jabra headset does support A2D2. I will now try changing the file. Thanks

---

### Post by SWGraphics291 on 2013-10-02
Im going to try the link, see if that works.

---

