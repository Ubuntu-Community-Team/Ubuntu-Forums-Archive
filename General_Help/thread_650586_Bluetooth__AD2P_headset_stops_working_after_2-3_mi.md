---
title: "Bluetooth / AD2P headset stops working after 2-3 minutes."
date: 2007-12-26
forum: General Help
---

### Post by zonky on 2007-12-26
I'm having a problem where a bluetooth headset is successfully paired and working around 3 minutes, then the connection appears to die.

I'm using blueman and have tried both connecting manually and automatically, but it still seems to stop.

If i go back into the Audio Service in blueman, i can't seem to reestablish the headphone connection without power cycling the headphones.

(Creative CB2530).
Bluetooth onboard HP NX5000.

Has anyone had this problem? How did they solve it (bluetooth connection dropping).

---

### Post by Can+~ on 2007-12-26
I don't use bluetooth, but it's a good idea to check for any logs (/var/log), or run any application on the terminal to receive some standard output, and post here your findings.

---

### Post by zonky on 2007-12-26
```

Dec 27 09:11:52 kingofubuntu audio[6948]: Audio API: received BT_STREAMSTART_REQ
Dec 27 09:11:52 kingofubuntu audio[6948]: avdtp_ref(0x806b588): ref=4
Dec 27 09:11:52 kingofubuntu audio[6948]: setup_ref(0x80698b0): ref=1
Dec 27 09:11:52 kingofubuntu audio[6948]: setup_ref(0x80698b0): ref=2
Dec 27 09:11:52 kingofubuntu audio[6948]: Audio API: sending BT_STREAMSTART_RSP
Dec 27 09:11:52 kingofubuntu audio[6948]: Audio API: sending BT_STREAMFD_IND
Dec 27 09:11:52 kingofubuntu audio[6948]: setup_unref(0x80698b0): ref=1
Dec 27 09:11:52 kingofubuntu audio[6948]: setup_unref(0x80698b0): ref=0
Dec 27 09:11:52 kingofubuntu audio[6948]: setup_free(0x80698b0)
Dec 27 09:11:52 kingofubuntu audio[6948]: avdtp_unref(0x806b588): ref=3
Dec 27 09:13:31 kingofubuntu audio[6948]: session_cb
Dec 27 09:13:31 kingofubuntu audio[6948]: Received CLOSE_CMD
Dec 27 09:13:31 kingofubuntu audio[6948]: SBC Source: Close_Ind
Dec 27 09:13:31 kingofubuntu audio[6948]: stream state changed: STREAMING -> CLOSING
Dec 27 09:13:31 kingofubuntu audio[6948]: stream state changed: CLOSING -> IDLE
Dec 27 09:13:31 kingofubuntu audio[6948]: avdtp_unref(0x806b588): ref=2
Dec 27 09:13:31 kingofubuntu audio[6948]: SBC Source SEP 0x80694b8 unlocked
Dec 27 09:13:31 kingofubuntu audio[6948]: avdtp_unref(0x806b588): ref=1
Dec 27 09:13:32 kingofubuntu audio[6948]: session_cb
Dec 27 09:13:32 kingofubuntu audio[6948]: Disconnected from 00:12:0E:09:CF:9E
Dec 27 09:13:32 kingofubuntu audio[6948]: avdtp_unref(0x806b588): ref=0
Dec 27 09:13:32 kingofubuntu audio[6948]: avdtp_unref(0x806b588): freeing session and removing from list
Dec 27 09:13:32 kingofubuntu NetworkManager: <debug> [1198700012.283867] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_49f_86_noserial_if0_bluetooth_hci_bluetooth_hci'). 




```This is what happens when the connection dies.

---

### Post by zonky on 2007-12-26
Hmm, a little more reading/reasoning suggests that the connection is being closed by something.

I am using vlc to view a avi in this case, although, when auto mode is set, i get the user login sounds when login to ubuntu is done.

It just seems that the connection is being auto-closed by something!

---

### Post by zonky on 2007-12-27
*bump*

---

### Post by zonky on 2007-12-30
It seems that the connection is kept open by the headset- it still seems to be paired with the notebook. When i scan for the headphones again, it is not detected until i power cycle them.

I do have these working with both a din -plug usb audio adaptor and a usb bluetooth adatptor attached to a windows xp box.

Greatful for any help and/or ideas.

---

