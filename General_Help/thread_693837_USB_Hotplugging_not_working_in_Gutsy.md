---
title: "USB Hotplugging not working in Gutsy"
date: 2008-02-11
forum: General Help
---

### Post by edjski on 2008-02-11
Gutsy will no longer automount USB devices. Namely my external harddrive and iPod. Hotplugging and automount worked well initially but no longer works. I have to reboot with devices plugged in to have them recognized and be mounted.

When I plug in my iPod and try to mount it, i get the following results when I try various things to see what is going on.
lsusb results in a blinking cursor on the next line in the terminal; 
df -h does list anything having to do with the iPod
sudo fdisk -l list only the internal partitions, nothing to do with the iPod or another external disk.

It seems to me that the there is a problem with USB system. 
My laptop has a built in webcam that seems to be giving problems. (when booting I often get lines of text stating something about usb cam not recognized or something.)

Attempts to manually mount iPod or external hard disk result in messages stating that the special device "sdb2" or whatever) does not exist.

Thought? This all worked initially, should I reinstall Gutsy?

thanks

---

### Post by jackocleebrown on 2008-02-11
Hello,

There is a setting to disable/enable automount of usb devices etc in preferences under removable drives and media - check that these settings are set as you want.

The system that does all of the hotplugging is called udev - make sure that you've not accidentally removed this package.

---

### Post by edjski on 2008-02-11
Thanks,

udev is installed. And my settings for Removable Drives and Media are set to mount removable drives when hotplugged, to mount removable media when inserted and to browse removable media when inserted.

Looks like things are set to work, however, they don't.

Whats the next step?

---

### Post by jackocleebrown on 2008-02-11
Hmm, 
Have a look in /var/log/messages and /var/log/kern.log and see if anything is logged here when you insert the usb device - i.e. does the kernel have any idea that you've plugged it in.
Also try booting to a livecd and seeing if hotplugging works, hopefully will rule out a hardware problem.

---

### Post by edjski on 2008-02-11
> **jackocleebrown said:**
> Hmm, 
Have a look in /var/log/messages and /var/log/kern.log and see if anything is logged here when you insert the usb device - i.e. does the kernel have any idea that you've plugged it in.
Also try booting to a livecd and seeing if hotplugging works, hopefully will rule out a hardware problem.

This is what /var/log/messages shows; it just keeps repeating and repeating.

[B]XX camera found.(VC0321) 
Feb 11 17:44:08 acer kernel: [58404.868000] gspca: probe of 5-8:1.0 failed with error -5
Feb 11 17:44:08 acer kernel: [58404.868000] usb 5-8: USB disconnect, address 86
Feb 11 17:44:08 acer kernel: [58405.140000] usb 5-8: new high speed USB device using ehci_hcd and address 87
Feb 11 17:44:08 acer kernel: [58405.296000] usb 5-8: configuration #1 chosen from 1 in choice
Feb 11 17:44:08 acer kernel: [58405.296000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5[/B]

In the lines ending: "...USB disconnect, address 86" and "...ehci_hcd and address 87" increase by one with each repetition.

/var/log/kern/log shows:
[B]Feb 11 17:52:15 acer kernel: [58892.168000] gspca: probe of 5-8:1.0 failed with error -5
Feb 11 17:52:15 acer kernel: [58892.168000] usb 5-8: USB disconnect, address 96
Feb 11 17:52:15 acer kernel: [58892.440000] usb 5-8: new high speed USB device using ehci_hcd and address 97
Feb 11 17:52:15 acer kernel: [58892.596000] usb 5-8: configuration #1 chosen from 1 choice
Feb 11 17:52:15 acer kernel: [58892.596000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Feb 11 17:52:15 acer kernel: [58892.808000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera[/B]
This just keeps on repeating with the address numbers increasing each time.
I can't see anything about the iPod. It looks like whatever is going on with the webcamera is keeping the USB automount from working. 
-When the computer is booting I sometimes see these messages. 
Thoughts?

---

### Post by jackocleebrown on 2008-02-12
Hi,

So that just keeps going over and over without any interaction from you? Sounds like your camera is hanging the USB system. This would explain why your "sudo lsusb" hangs too. I guess if you can fix the camera problem your troubles will go away.
It looks like the kernel driver for your camera is SPCA5XX there is an old wiki topic [here ]("https://help.ubuntu.com/community/Spca5xx#head-48b871e312b6c98ba31970d0545d73b7f2fec9af")that might be helpful to get you started.
Can you remember if your problems started just after a kernel update? (i.e. installing new versions of linux-image-2.6.22.....) That would make some sense - the driver might be broken in the new kernel. If this is the case there will be others with the same problem as you - have a search for people whos webcams have suddenly broken. You also might be able to fix it by compiling the driver from source.

---

### Post by edjski on 2008-02-14
> **jackocleebrown said:**
> Hi,

So that just keeps going over and over without any interaction from you? Sounds like your camera is hanging the USB system. This would explain why your "sudo lsusb" hangs too. I guess if you can fix the camera problem your troubles will go away.
It looks like the kernel driver for your camera is SPCA5XX there is an old wiki topic [here ]("https://help.ubuntu.com/community/Spca5xx#head-48b871e312b6c98ba31970d0545d73b7f2fec9af")that might be helpful to get you started.
Can you remember if your problems started just after a kernel update? (i.e. installing new versions of linux-image-2.6.22.....) That would make some sense - the driver might be broken in the new kernel. If this is the case there will be others with the same problem as you - have a search for people whos webcams have suddenly broken. You also might be able to fix it by compiling the driver from source.


Thanks. It looks like it is in fact the web cam. I have an Acer Aspire 5672 with an orbicam built in. I've seen some other people with similar problems. I'm going to look into it some more.

As far as compiling the driver from source.... can you recommend a good reference? I've been using ubuntu for over a year but haven't compiled anything from source yet. -At least not successfully!

Thanks

---

