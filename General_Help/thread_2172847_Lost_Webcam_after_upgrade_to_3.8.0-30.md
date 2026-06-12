---
title: "Lost Webcam after upgrade to 3.8.0-30"
date: 2013-09-06
forum: General Help
---

### Post by jjmf on 2013-09-06
Hey fellow Ubuntu'ers,

After an upgrade to the 3.8.0-30 generic kernel I lost the webcam (cheese: webcam not detected - video0 is completely gone)
reboot start with previous kernel (3.8.0-29) and the webcam is back on and working. My Ubuntu 13.04 is running on a Satellite-C650

Satellite-C650 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

When I start cheese I get:

** (cheese:5411): WARNING **: cheese-main.vala:256: Error: No device found




(cheese:5411): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion `CHEESE_IS_CAMERA_DEVICE (device)' failed


(cheese:5411): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed


(cheese:5411): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion `value != NULL' failed


(cheese:5411): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed


(cheese:5411): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given


** (cheese:5411): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion `device != NULL' failed


lsusb gives me:

lsusb
Bus 001 Device 002: ID 10f1:1a2a Importek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I also tried accessing it with VLC:

v4l2 demux error: cannot open device '/dev/video0': No such file or directory

(for the previous kernel video0 exists)

I tried re-installing the generic kernel

```
sudo apt-get install --reinstall linux-image-generic linux-image
``` 

no luck it is still not working. 

Is anyone else affected? Any suggestions?

Thanks,

JJ

---

### Post by mörgæs on 2013-09-08
When such a regression happens it would be good if you could report the bug in Launchpad.

---

