---
title: "Humax PVR-9200T USB connectivity."
date: 2007-03-13
forum: General Help
---

### Post by chrismyers on 2007-03-13
I've searched all over without success for information on how to transfer files from my Humax PVR-9200T with Linux in general, but Ubuntu in particular.

Has anyone managed to do this?

lshw produces:

Generic USB device
                   product: HUMAX PVR Mass Storage
                   vendor: HUMAX Co., Ltd.
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   serial: xxxxxxxxxx
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=480.0MB/s

lsusb produces:

USB Device ID: 02ad:138c

I'm unsure whether I can simply mount the device.

The windows software looks like FTP over USB, very similar to Gnomad. This leads me to wonder whether Gnomad can be persuaded to communicate with my Humax.

Does anyone have any hints or tips for me to try?

Cheers in advance :)

---

### Post by claypole on 2007-07-04
I am trying to do this also.  Any luck?

---

### Post by claypole on 2007-07-04
Check out [http://humaxdisk.wikispaces.com](http://humaxdisk.wikispaces.com).

Using a fairly simple hardware mod (adding a cable) you can add a proper high-speed USB connection and there is a linux app to access the internal hard drive, which uses a proprietary format.

---

### Post by claypole on 2007-07-04
See also: [http://www.hummy.org.uk/invison/index.php?showtopic=2503&st=120](http://www.hummy.org.uk/invison/index.php?showtopic=2503&st=120)

---

### Post by claypole on 2007-07-04
And this: [http://www.humax-zone.net/forum_url/HMC_GUI.html](http://www.humax-zone.net/forum_url/HMC_GUI.html)

The inbuilt USB connection is supposed to be very slow on all platforms and extremely unreliable in Linux.  Worth a try though.

---

### Post by jimbo54321 on 2008-01-13
got it working here is how i did it

[http://ubuntuforums.org/showthread.php?t=665773](http://ubuntuforums.org/showthread.php?t=665773)

---

