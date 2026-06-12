---
title: "Help requested with Multisync (Nokia&lt;-&gt;Evolution)"
date: 2007-06-21
forum: General Help
---

### Post by mawdryn on 2007-06-21
Hi,

I'm having issues running multisync between Feisty and my Nokia 6288. 

Firsty, I can confirm that Feisty and the Nokia are paired successfully and that obex file tranfers are successful both ways via bluetooth. (I have gnome-obex-server running).

When setting up the link in Multisync, I select enter the Nokia's bluetooth address and channel 10 (Correct me if this not correct) and click the test button.
The nokia lights up, says connected, but multisync almost immediately says connection failed and the nokia then says disconnected.

needless to say, Syncronisation fails with the message:
```
Failed to get first plugin changes: unknown error
```

Plugin 1 is the mobile phone, and Plugin 2 is Evolution.

my log shows the following:

```
Jun 21 14:21:52 mondas NetworkManager: <debug info>^I[1182399712.856307] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_50d_84_noserial_bluetooth_hci_bluetooth_hci'). 
Jun 21 14:21:54 mondas hcid[5792]: link_key_request (sba=00:0A:3A:50:C7:D8, dba=00:19:2D:E9:E9:93)
Jun 21 14:21:56 mondas NetworkManager: <debug info>^I[1182399716.429101] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_50d_84_noserial_bluetooth_hci_bluetooth_hci'). 
trevor@mondas:~$ 
```

Can anybody please let me know what I'm doing wrong.

---

