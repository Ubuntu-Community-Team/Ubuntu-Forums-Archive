---
title: "After a clean install, my USB ports do not recognise my MP3 devices."
date: 2014-03-03
forum: General Help
---

### Post by Fsirett on 2014-03-03
Another day, another problem.

This one is interesting...well maybe just frustrating.

I have three USB ports in the front of my computer and they worked fine before the reinstall, but have become somewhat picky since; I am assuming - read hoping - this is a configuration problem. 

What they do is read external disks and USB sticks without any problem, but stick when it comes to my MP3 devices. I thought it might be the devices and today bought another (MP3) that is also dead to the port. 

I tried changing the cables (three cables) and find that none of them make any difference. My Ebook reader is merrily charging away, but I am not able to get access to its memory. 

As an aside, I also tried to get the system to see my printer from another USB and it does not seem to be detecting that either. 

When I was running from the live CD it had no problems running the ports, so I am making the assumption it is something to do with the configuration. 

Does this sound familiar to anyone?

Frank Sirett

---

### Post by Yellow Pasque on 2014-03-03
So does dmesg show anything when you plug in the mp3 player?
```
dmesg | tail -n 20
```

---

### Post by Fsirett on 2014-03-03
I ran the code ( cheers for that, by the way) and this is what I got:

```
~$ dmesg | tail -n 20
[43618.688566] sd 11:0:0:0: [sdj] No Caching mode page found
[43618.688579] sd 11:0:0:0: [sdj] Assuming drive cache: write through
[43618.720703]  sdj: sdj1
[43620.279899] sd 11:0:0:0: [sdj] No Caching mode page found
[43620.279914] sd 11:0:0:0: [sdj] Assuming drive cache: write through
[43620.279924] sd 11:0:0:0: [sdj] Attached SCSI removable disk
[43620.797393] FAT-fs (sdj1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[43621.043487] systemd-hostnamed[12110]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[43629.352958] sdj: detected capacity change from 15999172608 to 0
[43632.206545] usb 1-6: USB disconnect, device number 31
[43632.484052] usb 1-6: new high-speed USB device number 32 using ehci-pci
[43632.623595] usb 1-6: New USB device found, idVendor=13fe, idProduct=3600
[43632.623607] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[43632.623614] usb 1-6: Product: USB DISK 2.0
[43632.623619] usb 1-6: Manufacturer:         
[43632.623624] usb 1-6: SerialNumber: 070223F14A0C6473
[43632.624082] usb-storage 1-6:1.0: USB Mass Storage device detected
[43632.624332] usb-storage 1-6:1.0: Quirks match for vid 13fe pid 3600: 4000
[43632.624851] scsi12 : usb-storage 1-6:1.0
[43632.831266] usb 1-6: USB disconnect, device number 32
```

What exactly this means escapes me, but it looks like there is something wrong in the file sysem, to me, but I am far from certain of anything. At the moment there is an ebook reader charging and an external disk as well as the new MP3 player. This player is a reader that takes a micro SD card. I find, since I listen to podcasts and rwrite over the flash a lot in a few months that I wear them out at an astonishing rate. Hopefully the cards last about the same time and are cheaper

I am now crawling to sleep for a few hours, so I will continue in the morning. I can see it wants me to run fsck, no problem there, but the stuff on nss-myhostname is completely new to me. No idea what to do with that or why I would want to when it tells me quite clearly that "Changing the local hostname might make it unresolveable." Times like this where I can really screw things up.

Once again my ignorance is on show for all to see.

Frank Sirett

---

### Post by Fsirett on 2014-03-04
As an addebdum, when I turned on the computer this morning the problem seems to have cleared itself up...for the moment, but that does not mean the problem has been solved 

I reran 

```
dmesg | tail -n 20
```

And I gat this, for your judgement and erudition and my education

```
~$ dmesg | tail -n 20
[  152.173485] sd 10:0:0:0: Attached scsi generic sg11 type 0
[  152.173996] sd 10:0:0:0: [sdk] 3893112 1024-byte logical blocks: (3.98 GB/3.71 GiB)
[  152.174592] sd 10:0:0:0: [sdk] Write Protect is off
[  152.174600] sd 10:0:0:0: [sdk] Mode Sense: 00 c0 00 00
[  152.177014] sd 10:0:0:0: [sdk] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
[  152.180827] sd 10:0:0:0: [sdk] 3893112 1024-byte logical blocks: (3.98 GB/3.71 GiB)
[  152.184670]  sdk:
[  152.193522] sd 10:0:0:0: [sdk] 3893112 1024-byte logical blocks: (3.98 GB/3.71 GiB)
[  152.195744] sd 10:0:0:0: [sdk] Attached SCSI removable disk
[  152.639911] FAT-fs (sdk): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  469.900109] usb 1-3: new high-speed USB device number 6 using ehci-pci
[  477.608614] usb 2-3: new full-speed USB device number 3 using ohci-pci
[  477.809145] usb 2-3: not running at top speed; connect to a high speed hub
[  477.827142] usb 2-3: New USB device found, idVendor=04e8, idProduct=329f
[  477.827154] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  477.827161] usb 2-3: Product: CLP-320 Series
[  477.827166] usb 2-3: Manufacturer: Samsung Electronics Co., Ltd.
[  477.827172] usb 2-3: SerialNumber: Z4PRBAEC201296R
[  478.099278] usblp 2-3:1.0: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04E8 pid 0x329F
[  478.099467] usbcore: registered new interface driver usblp

```

Everything now seems to work, but I am interested in knowing why it stopped working, if possible. I am afraid I do ot believe in "magic" and I hate having to use it as an excuse for things beginning to work. They just fail again later if I do.

Cheers

Frank Sirett

---

### Post by sudodus on 2014-03-04
> **Fsirett said:**
> As an addebdum, when I turned on the computer this morning the problem seems to have cleared itself up...for the moment, but that does not mean the problem has been solved 

Everything now seems to work, but I am interested in knowing why it stopped working, if possible. I am afraid I do ot believe in "magic" and I hate having to use it as an excuse for things beginning to work. They just fail again later if I do.

Cheers

Frank Sirett

It can take a few reboots until a new installation or re-installation has settled, so that all configuration files are correct. And in general, some errors are temporary, and things work again after reboot. If the problems do not come back, you need not worry about them. If they come back, try to remember what happened before and describe it, and we'll try to help you.

---

### Post by Fsirett on 2014-03-04
Cheers ! 

That is exactly what I needed to know. I always assumed if it did not work when it was in it was not working. 

I now have my printer back and all is well with the world. I am printing this, as every, thread for future reference. If one is going to be an idiot, it helps to have evidence.

In the meantime, I was counting my USB devices. I realise I have four plugged into the back. I know the mouse (or keyboard) is connected to another port, I know about the printer and the keyboard and am now left wondering what he other two are? I supose I could find out by disconnecting them or by tracing the leads to source, but the tangle and space makes me want to avoid that at all costs. It would be nice to move my external disk to the back, but what happens if I disconnect and...? 

In any case, my computer, my cubbyhole and myself sincerely thank you for helping me avoid facing the awful truths ( that never really existed, but certainly would have if I had a go at them) again.

Frank Sirett

---

