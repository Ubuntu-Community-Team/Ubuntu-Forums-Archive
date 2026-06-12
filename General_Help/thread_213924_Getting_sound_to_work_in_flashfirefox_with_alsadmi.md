---
title: "Getting sound to work in flash/firefox with alsa/dmix"
date: 2006-07-12
forum: General Help
---

### Post by lastexyle on 2006-07-12
Originally, I had firefox and flash working fine (for the most part) by setting aoss in firefoxrc. However, i recently set up a customized asound.conf (to fix sound quality and latency). Now all my alsa apps work great (no noticable latency, good quality, etc). But now flash causes firefox to freeze when it tries to play sound.

Here's my asound.conf:
```

ctl.mixer0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 48000
}
bindings {
0 0
1 1
}
}

```
Any ideas?

---

### Post by hanzomon4 on 2006-07-12
Go to System>Administration>Sound and see it says something about esd. Try turning esd on or off. Also look for howtos for configuring esd.

I could help more if I knew what kind of sound card you have.

---

### Post by lastexyle on 2006-07-12
Builtin sound on an nforce3 mainboard. I don't have esd running, but starting it up doesn't seem to make much difference.

---

### Post by hanzomon4 on 2006-07-12
Make sure you have aoss installed I don't think its there by default. I found some info on the gentoo forum for "nforce2" cards about firefox freezing here's the [link]("http://gentoo-wiki.com/Talk:HOWTO_ALSA_Complete_(includes_dmix)") hope it helps. > ########
# AOSS #
########
# OSS dsp0 device
pcm.dsp0 {
     type plug
#    slave.pcm "duplex" #### DOESN'T WORK
     slave.pcm "dmix" #### WORKS
}
Here is a more complete howto [link]("http://gentoo-wiki.com/HOWTO_ALSA_Complete_%28includes_dmix%29#dmix_Configuration_for_OSS_Emulation")
Scroll down their should be a section on getting apps that use oss/aoss to use the dmix plugin

---

### Post by lastexyle on 2006-07-15
Tried the gentoo guide, but flash still crashes, any other ideas?

---

