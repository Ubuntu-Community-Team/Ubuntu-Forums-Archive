---
title: "Mount Galaxy A5 (2017) on Ubuntu via MTP"
date: 2017-06-08
forum: General Help
---

### Post by paque on 2017-06-08
I have been reading numerous articles on this, but nothing seems to  work for me. I have a Galaxy A5 (2017). When I plug it into my Ubuntu  14.04 laptop, the phone is recognised and I can browse the folders and  see files, however I cannot open any of the files, nor can I copy  anything to the phone.

  When I first plug it in, this is the dmesg output:


```
[ 2168.258890] usb 2-1: new high-speed USB device number 9 using xhci_hcd
[ 2168.276856] usb 2-1: New USB device found, idVendor=04e8, idProduct=6860
[ 2168.276860] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2168.276862] usb 2-1: Product: SAMSUNG_Android
[ 2168.276863] usb 2-1: Manufacturer: SAMSUNG
[ 2168.276864] usb 2-1: SerialNumber: d31e7ed99d31e7ed
```
At this point, "SAMSUNG Android" shows up in Nautilus, with nothing in it. The phone then asks me if I want to allow the connection, which I do. Then dmesg displays the following additional output:


```
[ 2190.116385] usb 2-1: USB disconnect, device number 9
[ 2190.417923] usb 2-1: new high-speed USB device number 10 using xhci_hcd
[ 2190.434886] usb 2-1: New USB device found, idVendor=04e8, idProduct=6860
[ 2190.434891] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2190.434894] usb 2-1: Product: SAMSUNG_Android
[ 2190.434897] usb 2-1: Manufacturer: SAMSUNG
[ 2190.434899] usb 2-1: SerialNumber: d31e7ed99d31e7ed
```

Another Nautilus window pops up and the contents of the SAMSUNG  Android device now contain "Phone". When I open that, it displays the  directory structure. Like I said, I can browse through it, but not  actually read the files or copy anything to it.
  The "Use USB for" setting on the phone is set to "Transferring media  files"; "Transfer media files to a PC via an MTP connection.".
  When I change this to "Transferring images"; "Transfer images and  other files via a PTP connection if MTP is not supported.", then I can  open images on the phone, but I am restricted to only directories  containing images.
  The Galaxy A5 (2017) runs Android 6.0.1.
  
Any ideas?


  Thank you.

  
Marc.

---

### Post by gordintoronto on 2017-06-08
I believe your problem will go away if you upgrade to 16.04. It did for me, although I run several distros based on Ubuntu 16.04, not Ubuntu itself.

---

### Post by paque on 2017-06-10
Thanks for your reply. I ran Ubuntu 16.04 from a live USB key and tried to connect my Galaxy, but the results were the same: I can browse but not write in MTP mode. Not sure if any software is missing from the live version...

Marc.

---

### Post by efflandt on 2017-06-10
Ubuntu 12.04 did not support MTP and I never could get it to work properly in that trying everything. But I had no problems accessing my Samsung S3 (Android 4.3) in 14.04. You cannot open MTP files on the phone from Linux, you need to copy them to your computer first.

I currently have a Samsung J7 from Black Friday sale last year (S3 was too old to trade up to S7 no monthly charge) with Android 6.0.1. That works with Nautilus when USB connected, but generates a lot of logs related to phone capabilities in 16.10. So I still tend to use **AndFTP** Android app that I used with 12.04 to **sftp** files to/from my phone connected to LAN WiFi. Note that Android 6.0.1 blocks access between internal storage and microSD, so if you have microSD you need to set up a separate AndFTP connection with the microSD as home directory on the phone. And while Ubuntu installs ssh client by default, it does not install the server. So you would need to install Ubuntu **openssh-server** (which should include **openssh-sftp-server**) or **ssh** meta package that includes everything ssh not already installed. And it may help to have your Linux PC configured with static LAN IP unless it always gets same IP automatically (which also requires setting netmask (typically 255.255.255.0), gateway to your router LAN IP, and nameserver (typically also your router LAN IP). You could use passwords, but I usually specifically disallow passwords for sshd and use keys only (Linux keys will work for AndFTP sftp in Andoroid).

---

### Post by gordintoronto on 2017-06-10
With 16.04 or later, you should not need to use MTP at all.  Just access it with the file manager.

> **paque said:**
> Thanks for your reply. I ran Ubuntu 16.04 from a live USB key and tried to connect my Galaxy, but the results were the same: I can browse but not write in MTP mode. Not sure if any software is missing from the live version...

Marc.

---

### Post by paque on 2017-06-11
Thanks for all the replies. I am starting to think that perhaps my expectation is incorrect.

What I would like to accomplish is to access the storage on the phone (with whichever protocol) and have the ability to read and write to the phone's storage. For example, I would like to:
* copy photos from my phone to my Ubuntu laptop
* copy photos from my laptop to the phone
* do the above with music

As suggested, would I need to do this via an FTP server? Or should it be possible via Nautilus?

Marc.

---

### Post by paque on 2017-06-11
Hi Team,

I have been playing around with it some further. I can indeed copy files to and from the device, just not open them on there. I did some further reading on the MTP protocol and it seems that the limitation lies in the protocol itself.

I am also learning that I cannot use tethering at the same time as MTP, but that is not an Ubuntu issue. I will have a look into setting up an SSH server on the phone that I can connect to via the USB connection. That seems to become another challenge as all the SSH servers seem to use WiFi only.

Thanks for all the help and suggestions!

Marc.

---

### Post by gordintoronto on 2017-06-11
You're making it more complicated than you need to. With 16.04, if MTP and SSH are not in the picture, Nautilus should show the phone as "8 GB volume" or whatever. Click on it, and treat it like a hard drive.

---

