---
title: "startup issue - serious errors were found while checking the disk"
date: 2014-08-17
forum: General Help
---

### Post by maniac2 on 2014-08-17
I got a fresh ubuntu 14.04 install updates and upgraded. I have a second drive i use for /home that is encrypted with luks/ext4  and because lately i been away from my workstation and not able to personally punch in the passwords im using keys in unencrypted / root partition to unlock my luks /home drive. I know the security implications of doing that but it's not a big issue ill remove the key later. it works and did the job of unlocking the luks drive during startup.

But the problem is after it unlocks my drive and when it mounts it, it spits out the error message

serious errors were found while checking the disk... Press i to ignore press s to skip press m for manual recovery

I hit m, and did mount /home it mounts with no problem. So the luks drive is already decrypted. I even did a fsck.ext4 on the /dev/mapper/home and its clean. I'm confused why it does this every reboot. I don't think there is a problem at all with my drive

So i wanted to see if i can duplicate the problem so i copied all my data to a 2nd drive all same setup encrypted with luks unlocks with keyfile etc and i get the same error. 

Is there a way i can get my system to automatically ignore or bypass whatever that's causing the startup to stall during disk checks when my drives seem fine? 

I even tried editing /etc/default/rc0 and changing FSCKFIX=YES and that didn't work. 

I checked for badblocks and there is 0/0

My last option would probably be to create a script to not mount my luks /home drive during startup and mount it after the system is fully started.

I did this all the time with 12.04 and had no issues

I'm out of ideas looking for some advice. Please help thanks

---

### Post by tgalati4 on 2014-08-17
You have probably spent some time working on this.  I would look into changes in the luks/ext4 encryption framework from 12.04 to 14.04.  It's been 2 years and frameworks change.  It's possible there is some encryption metadata that is not compatible between versions.  I would not expect an encrypted, external drive formatted in 12.04 to automatically mount in 14.04.  I would expect breakage--as you have experienced.

Because you tried a second disk with a fresh encryption, I would presume using keys from a non-encrypted partition to unlock your drive is a Use Case that luks/ext4 does not support.  It's possible that the framework closed that Use Case as a security measure.

So you don't have many options other than manually logging in or only encrypt certain directories on /home so you can mount it during boot, but unlock manually when you really need to access the data.  Encrypting /home seems like a good idea on paper, but many, many apps need to read configuration files in /home so your system won't behave properly until /home is opened up.

---

### Post by bfg100k on 2014-12-29
hi, i recently setup a new Ubuntu 14.04 box with two dmcrypt/luks encrypted data (i.e. non-system) partitions unlocked via keyfiles stored in /root. Like you, I'm facing the same issue with auto mounting the partitions on boot. Please do let me know if you or anyone else have found a solution to this. Thanks!

---

### Post by maniac2 on 2014-12-31
i created a script that loads through rc.local that basically decrypts both drives using key files located on a usb stick then fsck.ext4 the mapped drives in case they need to be checked, then mount them. works for me.

---

### Post by maniac2 on 2014-12-31
Im stuck using 12.04 lts because the lack of ati video card support for older cards in 14.04 btw. I'm using a 1u rack as a workstation and can only use low profile half weight pci-e

---

