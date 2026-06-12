---
title: "usb audio in and skype problem"
date: 2006-10-26
forum: General Help
---

### Post by theslut on 2006-10-26
I have two sound cards, a terratec and a usb audio phone. Both worked just fine in Dapper but since installing edgy I cannot record my voice with the usb phone.

If i set the audio conferencing properties to "usb audio" for playback and recording and try the test signal i get this error when recording

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink
profile=chat:Resource Busy or not available

The light on the phone is green which tells me the mic is enabled. if i toggle the "rec" on gnome mixer the light turns to orange.

---

### Post by ssam on 2006-10-26
it might be this [https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/68128](https://launchpad.net/distros/ubuntu/+source/alsa-driver/+bug/68128)

basically in edgy usb sound devices are given a lower priority to stop web cams becoming the default sound device. but its a bit of a pain if you want the usb to be the main sound card.

---

### Post by theslut on 2006-10-26
nah its not that.

I can play sound just fine. It's recording that doesn't work.

It's a bit annoying cos the sound setup would have been perfect and I wouldnt be facing the problem of the desktop sounds coming through the USB and having to unplug without risk sodding up the main sound card.

---

### Post by dam :) on 2006-11-08
I have the same problem :(

---

