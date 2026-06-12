---
title: "some usbs recognized and others not"
date: 2014-03-31
forum: General Help
---

### Post by rules2 on 2014-03-31
I have two external usb drives: western digital and toshiba. western digital is auto mounted by ubuntu while the toshiba is not. same is the case in windows. any suggestions what might need to put on the toshiba drive for it to be auto mounted.

---

### Post by sudodus on 2014-03-31
Welcome to the Ubuntu Forums :-)

Recognizing, mounting and even more complicated, booting from USB drives will work most of the time, but it can be tricky. The problem might be in the hardware or maybe some firmware in the USB interface of the external drive, and maybe beyond what we can manage. But let us try :-)

Can you 'see' it as a mass storage device?

Are you prepared to run commands in the terminal window? In that case, please check with

```
sudo parted -l
```

There should be 'space minus ell' at the end of the command line. Finish with the Enter key, and copy the output to a reply.

It should be recognized with something like **/dev/sdb** or **/dev/sdc**

-o-

If it is recognized and there are partitions you can try mounting one of them manually. Otherwise you cannot.

*Example*: Let us assume that you have one internal drive, **/dev/sda**, and the two external drives connected.

```
Model: WDC (some specs)
Disk **/dev/sdb**
...
```

```
Model: Toshiba (some other specs)
Disk **/dev/sdc**
...
Number  Start   End     Size    Type      File system  Flags
 1      1049kB  3999MB  3998MB  primary   ext4

```

Try mounting the first partition of the Toshiba drive like this

```
sudo mount /dev/sdc1 /mnt
```

and look for it in the file browser at the mount point **/mnt**

---

### Post by SeijiSensei on 2014-03-31
Also, if you have a mix of USB 2.0 and USB 3.0 ports on your machine, try connecting the drive to one of the slower-speed ports and see if that matters.

---

