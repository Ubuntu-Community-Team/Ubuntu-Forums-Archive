---
title: "ACPI resume problem after S1 or S3 suspend"
date: 2005-10-01
forum: General Help
---

### Post by alza on 2005-10-01
Hi there
I have a box running Hoary Hedgehog with 2.6.10-5 kernel release. Using my power button I can invoke /etc/acpi/sleep.sh using ACPI events. The box seems to suspend to either S1 or S3 with no problems. In S3 the hard disk & cpu fan stops, in S1 just the cpu fan stops. The power LED on my case then starts flashing. 
However, when I use the power button to resume, after a short pause, the console shows 'kernel panic - not syncing: for safety' and I have to reboot. 
My box has an ASUS CUSL2-LS motherboard, with a SCSI hard disk. There are no usb devices attached to the box.
Should I file a bug for this or is there a workaround?
Thanks

---

