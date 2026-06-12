---
title: "udev run not working correctly anymore after update to 18.04 LTS"
date: 2018-08-31
forum: General Help
---

### Post by risq on 2018-08-31
i seem to have a strange (permission?) problem with udev, after i update from Ubuntu 16.04 LTS to Ubuntu 18.04 LTS

i use the following construct of udev rules for external usb devices

KERNEL=="sd?1", SUBSYSTEMS=="usb", ATTRS{serial}=="xxxxxyyyyy", SYMLINK+="vid1", ACTION=="add", RUN+="/usr/bin/mnt_vid

the executed script /usr/bin/mnt_vid should decrypt the device AND mount it 

#!/bin/bash
echo -n PASSCODE | cryptsetup luksOpen /dev/vid1 vid1
mount /dev/mapper/vid1 /usb/vid1

this worked perfectly with 16.04 before the update. after the update now:
- symlink is still created
- script is still executed
- /dev/mapper/vid1 is still created, so cryptsetup command still works
but
- mount /dev/mapper/vid1 /usb/vid1 IS NOT WORKING, /usb/vid1 shows up empty. i can mount it manual by doing /mount/mapper/vid1 /usb/vid1 as root though.

any help appreciated, thx in advance

---

### Post by risq on 2018-09-06
push

---

### Post by risq on 2018-09-13
push

---

### Post by DrPotoroo on 2018-10-22
I'm having a similar problem. If someone could even provide info on how to monitor if a run command is executing, that would be great. I know my script works when invoked directly.

---

### Post by DrPotoroo on 2018-10-26
Well, I found some answers to my problem with some testing. By adding some commands in my script being called by RUN+="..." to touch files in /tmp, I was able to confirm that my udev rule WAS triggering the script. But commands within the script weren't all completing. I don't know why - maybe because udev kills processes after a while. Anyway, using:
```
TAG+="systemd", ENV{SYSTEMD_WANTS}+="mysystemd.service"
```
in place of RUN+="..." and writing a systemd service to trigger the desired script was the solution.

I also found there were some changes to how udev was being triggered by the specific USB device I was using, so I had to add another udev rule for when the device was removed that was matched by ENV{PRODUCT}== instead of ATTRS{}

---

