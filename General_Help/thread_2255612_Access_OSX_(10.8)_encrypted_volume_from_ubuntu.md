---
title: "Access OSX (10.8) encrypted volume from ubuntu"
date: 2014-12-06
forum: General Help
---

### Post by bogren on 2014-12-06
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]                I need to access my two old drives (one hdd one ssd) from my  Macbook which I managed to kill with a couple of glasses of water. The  drives is still working though and shows up in 'Disks', but they where  encrypted in filevault if I remember correctly. This was a year ago. I  have a new Asus zenbook now with Ubuntu 14.04 LTS. 


  The ssd mounts automatically but I have no access to the  "User-private folders". So probably it is just an encrypted home-folder?


  The hdd is showing up in 'Disks' but the only mountable partition is  EFI (Don't ask me why those partitions are on my storage drive, it is  probably from when I only had 1 drive). On the big storage partition it  just says "1000 GB unknown".
  I really need to access the files on the drives. Can anyone help me? I  have been searching a bit about it to no real success. This is what  I've tried so far: 
  ```
sudo mount -t hfs -o loop,encryption=aes128 /dev/sdc2 /mnt/drive
Password: 
ioctl: LOOP_SET_STATUS: Invalid argument

```  I don't know if this is enough info for you so if you need anything else.....
  Appreciate it!
      
[/TD]
[/TR]
[/TABLE]

---

### Post by nerdtron on 2014-12-06
Hi,
Have you tried the suggestions on this thread? [http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write)

The first answer is "if you can still boot in OSX" while the second answer is force mounting in ubuntu.

---

### Post by bogren on 2014-12-06
Just tried it: 

```

sudo mount -t hfsplus -o force,rw /dev/sdc2 /media/storage
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by nerdtron on 2014-12-06
HHmmm.. usually the same error when a filesystem was not properly closed by the OS, or could be a corrupt journal, or when the system just can't read what it is. Happened to me a couple of times and my external hard drive (ntfs) fried all it's data.

What's the output of "dmesg | tail -n 50"?

---

### Post by bogren on 2014-12-06
```
$ dmesg | tail -n 50
[68948.065507] usb 3-1.2.2: Product: SteelS\xffffffec\xffffff80\xffffff81\xffffff80\xffffff81\xffffffcc\xffffff84\xffffff84\xffffffd0\xffffff89\xffffff89\xffffffcc\xffffff92\xffffff92DATA
[68948.065510] usb 3-1.2.2: Manufacturer: DATACOMP
[68948.065791] usb 3-1.2.2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[68948.065800] usb 3-1.2.2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[68948.086005] input: DATACOMP SteelS\xffffffec\xffffff80\xffffff81\xffffff80\xffffff81\xffffffcc\xffffff84\xffffff84\xffffffd0\xffffff89\xffffff89\xffffffcc\xffffff92\xffffff92DATA as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.2/3-1.2.2:1.0/input/input436
[68948.086302] hid-generic 0003:04B4:0101.0236: input,hidraw4: USB HID v1.00 Keyboard [DATACOMP SteelS\xffffffec\xffffff80\xffffff81\xffffff80\xffffff81\xffffffcc\xffffff84\xffffff84\xffffffd0\xffffff89\xffffff89\xffffffcc\xffffff92\xffffff92DATA] on usb-0000:00:14.0-1.2.2/input0
[68948.097835] input: DATACOMP SteelS\xffffffec\xffffff80\xffffff81\xffffff80\xffffff81\xffffffcc\xffffff84\xffffff84\xffffffd0\xffffff89\xffffff89\xffffffcc\xffffff92\xffffff92DATA as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.2/3-1.2.2:1.1/input/input437
[68948.098092] hid-generic 0003:04B4:0101.0237: input,hidraw5: USB HID v1.00 Device [DATACOMP SteelS\xffffffec\xffffff80\xffffff81\xffffff80\xffffff81\xffffffcc\xffffff84\xffffff84\xffffffd0\xffffff89\xffffff89\xffffffcc\xffffff92\xffffff92DATA] on usb-0000:00:14.0-1.2.2/input1
[68948.170062] usb 3-1.2.4: new full-speed USB device number 60 using xhci_hcd
[68948.189300] usb 3-1.2.4: New USB device found, idVendor=046d, idProduct=c52b
[68948.189307] usb 3-1.2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[68948.189311] usb 3-1.2.4: Product: USB Receiver
[68948.189314] usb 3-1.2.4: Manufacturer: Logitech
[68948.195820] logitech-djreceiver 0003:046D:C52B.023A: hiddev0,hidraw6: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-1.2.4/input2
[68948.197990] input: Logitech Unifying Device. Wireless PID:4024 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.4/3-1.2.4:1.2/0003:046D:C52B.023A/input/input438
[68948.198359] logitech-djdevice 0003:046D:C52B.023B: input,hidraw7: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:4024] on usb-0000:00:14.0-1.2.4:1
[68948.310521] usb 4-1: new SuperSpeed USB device number 4 using xhci_hcd
[68948.636029] usb 4-1: New USB device found, idVendor=2109, idProduct=0810
[68948.636038] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[68948.636042] usb 4-1: Product: 4-Port USB 3.0 Hub
[68948.636046] usb 4-1: Manufacturer: VIA Labs, Inc.
[68948.735508] hub 4-1:1.0: USB hub found
[68948.741702] hub 4-1:1.0: 4 ports detected
[68950.880751] usb 3-1.3: new high-speed USB device number 61 using xhci_hcd
[68950.898861] usb 3-1.3: New USB device found, idVendor=05e3, idProduct=0718
[68950.898868] usb 3-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[68950.898872] usb 3-1.3: Product: USB Storage
[68950.898875] usb 3-1.3: SerialNumber: 0000000000##
[68950.899638] usb-storage 3-1.3:1.0: USB Mass Storage device detected
[68950.899919] scsi14 : usb-storage 3-1.3:1.0
[68951.902169] scsi 14:0:0:0: Direct-Access     WDC WD10 TPVT-00HT5T1     0041 PQ: 0 ANSI: 0
[68951.902740] sd 14:0:0:0: Attached scsi generic sg2 type 0
[68951.903053] sd 14:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[68951.903470] sd 14:0:0:0: [sdc] Write Protect is off
[68951.903474] sd 14:0:0:0: [sdc] Mode Sense: 03 00 00 00
[68951.903880] sd 14:0:0:0: [sdc] No Caching mode page found
[68951.903885] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[68951.905249] sd 14:0:0:0: [sdc] No Caching mode page found
[68951.905258] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[68952.245775]  sdc: sdc1 sdc2 sdc3
[68952.247621] sd 14:0:0:0: [sdc] No Caching mode page found
[68952.247627] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[68952.247632] sd 14:0:0:0: [sdc] Attached SCSI disk
[68969.959147] asus_wmi: Unknown key cf pressed
[68970.909940] asus_wmi: Unknown key cf pressed
[73908.865333] [drm:intel_dp_start_link_train] *ERROR* too many full retries, give up
[83678.754373] hfsplus: unable to find HFS+ superblock
[83975.833331] hfsplus: unable to find HFS+ superblock
[84187.836272] systemd-hostnamed[27769]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[84217.893489] hfsplus: unable to find HFS+ superblock


```

---

### Post by bogren on 2014-12-10
I eventually ended up using my parents Macbook to connect the drives. I was emediately asked for the encryption password and could transfer the files to another drive and then format my own drives and place the files back on again.

---

