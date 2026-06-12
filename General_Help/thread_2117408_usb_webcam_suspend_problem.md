---
title: "usb webcam suspend problem"
date: 2013-02-18
forum: General Help
---

### Post by Carlos Pena on 2013-02-18
Hi everybody,

I'm using uvccapture to get images from a logitech C905 camera in my ubuntu 12.04 server
Everything works fine, but i have a problem. When the camera takes 90 or 100 images(after 4-5 minutes), it stop working and uvccapture rise the error "ERROR opening V4L interface: No such file or directory".  

In order to prevent the
webcam suspend i execute changed the values for the following parameters:

/sys/module/usbcore/parameters/autosuspend -1

/sys/bus/usb/devices/usb1/power/autosuspend -1
/sys/bus/usb/devices/usb2/power/autosuspend -1
/sys/bus/usb/devices/usb3/power/autosuspend -1
/sys/bus/usb/devices/usb4/power/autosuspend -1

/sys/bus/usb/devices/usb1/power/level on
/sys/bus/usb/devices/usb2/power/level on
/sys/bus/usb/devices/usb3/power/level on
/sys/bus/usb/devices/usb4/power/level on

/sys/bus/usb/devices/usb1/power/autosuspend_delay_ms -1
/sys/bus/usb/devices/usb2/power/autosuspend_delay_ms -1
/sys/bus/usb/devices/usb3/power/autosuspend_delay_ms -1
/sys/bus/usb/devices/usb4/power/autosuspend_delay_ms -1

/sys/bus/usb/devices/usb1/power/wakeup enabled
/sys/bus/usb/devices/usb2/power/wakeup enabled
/sys/bus/usb/devices/usb3/power/wakeup enabled
/sys/bus/usb/devices/usb4/power/wakeup enabled

But this doesn't fix the problem.

When i reboot the computer, the camera start working again for 4-5 minutes only until i reboot the computer again.  

How could i reset all the usb devices(or /dev/videox device) without rebooting the computer? 

Or, How could i keep all the USB alive?

Sincerely,
Carlos
Santo Domingo, D.R.

---

### Post by albandy on 2013-02-18
Try unloading and loading the kernel module of your webcam.
To know what kernel module is for your webcam do the following:
unplug de webcam
lsmod > unplugged.txt
plug de webcam
lsmod > plugged.txt

then type:
diff unplugged.txt plugged.txt 
and you will see the difference that should correspond to the kernel module name.

If no module appears do a lsmod and post the result.

---

### Post by Carlos Pena on 2013-02-18
Thank you Albandy,

There's no differences in lsmod when the camera is plugged and unplugged. I also try executing lsmod after reboot and after the camera stopped working. 

These are the modules shown after lsmod command:


Module                  Size  Used by
vesafb                 13516  1
ppdev                  12849  0
snd_via82xx            24718  0
snd_ac97_codec        110213  1 snd_via82xx
serio_raw              13027  0
ac97_bus               12642  1 snd_ac97_codec
snd_wavefront          34737  0
i2c_viapro             12969  0
via_ircc               26781  0
irda                  185517  1 via_ircc
snd_usb_audio         101566  0
uvcvideo               67203  0
videodev               86588  1 uvcvideo
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_cs4236             29294  0
crc_ccitt              12627  1 irda
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236
snd_hwdep              13276  3 snd_wavefront,snd_usb_audio,snd_opl3_lib
snd_pcm                80916  5 snd_via82xx,snd_ac97_codec,snd_usb_audio,snd_cs4236,snd_wss_lib
shpchp                 32325  0
snd_timer              28931  3 snd_wss_lib,snd_opl3_lib,snd_pcm
snd_page_alloc         14108  3 snd_via82xx,snd_wss_lib,snd_pcm
snd_mpu401             13847  0
snd_mpu401_uart        13865  4 snd_via82xx,snd_wavefront,snd_cs4236,snd_mpu401
snd_rawmidi            25424  3 snd_wavefront,snd_usbmidi_lib,snd_mpu401_uart
snd_seq_device         14172  2 snd_opl3_lib,snd_rawmidi
snd                    62218  15 snd_via82xx,snd_ac97_codec,snd_wavefront,snd_usb_audio,snd_usbmidi_lib,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_pcm,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              14635  1 snd
ns558                  12654  0
gameport               15060  3 snd_via82xx,ns558
parport_pc             32114  1
mac_hid                13077  0
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
via_rhine              27413  0
pata_via               13428  2
floppy                 60184  0

Other thing, after the uvcapture error, the camera does not work even if i unplug and plug again in the same/other usb port. Only works for 4-5 minutes if i reboot the computer.

Here is the shell i am running for the capture:

#!/bin/sh
echo "Start at $(date)" > /cameras/retrata.log
while [ $? -lt 1 ] 
do
  sudo -S</pass.dat uvccapture -m -d/dev/video0 -x1600 -y1200 -o/cameras/Cam01[$(date +"%Y-%m-%d[%H;%M;%S]")].jpg
done
echo "Error at $(date)" >> /cameras/retrata.log


Also, I tried adding a (sleep 2) seconds delay between do-done loop.

Carlos

---

### Post by albandy on 2013-02-18
Try with this module: uvcvideo

When the camera stop working type this:
sudo rmmod uvcvideo
sudo modprobe uvcvideo

---

### Post by Carlos Pena on 2013-02-18
It doesn't work. I also try unloading/loading other usb relatives modules to see what happens. :-(

---

### Post by Carlos Pena on 2013-02-18
It doesn't work. In fact, i rmmod each module (forced) and modprobe all of them after 4 seconds.

---

### Post by albandy on 2013-02-19
> **Carlos Pena said:**
> It doesn't work. In fact, i rmmod each module (forced) and modprobe all of them after 4 seconds.

Can you post your kernel log when this happens?

---

### Post by Carlos Pena on 2013-02-22
Thank you Albandy,

Finnaly i found a problem with the kernel module ehci_hcd. It stops randomly. I added the following actions when my program detects a failure in the USB device:

echo -n "0000:00:10.3" > /sys/bus/pci/drivers/ehci_hcd/unbind
echo -n "0000:00:10.3" > /sys/bus/pci/drivers/ehci_hcd/bind

These instructions "disconnect/connect" the USB from usb 2.0 driver. It is working, but sometimes the ehci_hcd crash too much. If you have a better idea i'd really appreciate any help.

Carlos

---

### Post by albandy on 2013-02-24
Have you tried using a previous kernel version?

---

