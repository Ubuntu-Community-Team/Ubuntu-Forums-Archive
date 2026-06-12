---
title: "Webcam Trouble"
date: 2015-10-27
forum: General Help
---

### Post by courseinmiracles2 on 2015-10-27
Hmmm, It started with my webcam dropping out while I was using skype and gradually changed to not working and Now the LED light is constantly on, even through a restart.

I am running 15.04 ( toshiba Laptop...maybe 8 years old) and can not find a solution to this anywhere. I am not sure if it is hardware or software and because "no device found" while running "cheese" I don't know if the webcam is on or its just the LED...

lsusb:
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any Ideas?

---

### Post by tgalati4 on 2015-10-27
Sounds like it is worn out.  If you don't see the webcam in *lsusb*, then it is offline--and not working.

You can try forcing the video driver and see if it wakes up:

```
sudo modprobe -if uvcvideo
```

Post any errors.

Take the laptop apart and examine the wires that go through the hinges.  Chances are you have a worn-out USB cable that is causing the camera to fail.  Try moving the screen back and forth slowly to see if the behavior changes.  If it does, then you know the problem.

---

### Post by courseinmiracles2 on 2015-10-27
Thanks for the reply.
On rebooting this morning the LED is not on

ran - sudo modprobe -if uvcvideo
code output:
modprobe: ERROR: could not insert 'uvcvideo': Exec format error

Does this error mess. tell you anything? There isn't much info on it around the traps.

I will have a look at taking the laptop apart later today...

Thanks again

---

### Post by courseinmiracles2 on 2015-10-27
UPDATE:
I took the front off the laptop and checked the connection going into the webcam and it seemed OK.
rebooted and ran lsusb and modprobe again and got the same results...

???

---

### Post by tgalati4 on 2015-10-27
Post *lsmod*:

It should look something like:

> uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core


This assumes that your webcam uses the *uvcvideo* driver.  Yours may use something different.  There is no output if it loads successfully.  I don't recognize the error.

---

### Post by courseinmiracles2 on 2015-10-27
Thanks agin for checking up on me.
output for code is below:

```
lsmod

Module                  Size  Used by
snd_usb_audio         184320  0 
snd_usbmidi_lib        32768  1 snd_usb_audio
gspca_sonixj           40960  0 
gspca_main             36864  1 gspca_sonixj
videodev              159744  2 gspca_sonixj,gspca_main
media                  24576  1 videodev
ctr                    16384  3 
ccm                    20480  3 
arc4                   16384  2 
rtl8192ce              57344  0 
rtl_pci                28672  1 rtl8192ce
rtl8192c_common        53248  1 rtl8192ce
rtlwifi                77824  3 rtl_pci,rtl8192c_common,rtl8192ce
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_conexant    24576  1 
mac80211              724992  3 rtl_pci,rtlwifi,rtl8192ce
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
snd_hda_intel          36864  4 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
i915                 1060864  8 
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
intel_powerclamp       20480  0 
cfg80211              540672  2 mac80211,rtlwifi
snd_pcm               106496  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
coretemp               16384  0 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
dm_multipath           24576  0 
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
drm_kms_helper        131072  1 i915
drm                   348160  5 i915,drm_kms_helper
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
scsi_dh                16384  1 dm_multipath
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
joydev                 20480  0 
toshiba_acpi           28672  0 
serio_raw              16384  0 
snd                    90112  19 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
sparse_keymap          16384  1 toshiba_acpi
toshiba_bluetooth      16384  0 
wmi                    20480  1 toshiba_acpi
mei_me                 20480  0 
i2c_algo_bit           16384  1 i915
soundcore              16384  2 snd,snd_hda_codec
mei                    90112  1 mei_me
intel_ips              20480  0 
shpchp                 40960  0 
video                  20480  1 i915
lpc_ich                24576  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
ums_realtek            20480  0 
uas                    24576  0 
usb_storage            69632  2 uas,ums_realtek
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  3 hid_generic,usbhid
psmouse               118784  0 
ahci                   36864  2 
libahci                32768  1 ahci
atl1c                  49152  0 
dm_mirror              24576  0 
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
```

---

### Post by tgalati4 on 2015-10-28
This appears to be your webcam.  It contains sound and a video driver:

> snd_usb_audio         184320  0 
snd_usbmidi_lib        32768  1 snd_usb_audio
gspca_sonixj           40960  0 
gspca_main             36864  1 gspca_sonixj
videodev              159744  2 gspca_sonixj,gspca_main

There is a debug switch:

> tgalati4@Mint17 ~ $ modinfo gspca_main
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/media/usb/gspca/gspca_main.ko
version:        2.14.0
license:        GPL
description:    GSPCA USB Camera Driver
author:         Jean-François Moine <http://moinejf.free.fr>
srcversion:     4E25DCB925481E83ADF34E7
depends:        videodev
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:          ** debug:1**:probe 2:config 3:stream 4:frame 5:packet 6:usbi 7:usbo (int)


Verify a full 5 VDC at the outer USB leads to the camera.  The inner leads are data.  I suspect either a cable problem or the camera chip is failing.  Check 5 VDC at the other USB ports.  It could be a failing USB hub. 

If you see the modules, then you should see the camera with *lsusb*.  Do this right after a cold, cold, boot.

---

### Post by tturrisi on 2015-10-28
Try booting a couple different live distros or even Windows to determine if it's failing hardware or a software issue.

---

### Post by courseinmiracles2 on 2015-10-29
I am away from my computer for a couple of days but I'll give a spin when i get back....stay tooned.

---

### Post by courseinmiracles2 on 2015-10-30
Hi,
I ran that code see output below. But I didn't understand what I was suppose to do next...

$ modinfo gspca_main
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/media/usb/gspca/gspca_main.ko
version:        2.14.0
license:        GPL
description:    GSPCA USB Camera Driver
author:         Jean-François Moine <http://moinejf.free.fr>
srcversion:     3DEBC2291DB17641D8140B5
depends:        videodev
intree:            Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B4:BA:13:D5:CE:C9:3E:1A:F4:B3:4D:36:DA:1B:D4:FC:FF:A5:44:10
sig_hashalgo:   sha512
parm:           debug:1:probe 2:config 3:stream 4:frame 5:packet 6:usbi 7:usbo (int)

---

### Post by tgalati4 on 2015-10-30
Many modules have switches that you can turn on and off.

Remove the current module:

```
sudo modprobe -r gspca_main
lsmod
```

Now reload it with switches:

```
sudo modprobe -i gspca_main 1
lsmod
lsusb
```

Some reading:  [http://www.linuxtv.org/wiki/index.php/Gspca](http://www.linuxtv.org/wiki/index.php/Gspca)
[http://www.linuxquestions.org/questions/linux-hardware-18/gspca-version-2-a-774782/](http://www.linuxquestions.org/questions/linux-hardware-18/gspca-version-2-a-774782/)

Any video device files?

```
ls -la /dev/vid*
```

---

### Post by courseinmiracles2 on 2015-10-30
I got an error with the first line of code.
sudo modprobe -r gspca_main:

modprobe: FATAL: Module gspca_main is in use.

Thanks for your help.

---

### Post by tgalati4 on 2015-10-30
Try removing:

```
sudo modprobe -r gspca_sonixj
```

Then try the steps I outlined earlier.

---

### Post by courseinmiracles2 on 2015-10-31
Ok tgalati4, I ran that code with no change. I won't bother you with the output, suffice to say the cam ain't "shiny"... I got a usb plug-in that works perfectly, so at this point I'm gonna let it go.
I really appreciate your feedback and assistance.

I hate to leave this unsolved but it's pretty clear my webcam has crapped out.

Cheers

---

