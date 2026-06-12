---
title: "Damn memory card reader"
date: 2008-04-21
forum: General Help
---

### Post by 6205 on 2008-04-21
Hi,

I have installed into my PC internal USB memory card reader(unknown brand, it is black and that's all...), connected to motherboard and in Windows XP is everything fine, it was recognized as Generic USB device (preview image), but my Ubuntu 7.10 don't see it :confused: and only led diod on it is flashing rapidly...

I am very frustrated, because i have not found anywhere simple installation howto for such a device. Can somebody help me, or i have one less reason to boot into linux :( When will these basic things finally work?

---

### Post by ibuclaw on 2008-04-21
I think I'm right in saying that you can't see it because nothing is inserted.
Linux won't mount anything to your root file hierachy unless it detects a device with a readable filesystem on.

Infact, the fact that the device is flashing is very good news indeed!
It means that Linux has found the device and is talking to it. (Remember, No lights = Not Working)

Try inserting a memory card into the slot.
If nothing happens, I will address to that issue.

[EDIT]
If in doubt, remove any external USB devices from your PC and type the following command in the terminal
```
lsusb
```

Regards
Iain

---

### Post by 6205 on 2008-04-22
OK, i tried that, but nothing has changed. I wish if linux had better P'n'P support in 2008 :(

And regarding lsusb, here is output from terminal

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00db Microsoft Corp. 
Bus 003 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


I have USB KB+Mouse from Microsoft, and those last 4 devices are maybe related to that reader...

---

### Post by ibuclaw on 2008-04-22
OK, try inserting a memory stick and then typing in lsusb.

If you gain a new device in the "lsusb" output, then we can be certain that it is working.

If the device is showing, but isn't mounted to your "/media/" folder.
Then we can find the device in the "/dev/" folder
```
ls /dev/sd*
```
Your memory card will be the last one on the list.
ie, if your output was:
```
[COLOR="RoyalBlue"]/dev/sda   /dev/sdb   /dev/sdb2  /dev/sdb5  /dev/sdc
/dev/sda1  /dev/sdb1  /dev/sdb3  /dev/sdb6  /dev/sdc1[/COLOR]
```

It will be the "/dev/sdc1" device.

So we type in:
```
pmount /dev/sdc1 /media/**SDCard**
```
The above is just an example.
You can mount it to anywhere you want.

[EDIT]
I think Bus 5 is your Memory Card Reader.
Unlike the others, it has eight ports (I think that is 4 slots?)
[QUOTE=lsusb -v.txt]
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
[/QUOTE]

Regards
Iain

---

### Post by 6205 on 2008-04-22
Output from lsusb is the same without or with inserted memory card. I have inserted microSD card in SD adapter from Nokia phone...

---

### Post by ibuclaw on 2008-04-22
The only thing I can think of, just to be sure is for you to:
Reboot your computer.
Then boot into Ubuntu.
Login.
Insert your microSD card,
Wait for about 10 seconds.
Remove your microSD card.
Wait for about 10 seconds.
Then type in the terminal:
```
dmesg | grep scsi << ~/Desktop/dmesg-scsi.txt
```
And post the text file up.

If there is no activity, then there is something wrong with the hardware detection.
Though, not necessarily the detection of the Memory Card Reader.
It could be the detection of the Memory Card itself, and so the Linux Kernel isn't communicating properly with the device.

If that is the case, then this may be beyond what I can do to help.
And all I can recommend is that you switch to Hardy as soon as it's released. With an updated "2.6.24" kernel, which comes along with better hardware detection for new devices, etc. I can only hope that *that* may solve it for you.

Regards
Iain.

---

### Post by 6205 on 2008-04-22
Uhm...nothing happens after that command. Only "**>**" character had appeared in terminal and every next push of enter displays in every new line **>** characters...I think i give up and wait some time, linux needs time.....a lots of time :( 

But thanks for help anyway...

---

### Post by gotthardt on 2008-04-22
I think he meant:
```
dmesg | grep scsi >> ~/Desktop/dmesg-scsi.txt
```

notice the arrows point different.

BTW - I had the same problem. I found there was a jumper on the motherboard for USB power, put it in the non-standby mode and my internal USB card reader started to work. 

I think I may have messed it up temporarily by putting in a card the wrong way and USB query (lsusb) took a long time. I had to power it off then back on to get it and the mouse to work again.


When I run dmesg with my USB card reader I get stuff like this (this should be in the file from above too):
[   38.311414] usb-storage: device scan complete
[   38.318686] scsi 2:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   38.325025] scsi 2:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   38.331388] scsi 2:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   38.338935] scsi 2:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   38.341548] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   38.341597] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   38.343187] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   38.343242] sd 2:0:0:1: Attached scsi generic sg2 type 0
[   38.346796] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   38.346849] sd 2:0:0:2: Attached scsi generic sg3 type 0
[   38.348884] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   38.348936] sd 2:0:0:3: Attached scsi generic sg4 type 0

---

### Post by 6205 on 2008-04-23
OK...i have to enter instead of Desktop word Plocha in my language and some txt file was created on Desktop with content ->

[   19.199494] scsi0 : ata_piix
[   19.199567] scsi1 : ata_piix
[   19.893911] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0812N  TK10 PQ: 0 ANSI: 5
[   19.895303] scsi 1:0:0:0: CD-ROM            TEAC     DV-W516GDM       M4S2 PQ: 0 ANSI: 5
[   19.966383] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.966408] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   20.005992] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   20.006337] sr 1:0:0:0: Attached scsi CD-ROM sr0


Note: My HDD is Samsung, DVD-RW is Teac, anyway when i'm inserting SD card nothing happens and the file content is the same when creating with or without card inserted. Btw. i don't have any jumpers on board anywhere near internal USB connectors.

I still don't understand where may be the problem, because in Windows this reader behaves like standard removable disk with icon in tray "Safely remove hardware" - the same like generic USB keys, but i cannot of course remove it, because it's connected to internal USB on MB...

---

### Post by 6205 on 2008-04-25
I made yesterday clean installation of Hardy, but results are the same or worst and command [COLOR="Blue"]dmesg | grep scsi >> ~/Desktop/dmesg-scsi.txt[/COLOR]
creates empty text file on desktop so my reader is still useless :( I'm so tired from similar issues, i'm done with linux. I don't need this in 2008...

---

### Post by christianxxx on 2008-05-17
I have this problem as well! The dmesg-scsi.txt showed the card as /dev/sg3, but I was unable to mount it.
Mounting gave me "mount: /dev/sg3 is not a block device"

I have done this before, I don't understand how it could suddenly become a problem.

---

### Post by 6205 on 2008-05-19
Any update on this issue? Has anybody some frakin' suggestions for me ?

---

### Post by feld on 2008-05-19
yes. This thing is USB, right?

Disconnect it and reconnect it.  Use `dmesg` and show us the last 10 or so lines. It should show the device being connected.

Give us the output of `lsusb -v`. If you don't have that program, install it.

If you don't provide information, how are we supposed to guess what your problem is? We don't even know what hardware this is.

Also, Linux has FAR better PnP support than any other OS out there. I have dozens of devices that I can plug in and they immediately work in Linux but are completely unrecognized without me locating a driver in XP.

[quote="6205"]
I'm so tired from similar issues, i'm done with linux. I don't need this in 2008...
[/quote]

Then leave. Don't make stupid comments like that because you feel helpless and you think people are going to beg you to stay. That's not the way it works. If you want to go back to Microsoft and deal with their issues, their DRM, their backdoors for the gov't, their viruses, and their lack of source code (who knows what they're doing behind your back; you accepted their terms by using their software) then go right ahead. 

The Linux community is here to assist those who require assistance and are able to be assisted. There is a ton of documentation out there that could help you resolve your problem -- you just have to WANT to resolve it.

In closing,

1) Ask intelligent questions
2) Be patient
3) Don't be snobby
4) Enjoy this 'Revolution OS' that is literally changing the world and the way we do business.

---

### Post by 6205 on 2008-06-08
This HW is _internal USB_ so i can't re-connect it and looks into output files and they are anyway not showing anything..

---

### Post by 6205 on 2008-06-20
Frak me ! Working like a charm under openSUSE 11.0 :) Finally a linux distro with great HW support. Not to mention higly polished GNOME.. Highly recommended!

---

