---
title: "WINTV HVR 900 - appears installed doesn't work"
date: 2007-11-27
forum: General Help
---

### Post by desertboy on 2007-11-27
Installed as per [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

dsmeg gives

> [   34.543647] tveeprom 0-0050: Hauppauge model 65018, rev B2C0, serial# 2093678
[   34.543649] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   34.543651] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   34.543653] tveeprom 0-0050: audio processor is None (idx 0)
[   34.543655] tveeprom 0-0050: has radio
[   34.543656] setting new tuner type now 71!
[   34.545784] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[   34.545794] attach inform (default): detected I2C address c2
[   34.545796] /home/stuart/driver/v4l-dvb-kernel/v4l/tuner-core.c: setting tuner callback
[   34.545798] tuner 0x61: Configuration acknowledged
[   34.545800] /home/stuart/driver/v4l-dvb-kernel/v4l/tuner-core.c: setting tuner callback
[   34.669022] /home/stuart/driver/v4l-dvb-kernel/v4l/xc3028-tuner.c: attach request!
[   34.669025] /home/stuart/driver/v4l-dvb-kernel/v4l/tuner-core.c: xc3028 tuner successfully loaded
[   34.674868] attach_inform: tvp5150 detected.
[   34.736703] tvp5150 0-005c: tvp5150am1 detected.
[   34.826665] Loading base firmware: xc3028_init0.i2c.fw
[   35.915335] Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
[   35.961435] xc3028-tuner.c: firmware 2.7
[   35.961437] ANALOG TV REQUEST
[   35.966465] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   35.968182] em28xx #0: V4L2 device registered as /dev/video0
[   35.968184] em28xx #0: Found Hauppauge WinTV HVR Rev. 1.2
[   35.968197] usbcore: registered new interface driver em28xx
[   36.104290] em28xx-audio.c: probing for em28x1 non standard usbaudio
[   36.104292] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   36.104671] Em28xx: Initialized (Em28xx Audio Extension) extension
[   38.102922] em2880-dvb.c: DVB Init
[   38.102924] em2880-dvb.c: unsupported device
[   38.102926] em2880-dvb.c: failed initializing zl10353 DVB-T demodulator
[   38.102927] em2880-dvb.c: retrying with mt352 DVB-T demodulator
[   38.103280] FIXME:em28xx_i2c_send_bytes(1e): write failed:
[   38.103281] ===============================
[   38.103283] 7f 
[   38.103284] ================================
[

Which suggests to me it's working but neither tvtime nor kaffeine see it or work. Any suggestions.

---

### Post by desertboy on 2007-11-30
bump

---

### Post by desertboy on 2007-12-06
Bump and if anyone has ideas on getting this to work on my PS3 w/Ubuntu installed I would appreciate it.

Although ust working on my Gutsy PC install would be nice.

---

### Post by tomplast on 2007-12-11
I'm not sure if we have the same revision but I also have a HVR 900 usb stick. The one I have (and possibly yours too) uses the drx3975d dvb-t modulator which isn't supported yet. But one guy (Markus Rechberger) is currently working on and before he or someone fixes it dvb-t wont work.

P.S I will also use it in my PS3 to record and watch tv ;).

---

### Post by desertboy on 2007-12-19
Unfortunately I can't even get analog tv working

---

### Post by mbriscatosta on 2008-04-18
just upgraded to hardy - same exact problem to me

if i modprobe em2880_audio the result i s SEGFAULT!
maybe the userspace drivers need some refining: i'll stick back to gutsy until something new happens for 2.6.24

---

### Post by mvillarejo on 2008-04-21
hi, I've got a worst problem i think, because I jsut want to use it for my PC with ubuntu or mythubuntu, and follwoing the installation procedure....there are no errors on the process, but even the usb lights are on at the end... :(

any idea?
MV

---

