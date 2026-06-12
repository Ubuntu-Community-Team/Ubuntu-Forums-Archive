---
title: "Olympus Digital Recorder DS 2300 not showing"
date: 2007-09-23
forum: General Help
---

### Post by Robbyx on 2007-09-23
The recorder shows under LSUB as 

BUS 001 Deviece 050 ID:0764:0211  Olympus Optical

Under media no extra drive is appearing when the Ds 2300 is pluggede in to the USB port.

How do I mount it? 

SDA1 and SDB1  are both appearing in the media drives, but then I have a serial hard dirve.

Does anyone know what I should do next to see the device?

---

### Post by ddrichardson on 2007-09-23
It's not one of these cameras that needs to be in the "play" position to act as a disk rather than the "take picture" switch position to act as a web camera is it?

---

### Post by Robbyx on 2007-09-25
I would like to some more help because this is a digital recorder.

---

### Post by ddrichardson on 2007-09-25
As I repsonded to your PM, does it mount OK under Windows and what filesystem does it use?

---

### Post by Robbyx on 2007-09-25
Sorry I didn't notice your email reply.

I only have Win2k in VMWare player. It is not finding the recorder.

I just ran the following:

robin@robin-desktop:~$ dmesg | tail
[55663.867884] sdb: Write Protect is off
[55663.867890] sdb: Mode Sense: 0b 00 00 08
[55663.867893] sdb: assuming drive cache: write through
[55663.887309] SCSI device sdb: 32000 512-byte hdwr sectors (16 MB)
[55663.899427] sdb: Write Protect is off
[55663.899434] sdb: Mode Sense: 0b 00 00 08
[55663.899436] sdb: assuming drive cache: write through
[55663.899445]  sdb: sdb1
[55663.939215] sd 9:0:0:0: Attached scsi removable disk sdb
[55663.939264] sd 9:0:0:0: Attached scsi generic sg1 type 0

It looks to me as if the dictation machine may be  being treated as sdb1 in the above. sdb1 shows in my media even if the DM is not connected. If it is connected it shows no contents when clicked


Robin.

---

### Post by ddrichardson on 2007-09-25
If there is only one hard disk then try mounting sdb1 manually.

---

### Post by Robbyx on 2007-09-26
> **ddrichardson said:**
> If there is only one hard disk then try mounting sdb1 manually.

I have a number of disks in the machine including two satas which are raided together, through a 3ware card, but I have never been sure if the raid has been set up properly. I have to ring the manufacturer for support!

In my media folder I am seeing  folders called sda1 and sdb1. Is the sdb1 the recorder or the raided drive. My fstab shows I have previously mounted sdb1. This was set up long before I bought the recorder.

Here is my fstab:

```
proc /proc proc defaults 0 0
tmpfs /dev/shm tmpfs defaults,ro 0 0
usbfs /proc/bus/usb usbfs auto 0 0
# Entry for /dev/hda1 :
UUID=221d448e-c456-4e67-b1f4-675a654e16c8 / ext3 defaults,errors=remount-ro,data=writeback,noatime 0 0
# Entry for /dev/hda5 :
UUID=5abbef3f-03f4-4927-868f-93ec33fe1a6f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb5 /media/hdb5 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb6 /media/hdb6 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb7 /media/hdb7 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd1 /media/hdd1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd5 /media/win2k4msi ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
```

It seems to me that sdb1 ihas nothing to do with the recorder and that I have mounted sdb1 as a serial drive. Do you agree? I seem to have done this even though the second serial drive is supposed to be raided with the first. 

I think I  still have to mount the recorder. Assuming that sdb1 is not being used by the recorder. However clicking on sdb1 in media does not open anyithing. No reaction so is it redundant?


 I am a bit muddled at the output of dmesg | tail. Is it showing the recorder as sdb or sdb1 or not at all ? I ran dmesg | tail after I plugged in the recorder and it only shows the one drive because all the rest were previously loaded.

I am concerned that I try to load the recorder onto an existing serial drive. How do you suggest I do it? 

As you can see I am confused.

Thanks for you support and help 

Robin

---

### Post by ddrichardson on 2007-09-26
dmesg is showing a removeable device so would believe it to be the recorder. If the raid card is working as it should (assuming it's striping and not mirroring) then only one drive would be visible.

---

### Post by Robbyx on 2007-09-26
The raid drive is supposed to be mirroring. Does that alter your view on what the sdb1 drive is?

---

### Post by ddrichardson on 2007-09-26
Yes - I would assume that mirroring would present two devices not one.

---

### Post by Robbyx on 2007-09-28
I have disconnected the two raid drives, but left the raid card in the slot. 

I ran dmesg after connecting the dictation machine to the usb port.

```
robin@robin-desktop:~$ dmesg | tail
[23964.737891] sda: Write Protect is off
[23964.737896] sda: Mode Sense: 0b 00 00 08
[23964.737898] sda: assuming drive cache: write through
[23964.756841] SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
[23964.769807] sda: Write Protect is off
[23964.769812] sda: Mode Sense: 0b 00 00 08
[23964.769815] sda: assuming drive cache: write through
[23964.770178]  sda: sda1
[23964.808949] sd 5:0:0:0: Attached scsi removable disk sda
[23964.821359] sd 5:0:0:0: Attached scsi generic sg0 type 0

```


The dictating machine has 16megs of memory so clearly it is being picked up by Ubuntu.

The serial raid drive is mounted in sda1. My fstab shows it as:

/dev/sda1 /media/sda1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0

Would you mind suggesting a way to mount the sda drive that is the digital dictating machine? I believe one way is to quote the drive uuid but i do not know how to find it or the syntax for the fstab line.

I have just run sudo fdisk -l and this shows the drive as sda1.

Robin

---

### Post by ddrichardson on 2007-09-28
To mount by UUID```
mount -U uuid
```
Find a UUID by:```
sudo vol_id -u partition
```

---

### Post by Robbyx on 2007-09-29
> **ddrichardson said:**
> To mount by UUID```
mount -U uuid
```
Find a UUID by:```
sudo vol_id -u partition
```

Appologies for asking for clarification. Can you please suggest an exact code for the command because these are my tries so far:

```
robin@robin-desktop:~$ sudo vol_id -u partition
partition: error open volume
robin@robin-desktop:~$ sudo vol_id -u
Usage: vol_id [options] <device>
 --export        export key/value pairs
  -t             filesystem type
  -l             filesystem label
  -u             filesystem uuid
  -L             raw label
 --skip-raid     don't probe for raid
 --probe-all     find possibly conflicting signatures
 --help

robin@robin-desktop:~$ sudo vol_id -u skip-raid probe-all
probe-all: error open volume
robin@robin-desktop:~$ sudo vol_id -u partition
partition: error open volume
robin@robin-desktop:~$ sudo vol_id -u sdb1
Password:
sdb1: error open volume


```

As you can see I have tried variations on a theme for the command.

When plugged in and on the Digtal Recorder is being allocated to sdb1. As I have not mounted it I do not know the syntax for the device,  in the vol_id command


Robin

---

### Post by ddrichardson on 2007-09-29
```
sudo vol_id -u /dev/sdb1
```

---

### Post by Robbyx on 2007-09-29
Thank you for you help. I am most grateful. I have just run your  latest version of the command and it does not give an error message but nor does it give a uid. I ran the command after the record was connected and on.

[HTML]robin@robin-desktop:~$ 
robin@robin-desktop:~$ sudo vol_id -u /dev/sdb1
robin@robin-desktop:~$ 
[/HTML]

Is there another way to get the UID?

Robin

---

### Post by ddrichardson on 2007-09-29
Not that I know of, sorry. Hopefully someone else does.

---

