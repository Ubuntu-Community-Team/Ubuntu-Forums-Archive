---
title: "pmount/usbmount issues in dapper"
date: 2006-07-11
forum: General Help
---

### Post by Henrythewound on 2006-07-11
I have looked and looked through threads on these forums but have not had the level of success I am looking for in auto-mounting a USB key when inserted. In Breezy an icon would appear on my desktop upon insertion of a USB memory stick/key (call it what you want). Now that I have upgraded to Dapper this does not occur. IN order to gain access to my usb key I had to edit my fstab file to include the device. What stinks in my situation is that I have an external USB HD which is seen as /dev/sde1. If it is turned on when I insert the usb key, the key is seen as /dev/sdf1. If I happen to want to insert the key w/o the external HD turned on, the key is seen as sde1 and wont load properly b/c fstab doesn't see the proper drive characteristics.

Is there a way to setup automatic mounting of USB devices? I used to see my ipod and USB keys just fine, now I have to do this folder creation, fstab editing process for each device and make sure they ar eplugged in in the correct order. I appreciate any help as I'm sure there is a fix out there.

Wound

---

### Post by Henrythewound on 2006-07-13
Im guessing nobody knows how to fix this issue just yet. I had the experience last night when my ipod was plugged to charge that my usb key was not recognized due to the expected order of drives plugged in (the ipod was plugged in 1st, and was assigned /dev/sdf status so the usb key plugged in next was assigned /dev/sdg and thus was not read because I had not entered it into my fstab log as such). 

To fix this I needed to unplug the ipod and the USB key and then re-plug in the key 1st in order for it to read. Whats really bad is that I have a memory card reader attached via usb and I will have to enter an fstab entry for each kind of card I may or may not use and then remember which has to be plugged in 1st, 2nd etc.

Someone out there knows how to get pmount running (or whatever program auto-mounts USB devices), please help. It worked fine in Breezy.

Joe aka Wound

---

### Post by givré on 2006-07-13
You should be interested by that
[http://www.ubuntuforums.org/showthread.php?t=168221](http://www.ubuntuforums.org/showthread.php?t=168221)

EDIT: and automount is done initially by gnome-volume-manager.

EDIT2: But i think the better is to put **zero** entry about usb device (even usb-disk) in fstab, and let's do g-v-m. Try it and you will be surprise

---

### Post by Henrythewound on 2006-07-14
Thanks for the info, I was not aware of this method, although I am more interested in the auto "hands off" approach of the Gnome Volume Manager as it used to work in Breezy. Is there away to get this method up and running in Dapper?

thx,
Joe aka Wound

---

### Post by suloku on 2006-07-14
seems the problem is updating from breezy, in my dapper it works perfectly.

The only issue I've found is that no dialog appears on gnome when unmounting the device, but in kde (kubuntu desktop) a dialog appears, but still no progress is shown, but at least i know when I can put off the device.

And talking of that...is there a way to change pmount to EVER use the -s option?

This option is for disabling the cache and "writing when unmounting) of pmount, making system copy the files at the moment, so when it's done extracting the device without unmounting is no a problem.

any solution¿?

---

