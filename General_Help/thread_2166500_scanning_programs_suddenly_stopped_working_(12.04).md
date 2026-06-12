---
title: "scanning programs suddenly stopped working (12.04)"
date: 2013-08-09
forum: General Help
---

### Post by serexia on 2013-08-09
Hello,

I have recently installed 12.04 and set up, not without difficulties, a scanner (hp scanjet 2400) that I was nicely using with xsane.

After a recent automatic update of the system, any attempt to scan pictures results in a crash of the scanning program, independently on which program I tried to use (meaning xsane, simplescan, scanner utility, gscan2pdf, skanlite, yes I have tried them all...). The result is always the same, the programs crash. 

After the crash, the bug report pop up points to a problem with the third party libsane-xxx.so.1.0.24. 

I have purged and installed from scratch xsane, the sane back-ends, libsane-dev several times, and the problem persists, and I couldn't find any thread that could help me solve this.

Did anyone experience anything similar or has any suggestions?

Thanks
s

---

### Post by pqwoerituytrueiwoq on 2013-08-09
run [FONT=courier new]scanimage -L[/FONT]
you will get something like this:
[FONT=courier new]device `hpaio:/usb/Officejet_4500_G510g-m?serial=CN12JF10VM05CQ' is a Hewlett-Packard Officejet_4500_G510g-m all-in-one[/FONT]
now run this obviously part of this command comes from part of the output from the last command
[FONT=courier new]scanimage --help -d hpaio:/usb/Officejet_4500_G510g-m?serial=CN12JF10VM05CQ[/FONT]
see if it crashes doing that

Are you sure you are using 12.04 LTS and not 13.10 Alpha? i am running 13.04 and only have version [FONT=courier new]1.0.23-0ubuntu1[/FONT] for [FONT=courier new]libsane[/FONT]
i know 13.10 has a issue with [FONT=courier new]scanimage[/FONT] that makes it crash 30-60% of the time
12.04 should have [FONT=courier new]libsane[/FONT] version [FONT=courier new]1.0.22-7ubuntu1[/FONT] or do you have a ppa enabled for [FONT=courier new]scanimage[/FONT]?

---

### Post by serexia on 2013-08-12
the Ubuntu version I am using is 12.04, I didn't upgrade to 13.0. libsane are 1.0.24 because I compiled and installed from the sane backends website since with the built in 1.0.22 I didn't manage to get high resolution scans (i.e. 600dpi) with my scanner.

when I type:
serena-iMac:~> scanimage -L
device `v4l:/dev/video0' is a Noname FaceTime HD Camera (Built-in) virtual device
device `genesys:libusb:001:005' is a Hewlett Packard ScanJet 2400c flatbed scanner
device `epson2:net:136.167.48.219' is a Epson PID 0899 flatbed scanner

the epson scanner must be a network scanner in some other room because I don't have such device in my room (it's a workplace issue...)

if I ask:
serena-iMac:~> scanimage --help -d genesys:libusb:001:005
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

[...]

List of available devices:
    v4l:/dev/video0 genesys:libusb:001:005 epson2:net:136.167.48.219

so it seems to see the scanner

if I type

serena-iMac:~> scanimage -d genesys:libusb:001:005 --preview=yes --resolution=600 > test
Segmentation fault (core dumped)

do you think I should try to change the libsane version?

---

