---
title: "[SOLVED] Problem copying to/from USB flash drive"
date: 2008-06-04
forum: General Help
---

### Post by Joe Soap on 2008-06-04
I have an 8G usb stick and it gives problem whenever I try to copy large files to or from it under Linux.  The problem does not appear to be hardware related because I was able to copy large files (1.7 G) to the stick under Windows.

When I try to copy the same large file to or from the stick about 200 Mb is copied and then the operation slows down and eventually just stops.

dmesg gives the following output:

[945327.313514] usb 5-3: reset high speed USB device using ehci_hcd and address 6
[945357.540390] usb 5-3: reset high speed USB device using ehci_hcd and address 6
[945387.767276] usb 5-3: reset high speed USB device using ehci_hcd and address 6
[945387.900140] sd 8:0:0:0: [sdg] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[945387.900152] end_request: I/O error, dev sdg, sector 4113567

I've tested this under ubuntu (heron), knoppix 5.3 and kanotix.

Any help will be appreciated.

Thanks
Joe

---

### Post by rraj.be on 2008-06-04
The problem is your hardware oriented.

Your usb its restricted to copy a particular size of file only at a time as the maximum cluster size  is set very high.

Check it by typing this in terminal and post the output.

```
cat /sys/block/sda/device/max_sectors

 (assuming the usbdisk is /dev/sda).
```

---

### Post by Joe Soap on 2008-06-05
Thanks for the response.

Here's what I got:

cat /sys/block/sdc/device/max_sectors
240

What does it mean and what can/should I do about it?

---

### Post by rraj.be on 2008-06-05
Just its set to very high value.

Hope this will help you.

```
echo 128 >/sys/block/sdc/device/max_sectors
```

---

### Post by Joe Soap on 2008-06-05
It helped me indeed :)

Thanks very much.

---

### Post by rraj.be on 2008-06-05
Mark your thread as solved hence it will help others.

To mark it as solved go to the top 

you can see ```
THREAD TOOLS.
```

Click it and select ```
MARK THIS THREAD AS SOLVED.
```

see my signature for more info.

mark solved for```
 every
``` solved thread.

---

### Post by lunarcloud on 2008-11-23
Can one set this permanently for all usb drives?

---

