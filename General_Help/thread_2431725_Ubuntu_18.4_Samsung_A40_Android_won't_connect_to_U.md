---
title: "Ubuntu 18.4 Samsung A40 Android won't connect to USB"
date: 2019-11-20
forum: General Help
---

### Post by nocruoro on 2019-11-20
I regularly upload photos from my phone with my USB-C cable onto the pc...but just recently today it refused to connect to my laptop which runs on Ubuntu 18.4 Bionic Beaver.
 I do get a prompt on my phone to connect and press allow but my file manager on the pc either blinks white or the freezes before I can open folders. It only recharges my phone and it connected fine before.

I've checked default phone settings  and the cable is new. How do I troubleshoot this. Both phone and PC are updated. 
Quick note Edit: some google searches mention turning off some sort of mtp setting but my phone does not have such a thing in the settings.

---

### Post by nocruoro on 2019-11-21
Does this mtp name error help with anything? only sd card can be accessed nearly fine but the phone directories freeze up faster.
[ATTACH=CONFIG]284460[/ATTACH]

EDIT: reset to factory settingd did the trick. its a tedious process. But what causes the usb to dislike connecting to pc?

---

### Post by jetsam on 2019-11-21
I worked around similar symptoms once by fully charging the phone before plugging in.  Dumb, but it worked...

...[lsusb ]("https://linux.die.net/man/8/lsusb")is probably the next step.  That should get us cooking with oil...

Post results please of:
```
lsusb -v
```

You could do a before and after comparison for plugged and unplugged phone.  Read the options to filter the output so you're only looking at relevant device information...

---

### Post by nocruoro on 2019-11-21
> **jetsam said:**
> I worked around similar symptoms once by fully charging the phone before plugging in.  Dumb, but it worked...

...[lsusb ]("https://linux.die.net/man/8/lsusb")is probably the next step.  That should get us cooking with oil...

Post results please of:
```
lsusb -v
```

You could do a before and after comparison for plugged and unplugged phone.  Read the options to filter the output so you're only looking at relevant device information...

unfotunately it displays very long log and i cant copy and paste here. i get a message here saying my post is too long

I have tested developer settings and none of these in particular work well. 
> 
DEF
** Default USB Settings**
USB Tethering 
Transferring Files
MIDI
Transferring Images
Charging Phone Only 

Need to figure out why it crashes while copying large amount of files and which setting needs to be used. Folder is 400 images. **Another Factory Reset is tedious and out of the question. And Samsung also has terrible Customer Service.**

---

### Post by nocruoro on 2019-11-24
bump

---

### Post by dragonfly41 on 2019-11-24
For information, as an alternative route I am exploring use of gsconnect to connect Samsung Android tab 4 to Ubuntu.  I have installed KDEconnect in Samsung and gsconnect as extension in Chromium. Samsung KDEconnect does not yet pair with Ubuntu.

---

### Post by nocruoro on 2019-11-24
> **dragonfly41 said:**
> For information, as an alternative route I am exploring use of gsconnect to connect Samsung Android tab 4 to Ubuntu.  I have installed KDEconnect in Samsung and gsconnect as extension in Chromium. Samsung KDEconnect does not yet pair with Ubuntu.
Gsconnect doesn't work for chrome fro me, all i get is service unavailable

---

### Post by dragonfly41 on 2019-11-24
I have that same problem ("service unavailable" shows in chromium browser gsconnect button) and I am still trying to solve it.
I have read this "[COLOR=#545454]Ensure that devices are on the same local network with [/COLOR]ports[COLOR=#545454]1716 to 1764 "
[/COLOR][https://www.omgubuntu.co.uk/2018/05/ubuntu-18-10-gsconnect-extension-by-default](https://www.omgubuntu.co.uk/2018/05/ubuntu-18-10-gsconnect-extension-by-default)

---

### Post by nocruoro on 2019-11-27
[B]bump 

[/B][SIZE=3]still having difficulties connecting properly without android phone connecting properly[/SIZE]

---

### Post by nocruoro on 2019-11-30
bump.................

---

### Post by nocruoro on 2019-12-02
&#8203;bump i still need help with this

---

### Post by nocruoro on 2019-12-03
bump still dont have proper help. and samsung customer service havent been able to provide suggestions

---

### Post by mörgæs on 2019-12-04
A week ago a post appeared which mentioned
```
lsusb -v
```

as well as

> **jetsam said:**
> 
Read the options to filter the output so you're only looking at relevant device information.

I guess that following the advice is more efficient than bumping.

---

### Post by Holger_Gehrke on 2019-12-04
Unplug the phone. Wait a moment. Run 'lsusb' without any options. Plug the phone in. Wait a moment. Run 'lsusb' without any options. The output of the second run should have a new line for the phone. Use the ID (two sets of four hexadecimal digits separated by a colon, preceded by 'ID ') printed in that line in 'lsusb -v -d ID' instead of the placeholder ID. The output will still be quite long (~400 lines), but a lot shorter than a verbose (-v) listing of all USB-devices ...

Personally I find mtp to be unreliable and slow on Linux. The former might be due to every manufacturer interpreting the specs a bit differently, the latter is probably due to layers and layers of abstraction (fuse, gvfs ...). I just put a micro sd card in the phone, set the camera app to store it's images on the card and put the card in a reader connected to my PC to transfer. If it's just one or two small files, I use Bluetooth. And if I really need to put or get stuff to / from the internal memory of the phone, then I start an ssh-server on the PC and transfer the data via sftp from the phone (using cx explorer, but there's other tools that can do it).

Holger

---

### Post by nocruoro on 2019-12-04
Hello again Mörgæs and Holger
> **mörgæs said:**
> A week ago a post appeared which mentioned
```
lsusb -v
```

as well as



I guess that following the advice is more efficient than bumping.

[B]i did reply to that with this :)
[/B]
> **nocruoro said:**
> unfortunately it only displayed a very long log and i could not paste here for analysis. I got a forum message my post was too long

I have tested developer settings in my phone and none of the usb settings/modes in particular work well. 



Which one is it in the software downloader that i should test. 

I do have a windows a pc at home which i can connect to **but not always**, thats why i need to troubleshoot this ubuntu android problem.

[ATTACH=CONFIG]284554[/ATTACH]

---

### Post by SeijiSensei on 2019-12-04
I occasionally use the Wifi File Transfer Pro app from the Google Play store. It turns the phone into a mini web server and lets you upload/download files via wifi. It's not free, but it's not expensive either. I think I paid $3 for it some years back.

---

### Post by nocruoro on 2019-12-09
> **SeijiSensei said:**
> I occasionally use the Wifi File Transfer Pro app from the Google Play store. It turns the phone into a mini web server and lets you upload/download files via wifi. It's not free, but it's not expensive either. I think I paid $3 for it some years back.

Thanks but i'm trying to avoid paid programs on android. don't want my cards accesed through online vendors.

---

### Post by nocruoro on 2019-12-11
bump..

---

### Post by joe154 on 2020-07-30
TLDR: Given up on connecting the A40, so just confirming the issue. Thanks.

My A40 is invisible to Ubuntu 20.04. The phone charges when connected, but 'lsusb', 'lsusb -v' and 'adb -l' show nothing at all.
I plugged in a samsung S6. That was recognized. It had a different connector, so I tried a Samsung S10E which uses usb-c like the A40. They both showed up:

$ lsusb
...
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 078: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy series, misc. (MTP mode)
Bus 003 Device 019: ID 89e5:1001   USB OPTICAL MOUSE

And

Bus 003 Device 064: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy series, misc. (MTP mode)

The A40 returned this:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 019: ID 89e5:1001   USB OPTICAL MOUSE

It was the same with lsusb -v. It jumped from entry:
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18..

To

Bus 003 Device 019: ID 89e5:1001   USB OPTICAL MOUSE
Couldn't open device, some information will be missing
Device Descriptor: 
etc.

---

### Post by joe154 on 2020-07-30
*adb devices -l

---

