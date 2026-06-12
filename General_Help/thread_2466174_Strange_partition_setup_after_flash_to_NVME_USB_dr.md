---
title: "Strange partition setup after flash to NVME USB drive"
date: 2021-08-21
forum: General Help
---

### Post by xsy77 on 2021-08-21
Hi guys,

Really struggling to find an answer to my issue.

Whenever I try and flash my NVME SSD with an Linux image, the partitions get all kinds of messed up:

Regardless of the image, or the means of writing (etcher / Win32 imager etc.) the above is always the result.

Can anyone shed any light please?

---

### Post by oldfred on 2021-08-21
Please attach screen shots or photos.
Easy to do with Forum's advanced Editor and paperclip icon.

If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

If you are creating a hybrid DVD/flash drive type installer, it does not have standard partitions. It is really a DVD format.
Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Then to have standard partitions, you have to zero out the partition table area.
Reset USB flash that was dd'd to make it usable again, reuse
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) & 
[https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection](https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection)

---

### Post by xsy77 on 2021-08-21
> **oldfred said:**
> Please attach screen shots or photos.
Easy to do with Forum's advanced Editor and paperclip icon.

If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

If you are creating a hybrid DVD/flash drive type installer, it does not have standard partitions. It is really a DVD format.
Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Then to have standard partitions, you have to zero out the partition table area.
Reset USB flash that was dd'd to make it usable again, reuse
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) & 
[https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection](https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection)


Hi,
Thanks for your reply.

I did attach a photo. can you not see it?

Heres another:

---

### Post by tea for one on 2021-08-21
Is the target an NVME SSD in a USB enclosure?

512GB NVME for a live system?

Which Ubuntu image have you used?

---

### Post by xsy77 on 2021-08-21
Hi,

Yes its in an enclosure. Its a portable SSD: Netac Mobile datastar [https://www.netac.com/ydyp-11/333.html](https://www.netac.com/ydyp-11/333.html)

Its for a Raspberry Pi boot drive and have tried various images including Ubuntu Desktop.

---

### Post by tea for one on 2021-08-21
My limited experience of NVME drives in USB enclosures has not been fruitful.
Two enclosures (separate manufacturers) both failed after 3 months with damaged connections.
The cables were OK but the connections and/or the chip inside started to yield odd results (similar to your picture).
A back-up that used to take 4 minutes sometimes never finished.

As for a Raspberry Pi, I can't help as I've never used one.

PS. Try and change the title to include Raspberry Pi

---

### Post by xsy77 on 2021-08-22
Thanks for your reply.

Yes it seems that its the drive itself. However Im sure there is a solution out there somewhere.

The drive is perfectly fine for use as an NTFS storage drive so I dont see what is causing the issue.

I could add Raspberry Pi to the title however it seems irrelevant as the issue isnt with the Pi and more withe the drive trying to write any Linux based image to it.

---

### Post by tea for one on 2021-08-22
Just curious - Will a Raspberry Pi boot from an image written to a NVME drive in a USB enclosure?

---

### Post by yancek on 2021-08-22
The image in your initial post from gparted is cut off on the right so  isn't useful.  The image in post 3 shows you have 2 drives, one of  29.7GB and another of 465.8 GB.  I'm not sure what you are trying to do here.  Are you trying to write an Ubuntu iso to the smaller drive to use to install Ubuntu to the larger drive?  Both drives are dos type drives and you have an Extended partition with one logical partition on each.  If you are trying to use the smaller drive to put the iso on, you should not have an Extended partition on it.  I'm not familiar with either Etcher or win32 Disk Imager but i would not expect them either to have an Extended partition.  Do you not have a standard usb to use, it would make things a lot simpler.

---

