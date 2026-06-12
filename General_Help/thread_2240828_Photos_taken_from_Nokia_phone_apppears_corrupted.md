---
title: "Photos taken from Nokia phone apppears corrupted"
date: 2014-08-22
forum: General Help
---

### Post by linuxyogi on 2014-08-22
Hi,

I tried to open some jpeg (not jpg) images for the SD card of my Nokia Asha 501 connected via micro usb cable but they

are appearing as corrupted. 

But fact is I can view those same images on my phone perfectly.

Since those images are in jpeg (not jpg) format I had a hard time finding an app. Most viewers won't open them.

After some searching I found an app called feh. Shutter can also open those images but the result is the same so its not a feh specific issue.

I am attaching an image. Please see if you can find out the problem.

---

### Post by Impavidus on 2014-08-22
That sample file is according to file```
$ file sample.jpg 
sample.jpg: JPEG image data, JFIF standard 1.01, comment: "CREATOR: gd-jpeg v1.0 (using IJG JPEG v80), quality = 75"
```The exif standard is more common, but basically all image programs should be able to open it. The reason the jpg extension exists next to the jpeg extension is an old convention on DOS file systems that extensions can be at most 3 characters long. Both extensions denote the same file format.

This seems more like file corruption. You may have a bad SD card or reader, file system corruption, whatever.

---

### Post by linuxyogi on 2014-08-23
> **Impavidus said:**
> That sample file is according to file```
$ file sample.jpg 
sample.jpg: JPEG image data, JFIF standard 1.01, comment: "CREATOR: gd-jpeg v1.0 (using IJG JPEG v80), quality = 75"
```The exif standard is more common, but basically all image programs should be able to open it. The reason the jpg extension exists next to the jpeg extension is an old convention on DOS file systems that extensions can be at most 3 characters long. Both extensions denote the same file format.

This seems more like file corruption. You may have a bad SD card or reader, file system corruption, whatever.

I did 

```
dd if=/dev/zero of=/dev/sdb bs=4M   
```

Then created a FAT32 partition with Gparted and restored the data. Then when I tried to open those files on the phone which previously used to open perfectly some of them refused to open.

Then I copied some new files and and my phone read them properly.

Just now I took a photo and opened it on my phone and it got properly displayed but again when I tried to open the photo from Lubuntu its appearing as corrupted.

I also opened a file which was downloaded from the web and feh opens that without any issues.

BTW this ^^ particular jpg image was one of the files that I had restored.

Really confusing.

---

### Post by sbnwl on 2014-08-23
How did you try to open the file? Did you copy the file to your lubuntu computer from the mounted SD card before trying to open it? If you try to open the file directly which is lying on the mounted SD card it might look corrupted.

First transfer/copy the file to your desktop and then try to open it...

---

### Post by linuxyogi on 2014-08-23
> **sbnwl said:**
> How did you try to open the file? Did you copy the file to your lubuntu computer from the mounted SD card before trying to open it? If you try to open the file directly which is lying on the mounted SD card it might look corrupted.

First transfer/copy the file to your desktop and then try to open it...

Copied the file to hard drive but same result.

---

### Post by sbnwl on 2014-08-23
I don't think there is anything wrong with your SDCard as long as the phone is able to open them correctly from the SDCard. The problem might lie in the copying the file from mounted SDCard to your computer.


  ```
If you have a card reader, you can give it a try. Pick out the SDcard from you phone (after switching it off) and insert it into a usb card reader. Then plug the card reader it into your computer. If the images open correctly then the only fault lies with the Ubuntu's handling of the phone in accessing its storage space.
```

---

### Post by sotiris2 on 2014-08-23
Can you get the file to your computer in a more indirect way? As in if you have wifi/internet to your phone upload it to google drive or similar and download it ? Or email it to your self? That is in order to make sure it's not actually being corrupted during transfer due to linux not supporting your phone perfectly etc.

---

### Post by linuxyogi on 2014-08-23
I don't have a card reader. I uploaded the image to Facebook and downloaded it back to my HDD.

Image attached.

If the micro usb cable is faulty then how come data is getting transferred to phone correctly ? and secondly not all files from the phone are appearing as corrupted only photos taken by the camera is appearing like that.

Photos downloaded from the web which are on the SD card are getting displayed on the PC correctly.

---

### Post by sotiris2 on 2014-08-23
It's not the cable's fault. Typically smart-phones don't appear as pure mass storage devices but use different protocols and you can get weird results.
I can't find much in google about asha phones and linux. 

Can you do ```
lsusb
```and
```
usb-devices
``` (copy only the section for your phone?

Maybe if we can see how it is detected we 'll have more luck troubleshooting it.

---

### Post by linuxyogi on 2014-08-23
```
 
Bus 002 Device 010: ID 0421:0683 Nokia Mobile Phones 

```

```
T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0421 ProdID=0683 Rev=14.00
S:  Manufacturer=Nokia
S:  Product=501
S:  SerialNumber=357898052871304
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


```

AFAIK Nokia Asha 501 is not a smart phone. Its just an entry level touch screen phone.


```
 $ identify corrupted.jpeg 
corrupted.jpeg JPEG 2048x1536 2048x1536+0+0 8-bit sRGB 526KB 0.000u 0:00.010

```

---

### Post by sotiris2 on 2014-08-23
Well it uses the driver for usb-storage like usb sticks etc... But it doesn't work... Does the phone have a 'setting' to connect it to a pc/usb? My android phone has one which basically i understand makes it present it's sdcard as a standar usb-device and it's more reliable. If I don't do that I can't tranfer some kinds of file from it though it appears to be mounted. Maybe your nokia phone also has a similar setting.

---

### Post by linuxyogi on 2014-08-23
> **sotiris2 said:**
> Well it uses the driver for usb-storage like usb sticks etc... But it doesn't work... Does the phone have a 'setting' to connect it to a pc/usb? My android phone has one which basically i understand makes it present it's sdcard as a standar usb-device and it's more reliable. If I don't do that I can't tranfer some kinds of file from it though it appears to be mounted. Maybe your nokia phone also has a similar setting.

I see 4 modes namely USB mode, Charging only, Modem, and Mass Storage.

The deafult is USB mode but in USB mode no new device is created in /dev. Its only when I select Mass Storage it appears in the file manager.

---

### Post by sotiris2 on 2014-08-23
And the problems appears when using mass storage?

---

### Post by linuxyogi on 2014-08-23
> **sotiris2 said:**
> And the problems appears when using mass storage?

Yes, that seems to be the only way to access the SD card.

---

### Post by sbnwl on 2014-08-23
You don't have the card reader.... THEN.... Then what...?


Can you send the original image?
 If you upload any image to facebook, it no longer remains the same as original one. 
It is scaled and repixelated (Or resampled) in facebook. 
The original exif info is preserved only if you gmail it to yourself from your phone as attachment. Then download it back on some computer from gmail and open it. I believe then it should look okay when you see it....

---

### Post by linuxyogi on 2014-08-23
> **sbnwl said:**
> You don't have the card reader.... THEN.... Then what...?


Can you send the original image?
 If you upload any image to facebook, it no longer remains the same as original one. 
It is scaled and repixelated (Or resampled) in facebook. 
The original exif info is preserved only if you gmail it to yourself from your phone as attachment. Then download it back on some computer from gmail and open it. I believe then it should look okay when you see it....

This phone is simply pathetic. When I purchased this phone I found that the email app cant attach any files.

Recently I received a software update and now I see that they have added this feature.

The image downloaded from my Gmail account is opening perfectly. So that means my a) my SD card is okay and b) feh supports the specifications of the jpeg. 

I can transfer files to the phone which the phone can read. I can read those files from my PC too.

:confused:

---

### Post by sbnwl on 2014-08-24
```
This phone is simply pathetic. When I purchased this phone I found that the email app cant attach any files.
```

I agree, their software is half baked actually...

Nokia was good only before the Microsoft-Nokia Deal...

Now Nokia is no longer the one it was once...

---

