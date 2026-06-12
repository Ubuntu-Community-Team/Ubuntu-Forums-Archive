---
title: "Ubuntu and fingerprint recognition"
date: 2006-07-25
forum: General Help
---

### Post by Jonathan Métillon on 2006-07-25
Hi,

I just got a new [Sony Vaio TX3]("http://crave.cnet.co.uk/laptops/0,39029450,49281462,00.htm") and everything works fine with Ubuntu.

Just had to deal with ndiswrapper to load [Intel drivers]("http://support.intel.com/support/wireless/wlan/sb/CS-010623.htm") for the PRO/Wireless 3945ABG (w39n51.inf).

What does not work out of the box is the fingerprint recognition. I searched Google and Synaptic packages and found nothing about it.

Is this something supported with Ubuntu? Is there a tutorial somewhere?

Thank you!

---

### Post by VosaxAlo on 2006-07-27
Hi Jonathan,

me too I have just got a new HP Compaq nw9440 with a fingerprint sensor. The hardware is recognized by Ubuntu, but I don't find any package to use it.
It will be very cool to have a login tool with fingerprint recognition.

---

### Post by Jonathan Métillon on 2006-07-28
> **VosaxAlo said:**
> It will be very cool to have a login tool with fingerprint recognition.

And a sudo!

---

### Post by Metacarpal on 2006-07-28
Apparently fingerprint recognition is [possible under Linux]("http://www.thinkgeek.com/gadgets/electronic/80be/"), I just wouldn't have a clue how to implement this in Ubuntu.

Hopefully, that link will make a good springboard for some of the real geniuses out there to track the necessary packages down!

---

### Post by Jonathan Métillon on 2006-08-07
Should I conclude that, at this time, yes this can *eventually* be supported on *some* devices, and even if it fits for me, there's no application to use with?

---

### Post by padre999 on 2006-08-07
> **Jonathan Métillon said:**
> Should I conclude that, at this time, yes this can *eventually* be supported on *some* devices, and even if it fits for me, there's no application to use with?
I found the following Wiki concerning fingerprint recognition:

[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

I don't know it is helpful to you. Probably your computer uses a different hardware. But at least it explains how to use the scanner with a software called pam_bioip.

---

### Post by Jonathan Métillon on 2006-08-10
> **padre999 said:**
> at least it explains how to use the scanner with a software called pam_bioip.

Very good! It will be of great value when I'll be able to use the device. But for now I found nothing. I don't even know how to discover what hardware it is.

---

### Post by shamrock_uk on 2006-08-10
Jonathan, 

Sorry I can't help with your fingerprint problem, google has turned up nothing for me either. 

Would you mind just confirming that "everything works" includes the widescreen, bluetooth and the internal ethernet card? And is the anti-shock system built in to the hardware, or do we miss out on that running Linux?

Thanks :)

---

### Post by Jonathan Métillon on 2006-08-11
> **shamrock_uk said:**
> Would you mind just confirming that "everything works" includes the widescreen, bluetooth and the internal ethernet card? And is the anti-shock system built in to the hardware, or do we miss out on that running Linux?

I can confirm that on Ubuntu 6.06 LTS,
[LIST]
[*]Widescreen works out of the box, but resolution was set to 1368x768 and I had to set it to 1366x768 which is the correct resolution.
[*]Bluetooth works out of the box. I installed Bluetooth Manager and Bluetooth File Sharing with Synaptics, and it detected my [Qtek S200.]("http://www.mobile-review.com/pda/review/htc-prophet-en.shtml") However, because I don't know what to type when the device asked me a password, I was not able to connect the two.
[*]Internal ethernet card and wireless do not work out of the box, but it was easy to setup using ndiswrapper to load [Intel drivers]("http://support.intel.com/support/wireless/wlan/sb/CS-010623.htm") for the PRO/Wireless 3945ABG (w39n51.inf). More info [here.]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")
[*]Anti-shock system was not tested. I'll wait before shocking my new 2500 € baby ;-)
[/LIST]

---

### Post by hashimoto on 2006-08-11
Does this help at all?: [http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader](http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader)

---

### Post by Jonathan Métillon on 2006-08-11
I just noticed that the Vaio TX3 is called TX770 in the USA and TX92 in Japan.

It might help to find ressources...

---

### Post by Jonathan Métillon on 2006-08-11
> **hashimoto said:**
> Does this help at all?

Indeed this looks helpful. But I need the drivers for the fingerprint reader. I just found out what hardware it is using *lspci*:

```
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
```

In the meantime I found a device from Alps Electric Co., Ltd. I think it's the MemoryStick/SD card reader (which works out of the box).

---

### Post by MrHorus on 2006-08-11
Nothing in the output of dmesg?

---

### Post by Jonathan Métillon on 2006-08-11
> **MrHorus said:**
> Nothing in the output of dmesg?

I don't know. I reviewed it but found nothing. For sure I missed it. Anyway, I now know what type of hardware it is, so I don't know what to find more from the dmesg.

Btw, I've had a search for SGS Thomson Microelectronics Fingerprint Reader and found nothing.

Also I tried to get help from #linuxbiometrics on Freenode but everyone seem asleep there :-)

---

### Post by shamrock_uk on 2006-08-12
This appears to have a walkthrough for your fingerprint scanner:

[http://www.qrivy.net/archive/html/linux-biometrics/2005-11/msg00002.html](http://www.qrivy.net/archive/html/linux-biometrics/2005-11/msg00002.html)

It seems to have the same vendor and product ID...

```
 idVendor           0x0483 SGS Thomson Microelectronics
>   idProduct          0x2016
```

It looks like he was having an error, but the solution is printed at the very bottom. The WIKI it links to also seems to deal with your *sudo* wish and allow you to use the scanner with non-root applications.

Hope it helps!





Many thanks for the quick reply to my questions :)

Do you get anything near the 9h battery life under Linux? 

Does the processor scale back as it's supposed to when unplugged?

I've heard that under Windows it scales back by 50%, so I was slightly worried that it wouldn't be able to play large .avi files (as my celeron 800 struggles), have you had any problems with performance of video files when it's unplugged? Can you play games like Metal Blob Solid (aka blobwars)?

And finally, the little mini-linux partition that does the "instant media" thing - does it get wiped by installing Linux? (obviously assuming we don't format it deliberately :))

I'll leave you in peace now ;)

Edit: The memory card reader works too?! You can just slide in the memory stick and retrieve photos? Hehe, I'm *this* close to shelling out for it. Where did you purchase yours from?

{Big edit to add info at top}

---

### Post by Jonathan Métillon on 2006-08-12
Many thanks for the ressources about the SGS Thomson sensor, shamrock_uk!
I'll look into that as soon as I can.

About the TX3,
[LIST]
[*]I don't get 9h autonomy with the standard battery. I get ~7h with Bluetooth+Wi-Fi switched off and ~5h switched on. And the screen it as the lowest brightness. Notice that these informations are provide by GNOME's Power Manager. It's not my own measures. Maybe the 9h they told you is using the large capacity battery.
[*]By default, the CPU throttle back to 800 Mhz. When in load, it switches to full speed, 1.2 Ghz. This behaviour is the same on battery or on AC power. When playing videos it goes full speed and it does not show any performance problem.
[*]I didn't know that the "instant media" thing was managed by a little mini-linux partition. But what's sure is that some software needed for it to run are deleted when formating, and the feature does not work anymore. When booting in AV MODE, it says something like "I can't find the software". And I don't care : Ubuntu boots super quick and hibernate mode works, so it's like if you had instant media anyway ;-)
[*]Memory card reader works. I tried it with photos taken from a Canon Ixus on SD Card and it did the job. However, I did not try the MemoryStick slot.
[*]I finally understood how Bluetooth file transfer works, [thanks to Randy Sparks]("http://ubuntuforums.org/showthread.php?t=94713"), and it does very well!
[*]I purchased it from [Vaio.fr]("http://www.vaio.fr/") A small shop with a very cool team.
[/LIST]

My advice is: if you are low on the green stuff and want to run Linux, go for a TX1 or TX2. You don't really need last marketing Intel CPU, penisprint reader, G-Shock sensor... But if 2500 € is ok for you, go for a TX3 (mine is a TX3XP/B). And if you want to run Windows, go to Hell :twisted: 

The Vaio Type T is a great computer and a the perfect balance between mobility and usability. For me, Type U is too small, Type S is too big. Notice that I'm really working with my unit: I'm a web developper and spend  more than 10h a day on it. So be assured that it's not just a gadget, it's really a profesionnal tool.

Also about the price, don't forget you'll have to shell out some more for the accessories: service plan extension, bluetooth mouse, case, backpack and additional battery and memory (1.5 GB max) are really useful ;-)

My next Sony baby will be a [DCR-SR100]("http://www.camcorderinfo.com/content/Sony-DCR-SR100-Camcorder-Review.htm") camcorder to replace my [JVC Everio GZ-MC200]("http://www.camcorderinfo.com/content/JVC-GZ-MC200-Camcorder-Review.htm") and its dam MOD files [that I can't edit properly]("http://ubuntuforums.org/showthread.php?t=231202") with Ubuntu :cry: 

*Note: if Vaio did not exist, i'd certainly go for a [Dell X1.]("http://reviews.cnet.com/Dell_Latitude_X1/4505-3121_7-31320873.html?tag=sub")*

---

### Post by Jonathan Métillon on 2006-08-12
> **Metacarpal said:**
> Apparently fingerprint recognition is [possible under Linux]("http://www.thinkgeek.com/gadgets/electronic/80be/"), I just wouldn't have a clue how to implement this in Ubuntu.

Don't bother, I don't think the sensor will read anything from your fingers.

(if your avatar really depicts yours).

---

### Post by bluetoad on 2006-08-12
> **Jonathan Métillon said:**
> I can confirm that on Ubuntu 6.06 LTS,
[LIST]
[*]Internal ethernet card and wireless do not work out of the box, but it was easy to setup using ndiswrapper to load [Intel drivers]("http://support.intel.com/support/wireless/wlan/sb/CS-010623.htm") for the PRO/Wireless 3945ABG (w39n51.inf). More info [here.]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")
[/LIST]

This should work.  Do you have the linux-restricted-modules package for your kernel installed?

---

### Post by Jonathan Métillon on 2006-08-17
> **bluetoad said:**
> Do you have the linux-restricted-modules package for your kernel installed?

Yep!

---

### Post by Metacarpal on 2006-08-18
> **Jonathan Métillon said:**
> Don't bother, I don't think the sensor will read anything from your fingers.

(if your avatar really depicts yours).

I had new ones carved in. :mrgreen:

---

### Post by preacherman on 2007-01-02
My fingerprint recognition device isn't on a laptop, but I need help with it on Ubuntu.

I have "The Q" from US Biometrics.  Any news on a driver?

Thanks!

I'm new to Ubuntu, and to this site.  I'm loving it!

---

### Post by Jonathan Métillon on 2007-01-02
> **shamrock_uk said:**
> This appears to have a walkthrough for your fingerprint scanner:

[http://www.qrivy.net/archive/html/linux-biometrics/2005-11/msg00002.html](http://www.qrivy.net/archive/html/linux-biometrics/2005-11/msg00002.html)

It seems to have the same vendor and product ID...

```
 idVendor           0x0483 SGS Thomson Microelectronics
>   idProduct          0x2016
```It looks like he was having an error, but the solution is printed at the very bottom. The WIKI it links to also seems to deal with your *sudo* wish and allow you to use the scanner with non-root applications.

Hope it helps!

Hello again Shamrock,

I had a look at that finally. I patched the bioapi source and installed it. Then tried to install the driver. And I get the exact same error as Marcio is having:

```
Installing TouchChip TFM/ESS Fingerprint BSP ...
Module: MDS Error (Init): 3117
 (Code #3117)!
```And I followed the instructions at the end from Michael, but it's not installing any better.

Any clue, someone?

---

### Post by tower_ on 2007-07-18
I have just got a new HP Compaq 6710b with a fingerprint sensor. The hardware is recognized by Ubuntu, and I found a package to use it. see [http://ubuntuforums.org/showthread.php?p=3080667&highlight=fingerprint+6710b#post3080667](http://ubuntuforums.org/showthread.php?p=3080667&highlight=fingerprint+6710b#post3080667) 

anyway: the vendor is not supporting 
fingerprint scanner drivers for linux.

---

### Post by MadeR on 2007-07-25
Acer Travelmate C204TMi (C200 family).

```
**sudo lsusb -vv**
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0483 SGS Thomson Microelectronics
  idProduct          0x2016 Fingerprint Reader
  bcdDevice            0.01
  iManufacturer           1 STMicroelectronics
  iProduct                2 Biometric Coprocessor
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              20
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by MountainX on 2008-02-18
> **hashimoto said:**
> Does this help at all?: [http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader](http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader)

That's a great link.

I have the built-in fingerprint reader on my ThinkPad working. Now I just need to figure out how to use a USB flash drive with a fingerprint reader on it. Any ideas?

---

