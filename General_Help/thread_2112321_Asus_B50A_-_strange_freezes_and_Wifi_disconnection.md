---
title: "Asus B50A - strange freezes and Wifi disconnection problem"
date: 2013-02-04
forum: General Help
---

### Post by matwes on 2013-02-04
Hello everyone.

I have a few problems with an Asus B50A laptop with Ubuntu 12.10 x86_64 installed (with all updates) as an upgrade from 12.04 LTS.

First one:
During normal activity on the laptop in random moments Ubuntu hangs and I have to move the mouse cursor on touchpad to make it "unfreeze". It happens all the time when I try to watch the YouTube video using Firefox 18.0.1 with Adobe Flash Player 11.2.202.261 plugin. It looks like the sound is looping and I need to move the mouse cursor to "unfreeze" the system.

Second one: 
The wireless network randomly disconnects. I'm getting errors like these all the time:
```
Feb  4 17:59:00 ubuntu-pc wpa_supplicant[1247]: wlan0: Failed to initiate AP scan
    Feb  4 17:59:00 ubuntu-pc kernel: [  716.824185] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
    Feb  4 17:59:00 ubuntu-pc kernel: [  716.824197] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 104 write_ptr 112
    Feb  4 17:59:03 ubuntu-pc wpa_supplicant[1247]: wlan0: Failed to initiate AP scan
    Feb  4 17:59:03 ubuntu-pc kernel: [  719.824224] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
    Feb  4 17:59:03 ubuntu-pc kernel: [  719.824237] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 104 write_ptr 113
    Feb  4 17:59:06 ubuntu-pc wpa_supplicant[1247]: wlan0: Failed to initiate AP scan
    Feb  4 17:59:06 ubuntu-pc kernel: [  722.824167] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
    Feb  4 17:59:06 ubuntu-pc kernel: [  722.824179] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 104 write_ptr 114
    Feb  4 17:59:09 ubuntu-pc wpa_supplicant[1247]: wlan0: Failed to initiate AP scan
    Feb  4 17:59:09 ubuntu-pc kernel: [  725.824247] iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms.
    Feb  4 17:59:09 ubuntu-pc kernel: [  725.824260] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 104 write_ptr 115

```

---

### Post by matwes on 2013-02-09
SOLVED:
It was the problem with ACPI options in /etc/default
I've changed the line to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic acpi_backlight=vendor acpi_osi=Linux"
```from just
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=Linux"
```next, I did:
```
sudo update-grub
```and videos run smooth

---

