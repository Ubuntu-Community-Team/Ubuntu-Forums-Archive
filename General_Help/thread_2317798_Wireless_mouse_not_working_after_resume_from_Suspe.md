---
title: "Wireless mouse not working after resume from Suspend"
date: 2016-03-19
forum: General Help
---

### Post by josephellengar2 on 2016-03-19
Hi there!

I'm using Ubuntu 14.04. After a recent update (kernel update?) my wireless mouse stopped working. It still works when I boot the computer, but stops as soon as I suspend/unsuspend, and I also normally ave to move the adapter to another USB port. No idea why.

lsusb output:

> 
Bus 001 Device 007: ID 0eef:a802 D-WAV Scientific Co., Ltd eGalaxTouch EXC7920
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 05c8:0361 Cheng Uei Precision Industry Co., Ltd (Foxlink) SunplusIT INC. HP Truevision HD Webcam
Bus 002 Device 006: ID 8087:07da Intel Corp. 
Bus 002 Device 008: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ETA: This is lsusb output after restarting, and then moving the mouse receiver, so that mouse currently works:
> 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 05c8:0361 Cheng Uei Precision Industry Co., Ltd (Foxlink) SunplusIT INC. HP Truevision HD Webcam
Bus 002 Device 006: ID 8087:07da Intel Corp. 
Bus 002 Device 014: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 009: ID 138a:0050 Validity Sensors, Inc. Swipe Fingerprint Sensor
Bus 002 Device 008: ID 0eef:a802 D-WAV Scientific Co., Ltd eGalaxTouch EXC7920
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



I tried this to fix it (the only reliable suggestion I could find online) but it didn't work. I was told to put the following script into my pm.d.
> 
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".

case "${1}" in
  hibernate|suspend)
    # Unbind xhci_hcd devices
    echo -n "0000:00:14.0" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
  ;;
  resume|thaw)
    # Bind xhci_hcd devices
    echo -n "0000:00:14.0" | tee /sys/bus/pci/drivers/xhci_hcd/bind
  ;;
esac


Thanks for any help.

---

### Post by josephellengar2 on 2016-03-20
bump

---

### Post by josephellengar2 on 2016-03-22
bump bump bumpety bump

---

### Post by josephellengar2 on 2016-03-27
pmub

---

### Post by nworbnhoj on 2016-05-08
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1561474](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1561474)

In the meantime 
sudo invoke-rc.d bluetooth restart

---

### Post by josephellengar2 on 2016-05-09
> **nworbnhoj said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1561474](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1561474)

In the meantime 
sudo invoke-rc.d bluetooth restart

Thanks, but my mouse isn't bluetooth. It's a Logitech unified receiver mouse.

---

