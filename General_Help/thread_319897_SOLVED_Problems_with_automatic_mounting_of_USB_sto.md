---
title: "SOLVED: Problems with automatic mounting of USB storage devices"
date: 2006-12-16
forum: General Help
---

### Post by joe.webster on 2006-12-16
I had been having problems with some of my/family's ubuntu installs with automounting of usb storage.

Specifically with my laptop, everything was working more or less fine with respect to mounting until I upgraded to 6.10. My usb flash drive stopped auto-mounting.

I would see the device in the "my computer" window, but double-clicking on it would give me an error:
> mount: only root can mount /dev/sda1 on /media/sda1

I checked my removable drives and media options and made sure the options to mount and open storage was enabled -- and it was.

I saw messages in dmesg/syslog/messages that it had detected my usb drive and identified the partitions. If I mounted the partition manually, (with mount /dev/sda1 /mnt/usb) all was fine.

I'll spare the log story for now, but basically it had to do with the fact that there WAS an fstab entry for the device. With udev/hald/pmount, you DO NOT want an entry in fstab. The reason, as is my understanding, is that we want to be able to mount devices as non-privileged users in the user-space. Historically we have had to do this in the kernel-space with mount/fstab.

It was annoying for me to find the problem as there are not many/any logs in regards to hald, udev or pmount. Watching syslog/messages/debug didn't show anything relating to these either.

I ultimately tried to round pmount as a non-privileged user. My device is /dev/sda1 and I wanted to mount it to test. I ran
> pmount /dev/sda1 test
and it failed saying:

> Warning: device /dev/sda1 is already handled by /etc/fstab, supplied label is ignored
mount: only root can mount /dev/sda1 on /media/sda1

This is what tipped me off to the fstab. I commented out the line in fstab for /dev/sda1, removed and reinserted my usb drive and it worked.

I'm guessing that along with some other changes that the upgrade made to my fstab, that it added this line. I'm 99% sure I never did -- as auto mount was working fine.

I think at the very least when you double-click on the drive in "computer" that it should let you know that pmount failed, and output pmount's error. Before I make this request, I wanted to see if this was the problem for anyone else? If it was the upgrade that broke this in the first place, then I'll make a request in regards to that, but I think that's a lesser issue.

---

### Post by Tubuntu on 2007-01-10
Thank you joe.webster!! 

I had the same problem and I had tried almost everything...

Your post Fixed the problem!

---

### Post by gjcamann on 2007-01-10
Thnks, i owe you about 3 hours of my life!
:KS

---

### Post by Shay Stephens on 2007-01-10
Just a dumb question.  Do you think the drive got entered into fstab because it was inserted during install of the OS?  Or was there another reaason for it being listed in fstab?

---

### Post by dcstar on 2007-01-11
> **Shay Stephens said:**
> Just a dumb question.  Do you think the drive got entered into fstab because it was inserted during install of the OS?  Or was there another reaason for it being listed in fstab?

It would be difficult - if not impossible - for an install script to determine if a USB drive it detected was either a permanent drive in a system or a removable one.

One can assume that anything detected during the install phase is added to the fstab file.

---

### Post by joe.webster on 2007-01-11
> **dcstar said:**
> It would be difficult - if not impossible - for an install script to determine if a USB drive it detected was either a permanent drive in a system or a removable one.

One can assume that anything detected during the install phase is added to the fstab file.

I tend to agree, however I almost never have my flash drive inserted (as it sticks out in the most annoying way -- thanks sony!) -- so I really doubt that I had it in at the time of the install. Of coarse I don't remember, and I really can't think of any other reason why the update script even thought that device/partition it existed other than the fact that I had the drive in. If the kernel cached something like that, maybe, but I have never heard or seen anything like that.

I noticed that in 6.06 the fstab was NOT using the UUID, and now in 6.10 they ARE using UUID. So in the update, it needed to find the UUIDs of the mounted partitions and update the fstab. I'm sure that's WHAT did it, but as to WHY it picked up on my flash drive (if it wasn't inserted) -- I'm not sure. If it was inserted, then absolutely I agree, it can't know what I use that partition for.

That being the case, I don't know I could even think of how to ask for a fix for this for the future. But, for sure, the messages that pmount outputted should have been displayed when double clicking the drive icon in "Computer" -- that would have sent me right to pmount in 10 seconds flat.

My brother and I were joking about this when we both had the problem saying that "I'm sure it's a stupid setting somewhere or a line that should be commented out".

---

### Post by dannyboy79 on 2007-02-07
> **joe.webster said:**
> I noticed that in 6.06 the fstab was NOT using the UUID, and now in 6.10 they ARE using UUID. So in the update, it needed to find the UUIDs of the mounted partitions and update the fstab. 

you DON't have to have the UUID for your fstab, that's merely one way of doing it I believe. at least that's what man fstab states. anyone correct me if I am wrong here.

---

### Post by joe.webster on 2007-02-07
> **dannyboy79 said:**
> you DON't have to have the UUID for your fstab, that's merely one way of doing it I believe. at least that's what man fstab states. anyone correct me if I am wrong here.

Your are correct, you don't NEED to use the UUID.

However, as part of the conversion it seems that the fine people at debian/ubuntu decided this was the 'new hotness'. If they want me to use UUID, I won't be the one to disagree -- not to mention I think it's better too.

Even if the USB partition was listed in the older non-UUID way, pmount would still refuse to use it.

---

### Post by oasiscity on 2007-02-09
my problem is that I can't find "/dev/sda1" or "/dev/sda2" at all.
thus I am not sure if my device is recognized or not. and there is no way even for manual mounting.

Any clue?

---

### Post by joe.webster on 2007-02-12
> **oasiscity said:**
> my problem is that I can't find "/dev/sda1" or "/dev/sda2" at all.
thus I am not sure if my device is recognized or not. and there is no way even for manual mounting.

Any clue?

The creation of the devices in dev is the job of the kernel and/or hald. Once the device is created, then another process can mount it (mount or pmount for examples).

The lack of a /dev device being created would suggest a lack of a kernel driver (or maybe something wrong with your USB electronics/cable). I would recommend 2 commands to check if you have the driver needed to use your USB device -- lsusb and dmesg. I'm sure there are forum postings with good detail on how to check than I can give you here, so search them out.

---

