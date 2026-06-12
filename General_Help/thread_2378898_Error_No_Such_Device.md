---
title: "Error No Such Device"
date: 2017-11-28
forum: General Help
---

### Post by box02-0 on 2017-11-28
Hi.
I have a bootable USB with an old Ubuntu 14.04. I tried overlaying a newer version of Ubuntu 14.04 using GParted copy/paste. 

The newer Ubuntu has a different uuid. After the GParted copy, I checked the Ubuntu on the USB, and, as expected, it is the newer uuid. I examined grub.cfg on the usb, and, as expected, it has the newer uuid in the code.

However, when I boot the usb, I get "Error No Such Device: ......d6d7" which is the previous uuid. I then get into Grub Rescue.  So where is the previous uuid coming from?

Thanks,
M...

---

### Post by box02-0 on 2017-11-30
Can anyone help?

Thanks,
M...

---

### Post by yancek on 2017-11-30
I'm not really sure what you mean by "overlaying"  but if you copied an instance of Ubuntu to another drive/device and have checked that the UUIDs in grub.cfg are correct, check /etc/fstab.

---

### Post by box02-0 on 2017-11-30
Hi.

By overlaying I mean a GParted copy/paste

Yes FSTAB on the USB reflects the new UUID.


So to recap:
I started with a new empty USB formatted to ext4 by GParted

I did a GParted copy/paste of an operational Ubuntu to the usb. The source Ubuntu is using a uuid of "WXYZ"

I changed the uuid of the USB Ubuntu to "ABCD" using GParted

I changed FSTAB and GRUB.cfg in the USB Ubuntu to "ABCD"

I did a 'dd' copy of the first 446 bytes of another bootable USB to the new USB

I BIOS disabled all other drives on the system

I boot with the new USB, and Grub Rescue comes up and says "Error No Such Device: ......WXYZ

There must be another file in the USB Ubuntu that has the old uuid "WXYZ".

Where else would the old uuid be stored other than etc/FSTAB & boot/grub/GRUB.cfg ?

Thanks for responding.

M...

---

### Post by box02-0 on 2017-12-04
Hi Again.

Can anyone help?

Thanks,
M..

---

