---
title: "Broke USB drive using dd command"
date: 2018-07-02
forum: General Help
---

### Post by xxbluesskyxx on 2018-07-02
Hello, i was using my Kingston DataTraveler 32 gb , and up to recently it stopped working, and i think its because it was corrupted. i followed [this tutorial]("https://www.addictivetips.com/ubuntu-linux-tips/fix-a-bad-hard-drive-on-linux/"). i tried the «Zero out a hard drive» method, and now my usb stick is no longer recognised on my ubuntu 16.04 system.



Thanks In Advance :P

Note: The usb was formatted in WBFS (Wii Backup File System)

Sorry if i posted this in the wrong place, this is my first post.

---

### Post by QIII on 2018-07-02
Hello!

After zeroing the device, did you then use gparted to create new partitions?

---

### Post by ajgreeny on 2018-07-02
When you "Zero out" a drive to repair the filesystem it does exactly what it says and removes everything from the drive; all partition tables, partitions, filesystems and any data.

To use it again you have to create a new partition table and at least one partition. The easiest way to do this for most is using gparted.

---

### Post by warmango on 2018-07-03
Open gparted, navigate to the USB, and then select devices, there should be an option to create a partition table there.

---

### Post by xxbluesskyxx on 2018-07-05
The thing is that i already tried using gparted , the usb didn't show up.

---

### Post by vanadium on 2018-07-05
- See whether it appears in the output of "lsblk" or "sudo blkid" or "sudo fdisk -l".
- See how the kernel reacts when you plug the drive in. Unplug the drive, wait a bit, plug it in then issue the command "dmesg | tail -n 30" to display the 30 last lines of kernel output: these will give an indication on whether the device is seen and on what the kernel tries to do with it.

---

### Post by xxbluesskyxx on 2018-07-08
This is the output of [COLOR=#000000]"sudo blkid" : [/COLOR]/dev/sda1: LABEL="Ubuntu" UUID="307cc36c-9e57-4fcf-b0cd-5cd86c1af065" TYPE="ext4" PARTUUID="10000000-01"/dev/sda5: UUID="4d2c459f-8192-4c16-a379-bcd22305dbd6" TYPE="swap" PARTUUID="10000000-05"

This is the output of [COLOR=#000000]"dmesg | tail -n 30" :
 [/COLOR][  228.699650] sd 6:0:0:0: [sdb] Write Protect is off
[  228.699652] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 00
[  228.701274] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  228.706434] sd 6:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  228.706437] sd 6:0:0:0: [sdb] Sense Key : Unit Attention [current] 
[  228.706440] sd 6:0:0:0: [sdb] Add. Sense: Not ready to ready change, medium may have changed
[  228.707703] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  230.728940] usb 2-2: USB disconnect, device number 5
[  249.732167] usb 2-2: new high-speed USB device number 6 using ehci-pci
[  249.892747] usb 2-2: New USB device found, idVendor=0930, idProduct=6544
[  249.892756] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  249.892761] usb 2-2: Product: DataTraveler 2.0
[  249.892766] usb 2-2: Manufacturer: Kingston
[  249.892771] usb 2-2: SerialNumber: 00241D8B55C2FD809934C56C
[  249.893624] usb-storage 2-2:1.0: USB Mass Storage device detected
[  249.895674] scsi host6: usb-storage 2-2:1.0
[  250.994406] scsi 6:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 4 CCS
[  250.994833] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  251.001978] sd 6:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.001982] sd 6:0:0:0: [sdb] Sense Key : Unit Attention [current] 
[  251.001985] sd 6:0:0:0: [sdb] Add. Sense: Not ready to ready change, medium may have changed
[  251.001989] sd 6:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[  251.001991] sd 6:0:0:0: [sdb] 0-byte physical blocks
[  251.002595] sd 6:0:0:0: [sdb] Write Protect is off
[  251.002597] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 00
[  251.003215] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  251.009359] sd 6:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.009363] sd 6:0:0:0: [sdb] Sense Key : Unit Attention [current] 
[  251.009367] sd 6:0:0:0: [sdb] Add. Sense: Not ready to ready change, medium may have changed
[  251.011100] sd 6:0:0:0: [sdb] Attached SCSI removable disk
 
All i understood was that my usb drive was /dev/sdb, since i only have a hard drive with 2 partitions on it.

i guess it does detect it in some way?

---

### Post by VMC on 2018-07-08
lsblk, then:
```
sudo mkfs.vfat /dev/sdb1
or
sudo mkfs.ext4 /dev/sdb1 
```

Replace "sdb1" with output

---

### Post by xxbluesskyxx on 2018-07-08
the output of command [COLOR=#000000][FONT=&quot]sudo mkfs.vfat /dev/sdb1 gives me this:
 [/FONT][/COLOR]mkfs.fat 3.0.28 (2015-05-16)mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)

And the output of [COLOR=#000000][FONT=&quot]sudo mkfs.ext4 /dev/sdb1 is this :
[/FONT][/COLOR]mke2fs 1.42.13 (17-May-2015)
mkfs.ext4: La taille rapportée du périphérique est zéro. La partition spécifiée est
	invalide ou la table de partitions n'a pas été relue après
	l'exécution de fdisk, dû au fait que la partition modifiée était
	occupée et utilisée. Vous devez ré-amorcer pour forcer une
	relecture de la table de partitions.

The french stuff is because my computer i in french but basically in english it says (Traslated with google translate) :
[SIZE=3][/SIZE][SIZE=2]The reported size of the device is zero. The specified partition is
invalid or the partition table was not replayed after
the execution of fdisk, due to the fact that the modified partition was
busy and used. You must re-boot to force a
replay of the partition table.[/SIZE]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-07-09
It still looks to me as if there is no partition table on that USB or the PT is corrupt.

It may be worth using the wipe menu option of mkusb [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) to return the USB to a standard, single partition, drive then if necessary use gparted to manipulate the partition as you wish.

---

### Post by The Cog on 2018-07-09
Can you please post the full output of
```
sudo parted -l
```
which should show us what the PC thinks is actually there on the stick.

And please use code tags round the copied output (use the **Go Advanced** button, highlight the text and press the **#** button in the editor) because it makes it much easier to read.

---

### Post by xxbluesskyxx on 2018-07-24
a

---

### Post by xxbluesskyxx on 2018-07-24
ok ill try that

---

### Post by xxbluesskyxx on 2018-07-24
ill try it

---

### Post by sudodus on 2018-07-24
Maybe the following link can help,

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

