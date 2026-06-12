---
title: "microtek slimscan C3 parallel port installation problems"
date: 2008-02-01
forum: General Help
---

### Post by treehouse on 2008-02-01
I have a similar problem to the one in [this thread](http://ubuntuforums.org/showthread.php?t=525456&highlight=) which has no real solution.

I have a Microtek Slimscan C3 which goes on the parallel port. I tried doing:

```

:~$ sudo sane-find-scanner -p
Password:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # No Mustek parallel port scanners found. If you expected something
  # different, make sure the scanner is correctly connected to your computer
  # and you have apropriate access rights.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

I don't really know any other methods to install scanners on Linux, so if there's any way I could get pointed in the right direction, that'd be awesome. Thanks.

---

### Post by linuxwizard on 2008-02-01
According to this that scanner should work complete > [http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK](http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK)

Look over this see if you need to change or add anything to your configuration file > [http://www.sane-project.org/man/sane-microtek2.5.html](http://www.sane-project.org/man/sane-microtek2.5.html)

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by treehouse on 2008-02-01
Well I have all the Microtek and Mustek stuff enabled for Sane, but it's still not detecting. I'm assuming I need to use the ppSCSI patch, but I have no idea how to go about building it or applying it to the kernel or whatever. Where do I look for instructions?

---

### Post by linuxwizard on 2008-02-01
Not sure if you need the ppSCSI patch or not. Look over these see if something will help.

[http://cyberelk.net/tim/parport/ppscsi.html](http://cyberelk.net/tim/parport/ppscsi.html)

[http://penguin-breeder.org/kernel/download/](http://penguin-breeder.org/kernel/download/)

---

