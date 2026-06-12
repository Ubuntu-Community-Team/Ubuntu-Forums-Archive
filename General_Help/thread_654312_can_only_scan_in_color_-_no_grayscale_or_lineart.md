---
title: "can only scan in color - no grayscale or lineart"
date: 2007-12-30
forum: General Help
---

### Post by brion@cbkidder.com on 2007-12-30
Xsane and gscan2pdf work well with my HP scanjet 3570C scanner except only in color; I cannot select grayscale or lineart modes. I have scanned to lineart and to grayscale with this device under another OS but I don't know how to configure it to scan in other modes besides color within Ubuntu.

Here is the output of the device options. Can anyone advise?

Thanks,
Brion Kidder
Orange, CA
---------------
brion@brion-desktop:~$ scanimage --help -d hp3500:libusb:004:003

Options specific to device `hp3500:libusb:004:003':
    --resolution 50|75|100|150|200|300|400|600|1200dpi [200]
        Sets the resolution of the scanned image.
  Geometry:
    -l 0..215.9mm (in steps of 0.0211639) [0]
        Top-left x position of scan area.
    -t 0..298.7mm (in steps of 0.0211639) [0]
        Top-left y position of scan area.
    -x 0..215.9mm (in steps of 0.0211639) [215.893]
        Width of scan-area.
    -y 0..298.7mm (in steps of 0.0211639) [298.454]
        Height of scan-area.
  Scan Mode Group:
    --mode Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    hp3500:libusb:004:003

---

### Post by quinnten83 on 2008-03-11
Has anyone had any luck with solving this issue?
I have the same thing only my specs differ.
I have a HP scanjet  2400.
I got it to work by using these tutorials:
[http://ubuntuforums.org/showthread.php?t=78305&page=2 ]("http://ubuntuforums.org/showthread.php?t=78305&page=2")
[http://www.elcot.in/linuxdrivers_download.php#Scan240]("http://www.elcot.in/linuxdrivers_download.php#Scan240")0 
Unfortunately I can only scan in color and I desperately need the line art.

---

