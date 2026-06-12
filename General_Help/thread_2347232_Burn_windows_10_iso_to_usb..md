---
title: "Burn windows 10 iso to usb."
date: 2016-12-22
forum: General Help
---

### Post by Hewjr100 on 2016-12-22
How would you burn the windows 10 iso to a usb in ubuntu?

Henry

Ps Running ubuntu 16.10

---

### Post by oldos2er on 2016-12-22
I like [mkusb]("https://help.ubuntu.com/community/mkusb").

---

### Post by karl96 on 2016-12-22
You can (carefully) do it with dd. Make sure the disk is formatted as NTFS.

---

### Post by jeremy31 on 2016-12-22
Search Dash for startup disk creator as I have used it to put ISO's on USB in 16.04 and I would hope it is still available in 16.10

---

### Post by oldfred on 2016-12-22
I do not think dd works with Windows ISO, as then it has to be configured by the vendor to be a hybrid ISO. 

If you only want UEFI, boot.
       UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)

---

### Post by karl96 on 2016-12-22
I had no issues with a Windows 8 iso, just needed to make sure it was NTFS. Might have changed for Windows 10 but it was just a standard iso MS distribute online when I did it.

---

### Post by Hewjr100 on 2016-12-22
Wow, seems complicated.  I will review options tomorrow.  Thanks for your replies.

Henry

---

### Post by C.S.Cameron on 2016-12-22
+1 for **mkusb**.

---

### Post by sudodus on 2016-12-22
mkusb-nox and dus (guidus) can create installer drives for Windows 7-10. See these links,

[Making a USB drive to install Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

[mkusb/gui#Installation](https://help.ubuntu.com/community/mkusb/gui#Installation)

[dus - a revamped interface of mkusb and mkusb-nox](https://help.ubuntu.com/community/mkusb/gui#dus_-_a_revamped_interface_of_mkusb_and_mkusb-nox)

---

### Post by Hewjr100 on 2016-12-23
Sudodus I will check that out today.

Henry

---

