---
title: "Help With USB Drives (Not Working)"
date: 2013-02-17
forum: General Help
---

### Post by daTomoT on 2013-02-17
Hi all,

Just looking for some help with my data storages. I can't load them, which is a real pain. I've tried:

32GB SD Card (From my DSLR)
1TB WD 'My Passport' (USB)
8GB Cruzer Edge USB Drive

When I put the SD card in, the error says 'Could not display "/media/tom/F84E-1690". The location is not a folder.' and I cannot access the card's contents.

When I plug the Hard Drive in, the error says 'Could not display "/media/tom/Tom's Drive". The location is not a folder.' and I cannot access the drive's contents

When I put the USB Drive in, the error says 'Could not display "/media/tom/E03B-0B93" The location is not a folder." and I cannot access the drive's contents.

So basically, the locations are not folders and I cannot access them. It's a real pain having to load my windows duel boot to import my pictures and put files onto my drives. I'm trying too become ubuntu-dependat (but for gaming), and this is knocking me down.

Ubuntu 12.10 on a Dell laptop. Can anybody sort me out?

Tom.

---

### Post by Bucky Ball on 2013-02-17
Which release and flavour are you using?

---

### Post by daTomoT on 2013-02-17
Ubuntu 12.10 Quantal Quetzal, Unity DE.

---

### Post by daTomoT on 2013-02-18
Still nobody? I still need a fix!

---

### Post by Bucky Ball on 2013-02-18
A simple search could get you started. See if you can find some clues here:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=Could+not+display++The+location+is+not+a+folder&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=Could+not+display++The+location+is+not+a+folder&ql=)

---

### Post by sudodus on 2013-02-18
There can be several causes for your problems.

1. Your drives may have file systems, that cannot be read by Ubuntu without a special driver.

Check in Windows, what is the name of the file systems!

- FAT32 and NTFS can be read and written by linux
- exFAT needs a special driver for linux

2. You try to mount the drives in some strange way. Do you simply get this message automatically? Or are you trying to mount the devices manually?

3. There is really something wrong with your Ubuntu system ...

---

### Post by HermanAB on 2013-02-18
Howdy,

The trick is to use the built-in Linux debug capabilities:

$ sudo tail -f /var/log/messages

Plug the thing in.

Read what is displayed and Google for answers.

---

### Post by n4pgw on 2013-02-18
I found that some USB devices only work when plugged directly into the computer rather than into an external hub.

---

### Post by daTomoT on 2013-02-18
> **Bucky Ball said:**
> A simple search could get you started. See if you can find some clues here:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=Could+not+display++The+location+is+not+a+folder&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=Could+not+display++The+location+is+not+a+folder&ql=)

Well, I had a look around and lots of people were having issues with the exo-utils package. I used ```
sudo apt-get remove exo-utils
``` but it told me it wasn't installed, and recommended I use a ```
sudo apt-get autoremove
``` to sort out a few packages, so I did, but to no avail. 

> **sudodus said:**
> There can be several causes for your problems.

1. Your drives may have file systems, that cannot be read by Ubuntu without a special driver.

Check in Windows, what is the name of the file systems!

- FAT32 and NTFS can be read and written by linux
- exFAT needs a special driver for linux

2. You try to mount the drives in some strange way. Do you simply get this message automatically? Or are you trying to mount the devices manually?

3. There is really something wrong with your Ubuntu system ...

1. The File Systems are Fat32 and NTFS
2. It comes up automatically
3. Poo.

> **HermanAB said:**
> Howdy,

The trick is to use the built-in Linux debug capabilities:

$ sudo tail -f /var/log/messages

Plug the thing in.

Read what is displayed and Google for answers.

I put the USB in, tried it and it said ```
tail: cannot open `/var/log/messages' for reading: No such file or directory
```, and I tried it again without it plugged in, and received the same. 

**So, any other suggestions? Sorry to be a pain.**

---

### Post by steeldriver on 2013-02-18
Not sure what file HermanAB had in mind, but I would try plugging the device(s) in after doing

```
tail -f /var/log/**syslog**
```That seems to be where pluggable USB / udev messages go - at least on my system (12.04)

---

### Post by Bucky Ball on 2013-02-18
You might even try plugging it in and checking the last entries in dmesg.

---

### Post by sudodus on 2013-02-19
> **daTomoT said:**
> 
1. The File Systems are Fat32 and NTFS
2. It comes up automatically

I'm trying to narrow down the problem: Is it due to hardware or software?

- Did I understand correctly from your first post, that Windows can read the drives ***in the same computer*** (dual boot)?

- What happens when you boot from a CD/USB drive, for example your Ubuntu install drive? These USB devices should automount and be available for read and write. If this does not work, I suggest you download the newest 12.04 LTS iso file and try with that version booted from a CD/USB drive.

- Have you tried different USB ports of the computer?

---

### Post by fdrake on 2013-02-19
what is the output for :
```

ls -l /media/

```

---

### Post by daTomoT on 2013-02-19
> **steeldriver said:**
> Not sure what file HermanAB had in mind, but I would try plugging the device(s) in after doing

```
tail -f /var/log/**syslog**
```That seems to be where pluggable USB / udev messages go - at least on my system (12.04)

I did so, and received the output

```
Feb 19 11:42:08 ubuntu kernel: [  247.003356] usb 2-1.2: new high-speed USB device number 4 using ehci_hcd
Feb 19 11:42:08 ubuntu kernel: [  247.096092] usb 2-1.2: New USB device found, idVendor=0781, idProduct=556b
Feb 19 11:42:08 ubuntu kernel: [  247.096099] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 19 11:42:08 ubuntu kernel: [  247.096104] usb 2-1.2: Product: Cruzer Edge
Feb 19 11:42:08 ubuntu kernel: [  247.096108] usb 2-1.2: Manufacturer: SanDisk
Feb 19 11:42:08 ubuntu kernel: [  247.096111] usb 2-1.2: SerialNumber: 20053550830CA000593B
Feb 19 11:42:08 ubuntu mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Feb 19 11:42:08 ubuntu mtp-probe: bus: 2, device: 4 was not an MTP device
Feb 19 11:42:09 ubuntu kernel: [  248.229885] Initializing USB Mass Storage driver...
Feb 19 11:42:09 ubuntu kernel: [  248.230009] scsi5 : usb-storage 2-1.2:1.0
Feb 19 11:42:09 ubuntu kernel: [  248.230084] usbcore: registered new interface driver usb-storage
Feb 19 11:42:09 ubuntu kernel: [  248.230086] USB Mass Storage support registered.
Feb 19 11:42:09 ubuntu kernel: [  248.283542] usbcore: registered new interface driver uas
Feb 19 11:42:10 ubuntu kernel: [  249.229079] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Edge      1.26 PQ: 0 ANSI: 5
Feb 19 11:42:10 ubuntu kernel: [  249.231438] sd 5:0:0:0: Attached scsi generic sg2 type 0
Feb 19 11:42:10 ubuntu kernel: [  249.233052] sd 5:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
Feb 19 11:42:10 ubuntu kernel: [  249.234377] sd 5:0:0:0: [sdb] Write Protect is off
Feb 19 11:42:10 ubuntu kernel: [  249.234383] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
Feb 19 11:42:10 ubuntu kernel: [  249.235123] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Feb 19 11:42:10 ubuntu kernel: [  249.250665]  sdb: sdb1
Feb 19 11:42:10 ubuntu kernel: [  249.253711] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Feb 19 11:42:11 ubuntu udisksd[1938]: Mounted /dev/sdb1 at /media/tom/E03B-0B93 on behalf of uid 1000
Feb 19 11:42:53 ubuntu kernel: [  292.029344] [UFW BLOCK] IN=eth1 OUT= MAC=
```

I think that's all that's relevant. Does that help in any way?

> **Bucky Ball said:**
> You might even try plugging it in and checking the last entries in dmesg.

Okay, this is what it gave me.

```
[  416.020792] usb 2-1.2: Product: Cruzer Edge
[  416.020796] usb 2-1.2: Manufacturer: SanDisk
[  416.020799] usb 2-1.2: SerialNumber: 20053550830CA000593B
[  416.021305] scsi6 : usb-storage 2-1.2:1.0
[  417.019833] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer E****dge      1.26 PQ: 0 ANSI: 5
[  417.020710] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  417.023547] sd 6:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[  417.025056] sd 6:0:0:0: [sdb] Write Protect is off
[  417.025061] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  417.025779] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  417.040927]  sdb: sdb1
[  417.043629] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

Again, what does this tell us?


**Either way, after using these commands I still receive the 'This location is not a folder.' error. What else is there we can do?**

---

### Post by sudodus on 2013-02-19
- What happens when you boot from a CD/USB drive, for example your Ubuntu 12.10 install drive? These USB devices should automount and be available for read and write.

If this does not work, I suggest you download the newest 12.04 LTS iso file and try with that version booted from a CD/USB drive.

---

### Post by Bucky Ball on 2013-02-19
From your dmesg output:

[  417.043629] sd 6:0:0:0: [sdb] Attached SCSI removable disk

That is probably it if you plugged in then immediately checked dmesg, so looks like it is being recognised at least.

---

### Post by fdrake on 2013-02-19
post the output if you can:
> **fdrake said:**
> what is the output for :
```

ls -l /media/

```

---

### Post by daTomoT on 2013-02-19
Hi all,

I don't know which line of coding did it, but I can now access all of my external drives!

Thanks to everybody who came in here, I can't tell you who gave me the fix though, possibly a few of you!

[B]Thanks,

Tom.[/B]

---

### Post by Bucky Ball on 2013-02-20
All good Tom. Enjoy the OS, the forums and the learning curve. ;)

---

### Post by parag2 on 2013-09-12
Check the permissions of /media with
```
sudo ls -o /media/
```

it should show a 'user' folder (user being your login name)
The folder should belong to 'user' and not 'root'. If it says root, do

```
sudo chown user:user /media/user
```
(replace 'user' with your login name).

It should work now!!
Cheers!!  :)

---

### Post by Bucky Ball on 2013-09-12
***Thread closed.***

Hello and welcome, parag2.

While your comments are appreciated, this thread is solved and has been for seven months. Please move along, nothing to see here. ;)

---

