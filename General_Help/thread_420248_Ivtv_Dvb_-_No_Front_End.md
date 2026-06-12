---
title: "Ivtv Dvb - No Front End"
date: 2007-04-23
forum: General Help
---

### Post by b3n87 on 2007-04-23
im getting this error in my dmesg

```
[   40.201483] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[   40.332274] dib0700: firmware started successfully.
[   40.462577] intel8x0_measure_ac97_clock: measured 58769 usecs
[   40.462584] intel8x0: clocking to 48000
[   40.838334] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   40.838497] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   40.839019] DVB: registering new adapter (Hauppauge Nova-T Stick).
[   41.047134] dvb-usb: no frontend was attached by 'Hauppauge Nova-T Stick'
[   41.047145] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   41.047177] usbcore: registered new interface driver dvb_usb_dib0700
[   41.047352] usbcore: registered new interface driver snd-usb-audio

```

i really cant get this to work, please please please could someone give me a pointer as to why its not giving it a frontend, which i need for it to work with programs i believe?

i have these firmware files to
```
ben@ben-desktop:/lib/firmware$ ls /lib/firmware/v4l*fw -l
-rw-r--r-- 1 root root 262144 2007-02-18 23:22 /lib/firmware/v4l-cx2341x-dec.fw
-rw-r--r-- 1 root root 376836 2007-02-18 23:22 /lib/firmware/v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root  16382 2007-02-18 23:22 /lib/firmware/v4l-cx25840.fw
-rw-r--r-- 1 root root   8192 2007-02-18 23:22 /lib/firmware/v4l-pvrusb2-24xxx-01.fw
-rw-r--r-- 1 root root   8192 2007-02-18 23:22 /lib/firmware/v4l-pvrusb2-29xxx-01.fw
```

best regards

---

### Post by tom56 on 2007-04-24
This should work - [http://ubuntuforums.org/showpost.php?p=2420108&postcount=20](http://ubuntuforums.org/showpost.php?p=2420108&postcount=20)

Remember to change the kernel version number to whatever kernel you're running and to check the list for what file you need.

---

