---
title: "how to set a pci setting at boot?"
date: 2020-01-26
forum: General Help
---

### Post by forevertheuni2 on 2020-01-26
I have been having big failures to resume from suspension in my laptop. (Lenovo Y540)
With the power cable on, everything is fine.
With battery power it just doesn't resume.

I pointed it to the nvme disk because of the dmesg errors that I found.

I test to do :
# echo "0" > /sys/bus/pci/devices/0000:06:00.0/d3cold_allowed

And it fixed my problem a couple of times .

My question is, how can I do this at boot?
I don't think I can set this with sysctl. 

is there any file in ubuntu that works the same way for pci stuff (setpci related?)

Thank you.

---

