---
title: "I Can't Type in Udev! or .rcbash for that matter."
date: 2013-06-15
forum: General Help
---

### Post by FMFCorpsman on 2013-06-15
I am trying to get Ubuntu to recognize my Kindle. I found a way to do it and it was going well until I got to Udev. I was unable to type both times I was in and now I have two recorded instances of access and percieved changes I will need to figure out how to wipe clean once I can type. Any ideas? Thanks.

```
sudo vi /etc/udev/rules.d/51-android.rules
```

This what I typed to get in.

---

### Post by HiImTye on 2013-06-15
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
after reading your post, I still don't know what you were trying to do, or what your question is

---

### Post by MG&amp;TL on 2013-06-15
> **FMFCorpsman said:**
> 
```
sudo** vi **/etc/udev/rules.d/51-android.rules
```

This what I typed to get in.

Unless you're accustomed to *vi* (an awesome editor, by the way), you're going to be confused when you start using it, as it's a modal editor quite unlike any other. Use *nano* instead or learn how to use *vi*.

---

### Post by HiImTye on 2013-06-15
> **MG&TL said:**
> Unless you're accustomed to vioh I get it haha
yeah, use nano, and learn vi/[vim]("https://www.linux.com/learn/tutorials/228600-vim-101-a-beginners-guide-to-vim")
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by FMFCorpsman on 2013-06-15
HilmTye, sorry I wasn't clearer. Ubuntu wasn't recognizing my Kindle, so I needed to go into Udev and put a string of info in that I got from lsusb

```
lsusb
```

Got me this:
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 1949:000a Lab126 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e004 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:58c2 Realtek Semiconductor Corp.

See Lab126? That's my kindle attached to the laptop via usb. The key info I needed for Udev was the I.D 1949 and 000a.

```
sudo nano /etc/udev/rules.d/51-android.rules
```

I got lucky here and was able to type this in Udev:

```
SUBSYSTEM=="usb", ATTR{idVendor}=="1949", ATTR{idProduct}=="000a", MODE="0666"
```

once that went without a hitch did a:

```
dmesg
```

and got this:

[ 1204.023940] usb 3-2: new high-speed USB device number 3 using xhci_hcd
[ 1204.046536] usb 3-2: New USB device found, idVendor=1949, idProduct=000a
[ 1204.046547] usb 3-2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1204.046553] usb 3-2: Product: Kindle
[ 1204.046557] usb 3-2: Manufacturer: Amazon
[ 1204.046562] usb 3-2: SerialNumber: D026A0A0235310KQ
[ 1343.891953] usb 3-2: USB disconnect, device number 3
[ 1354.835975] usb 3-4: new high-speed USB device number 4 using xhci_hcd
[ 1354.858865] usb 3-4: New USB device found, idVendor=1949, idProduct=000a
[ 1354.858876] usb 3-4: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1354.858881] usb 3-4: Product: Kindle
[ 1354.858886] usb 3-4: Manufacturer: Amazon
[ 1354.858890] usb 3-4: SerialNumber: D026A0A0235310KQ
[ 2681.199083] wlan0: authenticate with 00:17:9a:32:38:6a
[ 2681.207998] wlan0: direct probe to 00:17:9a:32:38:6a (try 1/3)
[ 2681.410097] wlan0: direct probe to 00:17:9a:32:38:6a (try 2/3)
[ 2681.613954] wlan0: direct probe to 00:17:9a:32:38:6a (try 3/3)
[ 2681.818015] wlan0: authentication with 00:17:9a:32:38:6a timed out
[ 7531.718603] usb 3-4: USB disconnect, device number 4
[ 7535.682330] usb 3-4: new high-speed USB device number 5 using xhci_hcd
[ 7535.704786] usb 3-4: New USB device found, idVendor=1949, idProduct=000a
[ 7535.704796] usb 3-4: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 7535.704802] usb 3-4: Product: Kindle
[ 7535.704806] usb 3-4: Manufacturer: Amazon
[ 7535.704811] usb 3-4: SerialNumber: D026A0A0235310KQ

Which was a lovely sight!

Next made a place to mount it:

```
sudo mkdir -p /media/Kindle sudo
 chmod 755 /media/Kindle
```

This next step now has failed me and more research is needed:

```
mtpfs -o allow_other /media/Kindle
```

I got this:
mtpfs -o allow_other /media/Kindle
fusermount: failed to open /etc/fuse.conf: Permission denied
fusermount: user has no write access to mountpoint /media/Kindle

Now you ask, did I check fuse.conf before hand, yes I did and it said: "user_allow_other"

So this is where I am stuck now, I can't be more descriptive than I have been. This is obnoxiously apparent, that it is not all my work, but these things worked for him and for me to a point.

I am learning, and thats important. Well, so is getting the kindle recognized.

---

### Post by HiImTye on 2013-06-15
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
only root can write to /media, so do the mtpfs command with sudo

---

