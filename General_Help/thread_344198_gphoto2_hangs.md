---
title: "gphoto2 hangs"
date: 2007-01-22
forum: General Help
---

### Post by kingmonkey on 2007-01-22
When i connect my camera and try and import it hangs at detecting camera.

When I go to the command line and type gphoto2 --debug --auto-detect I get the following:

```
$ gphoto2 --debug --auto-detect
0.000098 main(2): ALWAYS INCLUDE THE FOLLOWING LINES WHEN SENDING DEBUG MESSAGES TO THE MAILING LIST:
0.000576 main(2): gphoto2 2.2.0
0.000694 main(2): gphoto2 has been compiled with the following options:
0.000789 main(2):  + gcc (C compiler used)
0.000880 main(2):  + popt (for handling command-line parameters)
0.000972 main(2):  + exif (for displaying EXIF information)
0.001063 main(2):  + cdk (for accessing configuration options)
0.001155 main(2):  + no aa (for displaying live previews)
0.001246 main(2):  + jpeg (for displaying live previews in JPEG format)
0.001337 main(2):  + readline (for easy navigation in the shell)
0.001431 main(2): libgphoto2 2.2.1
0.001529 main(2): libgphoto2 has been compiled with the following options:
0.001621 main(2):  + gcc (C compiler used)
0.001718 main(2):  + EXIF (for special handling of EXIF files)
0.001809 main(2):  + no /proc/meminfo (adapts cache size to memory available)
0.001903 main(2): libgphoto2_port 0.6.1
0.002000 main(2): libgphoto2_port has been compiled with the following options:
0.002092 main(2):  + gcc (C compiler used)
0.002182 main(2):  + USB (libusb, for USB cameras)
0.002272 main(2):  + serial (for serial cameras)
0.002363 main(2):  + no resmgr (serial port access and locking)
0.002453 main(2):  + no baudboy (serial port locking)
0.002543 main(2):  + no ttylock (serial port locking)
0.002633 main(2):  + no lockdev (serial port locking)
0.002857 gphoto2-port-info-list(2): Using ltdl to load io-drivers from '/usr/lib/libgphoto2_port/0.6.1'...
0.003058 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.6.1/disk'.
0.003665 gphoto2-port-info-list(2): Could not load port driver list: 'Unspecified error'.
0.003771 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.6.1/ptpip'.
0.003987 gphoto2-port-info-list(2): Loaded 'PTP/IP Connection' ('ptpip:') from '/usr/lib/libgphoto2_port/0.6.1/ptpip'.
0.004090 gphoto2-port-info-list(2): Loaded '' ('^ptpip') from '/usr/lib/libgphoto2_port/0.6.1/ptpip'.
0.004482 gphoto2-port-info-list(2): Called for filename '/usr/lib/libgphoto2_port/0.6.1/serial'.
0.004693 gphoto2-port-serial(2): Trying to lock '/dev/ttyS0'...
0.004810 gphoto2-port-serial(2): Trying to lock '/dev/ttyS1'...
0.004912 gphoto2-port-serial(2): Trying to lock '/dev/ttyS2'...


```

It just hangs there.

Does anyone have any pointers?

---

