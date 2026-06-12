---
title: "USB stick problems"
date: 2013-02-02
forum: General Help
---

### Post by iwoo on 2013-02-02
I can copy files from a USB stick into home, but I cannot copy any of my files onto my USB stick

I get the error message

Error opening file '/media/usb0/Tango Serida Sequence Dance Steps (Full HD).mp4': Permission denied

Iam on Ubuntu 12.04.1 LTS

---

### Post by iwoo on 2013-02-03
I followed this advice and hey presto I can now write to my USB drive again

> **pregiopomo said:**
> I've been having the same problem for a while, and I went for the  solution posted here (modyfing the etc/fstub) then I finally went to  test it with the laptop of a friend that recently installed Ubuntu  10.04, and on his computer everything worked fine.

So I checked out the Synaptic packages he had installed by default, and I  realized that I had some more that probably were creating some  conflicts/problems.

Now it works again!!

Here is what i did:

- start the "synaptic package manager"
- insert "usb" in the quick search
- compare your installed packages with the following list (these are the  one installed by default):
:arrow: 
 usbmuxd
    usbutils
      libusbmuxd1
      libusb-0.1-4
      libusb-1.0-0
      xserver-xorg-video-sisusb
      libmtp8
      usb-creator-gtk
      usb-creator-common
      libmobiledevice0
      libgphoto2-port0
      libgphoto2-2
      media-player-info
      libhpmud0
      hpijs
      hplip
:arrow:
- remove those packages that have been added by you or that may cause  conflicts, in my case I had all the previous ones and I removed the  following that I added months ago messing up with my laptop:

     :arrow: 
usbmount  (yep it sound weird, but now is working properly in my  laptop!)
       pyton usb
       usb creator
       gnome pilot
:arrow:

I hope this example might help some people as I did receive help reading  this forum, this is not "THE WAY" you "HAVE TO" follow to solve this  problem, but this is just a way that worked for me, and I think is worth  to be shared :wink:

---

