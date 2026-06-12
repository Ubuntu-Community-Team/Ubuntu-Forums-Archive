---
title: "Problem connecting LG G4 phone to Xubuntu linux system with MTP"
date: 2015-08-24
forum: General Help
---

### Post by cjsmall on 2015-08-24
I just got the android LG G4 and I cannot get it to mount to my Xubuntu Linux 15.04 system. When first plugged in, it shows up as a "Verizon Mobile" device and that mounts temporarily as an "installer" (whatever that means).  In about 15 seconds it automatically unmounts and redisplays itself as an attached "LGE Android Phone".  Repeated attempts to mount this as a Media Sync (MTP) device results in:

```
Could not display "mtp://[usb:005,034]".
Error: Location is already mounted
Please select another viewer and try again
```

mount(8) shows no such device mounted.

If I select Camera (PTP), then the device will mount, but only the DCIM and Pictures folders on the internal card. The external SD card is not shown.

Following past reports of similar problems such as this, I created the following entry in /lib/udev/rules.d/69-libmtp.rules:

```
# LG Electronics Inc. LG G4
ATTR{idVendor}=="1004",  ATTR{idProduct}=="629a", SYMLINK+="libmtp-%k", MODE="660",  GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```

And created the /etc/udev/rules.d/51-android.rules file with:

```
ATTR{idVendor}=="1004", ATTR{idProduct}=="629a", MODE=”0666"
```

Then restarted the udev service.  No improvement.

Has anyone had success establishing a MTP mount or can you suggest other things to try?

Thanks.

---

### Post by ajgreeny on 2015-08-24
I think from what you say, that you may already have tried all of this, but if not, have a good read through the info at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)

It has worked well for my android devices, Huawei phone and Acer tablet, on my Xubuntu 14.04, but I do not have an LG phone to test, nor a 15.04 OS to test it on.

I have also moved the thread from the "Ubuntu phone and tablet" section to "General" as replies to the phone section you chose is for the Ubuntu phones only and will therefore be very limited, as both the hardware and software are very new and generally unknown to most of us so far.

---

### Post by cjsmall on 2015-08-25
ajgreeny:  Thanks for properly locating the thread, and yes, that article you referenced is the one I followed.  I have not had any luck getting things working after following the instructions.

Maybe someone can comment on the error message which states:

Error: Location is already mounted

Any clue as to why this is reported and how to investigate things further?

---

