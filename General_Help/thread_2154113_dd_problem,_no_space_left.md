---
title: "dd problem, no space left"
date: 2013-06-13
forum: General Help
---

### Post by vecnu on 2013-06-13
Hi everyone.

I'm trying to duplicate a bootable usb drive by means of dd. Both are 8Gb usb drives. After some minutes, dd finishes and says there is no more space left. Any idea on how to solve it?

Origin:
/dev/sdb1   *        2048    15204351     7601152    7  HPFS/NTFS/exFAT

Destination:
/dev/sdc1              63    15148223     7574080+   b  W95 FAT32

My terminalanguage is Spanish.  The output is some kind of
*dd*: *writing* /dev/sdc: *No space left* on device

EDIT: I've tried both dd if=/dev/sdb of=/dev/sdc and dd if=/dev/sdb1 of=/dev/sdc1

---

### Post by VMC on 2013-06-13
You left out the 'dd' command your using. This [iso-to-usb]("http://askubuntu.com/questions/59551/how-to-burn-iso-to-usb-device") link may help.

---

### Post by matt_symes on 2013-06-13
Hi

Can we take a close look at the devices as i'm surprised that copying sdb to sdc did not work if they are the same size.

Plug both devices in and then type..

```
sudo lshw -short | grep "sd[bc]"
```

Post the results back here.

EDIT: And are you sure they are not copying correctly as i can get that error when i use gddresuce to wipe a pen drive.

I.E this will return the same 'out of space' error.

```
sudo ddrescue /dev/zero /dev/sdb
```

Kind regards

---

### Post by vecnu on 2013-06-13
#2: what I need is to duplicate an USB boot device, I don't have an ISO image. I'm not sure if the tips in your link will work, unless some formatting is needed before using dd. 

#3: this is the output:
 ```

sudo lshw -short | grep "sd[bc]"

/0/2/0.0.0             /dev/sdb     disk        7784MB SCSI Disk
/0/2/0.0.0/1           /dev/sdb1    volume      7423MiB Windows NTFS volumen
/0/3/0.0.0             /dev/sdc     disk        7756MB SCSI Disk

```

---

### Post by matt_symes on 2013-06-13
Hi

> /0/2/0.0.0     /dev/sdb     disk** 7784MB**     SCSI Disk 
/0/3/0.0.0     /dev/sdc     disk **       7756MB**     SCSI Disk

Well, according to that, they are different sizes :)

These are two "identical" USB pen drives i have (same make, model and size) ...

```

matthew-S206:/home/matthew % sudo lshw -short | grep "sd[bc][^1-9]"
/0/2/0.0.0     /dev/sdb    disk        3997MB SCSI Disk
/0/3/0.0.0     /dev/sdc    disk        3998MB SCSI Disk
matthew-S206:/home/matthew % 
```

They are also not the same size.

In your case sdb is bigger than sdc. 

I expect if you were copying sdc to sdb you would not get that error.

Kind regards

---

### Post by vecnu on 2013-06-13
Ok, thanks!! I would not have thought disk sizes would be the problem. I'll try with a different one.

---

