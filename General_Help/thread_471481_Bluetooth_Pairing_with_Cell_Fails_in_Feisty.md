---
title: "Bluetooth Pairing with Cell Fails in Feisty"
date: 2007-06-12
forum: General Help
---

### Post by DRicher33 on 2007-06-12
Hi all,

I've been working on this for a few days now.  

I can't seem to get pairing to work between my bluetooth adaptor and my nokia cell.

I managed to get hci0 working and running.  And it can see my nokia.   My nokia can see my hci0 but when I enter the passkey it fails.

I've tried with the default passkey and I've tried with a made passkey.

When I do try the connection this is what I get in the syslog:

Jun 11 22:26:19 localhost NetworkManager: <debug info>^I[1181625979.765943] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_bluetooth_hci_bluetooth_hci'). 
Jun 11 22:26:49 localhost NetworkManager: <debug info>^I[1181626009.784738] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_bluetooth_hci_bluetooth_hci'). 
Jun 11 22:27:33 localhost gconfd (root-26432): starting (version 2.18.0.1), pid 26432 user 'root'
Jun 11 22:27:33 localhost gconfd (root-26432): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 11 22:27:33 localhost gconfd (root-26432): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 11 22:27:33 localhost gconfd (root-26432): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 11 22:27:33 localhost gconfd (root-26432): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 11 22:27:33 localhost gconfd (root-26432): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 11 22:28:26 localhost NetworkManager: <debug info>^I[1181626106.483396] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_bluetooth_hci_bluetooth_hci'). 
Jun 11 22:28:33 localhost gconfd (root-26432): GConf server is not in use, shutting down.
Jun 11 22:28:33 localhost gconfd (root-26432): Exiting
Jun 11 22:28:56 localhost NetworkManager: <debug info>^I[1181626136.504462] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_a12_1_noserial_bluetooth_hci_bluetooth_hci'). 

Is this a permission problem? Or am I on the wrong track

THANKS!

---

### Post by useResa on 2007-06-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/110375) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				There are more of us with the same issue  :(

All I can suggest is to add your issue to the indicated bug.
If you want to read about others with the same issue, visit [this post]("http://ubuntuforums.org/showthread.php?t=421466").

---

### Post by NIT006.5 on 2007-06-25
Since it seems that the bug mentioned is mostly to do with not being able to detect bluetooth devices, I'm not sure if you're problem is related, since you're only failing to pair the devices (but have no problem detecting them from what I gather?).

This is a minor point but might be useful:

When I first started using ubuntu I had a similar issue and it was because I was used to the bluetooth package I used in Windows which had a preset pass key. I only realised after about an hour, that when prompted for pass keys, I didn't have to enter any presets - it would accept ANY pass key provided that the same one was entered on the phone as well. i.e. it doesn't use a stored one, you just have to enter the same key (anything you like) on both devices at the time of pairing. That's assuming that your phone also prompts for a key at the same time? That worked for me on a Samsung E860, but haven't tried with a Nokia.

---

