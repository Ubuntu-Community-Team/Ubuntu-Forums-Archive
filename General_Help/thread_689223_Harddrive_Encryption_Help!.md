---
title: "Harddrive Encryption Help!"
date: 2008-02-06
forum: General Help
---

### Post by Spydr4590 on 2008-02-06
I recently installed Ubuntu with the Alternate CD and I choose encryption. When booting I get ```
cryptsetup: failed to setup lvm device
``` Which I found only one post referring to this and one in bugs. Supposedly this is fine and nothing is wrong. I would like to know how to verify that my harddrive is indeed encrypted and what encryption it is using? I've searched for thirty mins and couldn't find any information. Any help would be appreciated!

---

### Post by kuja on 2008-02-06
try using "ls /dev/mapper" and see what shows up..... if you see a bunch of things like xxx#_crypt then it should be using encryption.

---

### Post by Spydr4590 on 2008-02-07
I just see control  linux-root  linux-swap_1  sda5_crypt. Not really sure it is is working :)

---

### Post by tact on 2008-02-07
That looks fine... if you need further convincing then install the partition editor "gparted"
```
sudo apt-get install gparted
```

When you run that (system>admin>partition editor) you will see the button on the top right where you can choose different devices...  Choose "sda" for example:
you will see sda1 is ext3 and /boot
you will see sda2 is extended partition
you will see sda5 is unknown.

sda1 (/boot) is not encrypted.  cannot be encrypted. is needed unencrypted so your system can boot.

sda2 is the extended partition that your encrypted volume is created in.  

sda5 is the encrypted volume and because it is encrypted it is "unknown", unintelligible to the partition editor..

If you now change the device to /dev/mapper/sda5_crypt you will see the entire space is "unallocated".   This is because it is encrypted and unintelligible to the partition editor.

If you change device to /dev/mapper/linux-root you will see a fully recognised partition, ext3, where it is mounted, how much space is used and free etc...  because this is being decrypted on the fly by the system to give you an unencrypted view of it.  It is only viewable because you have your system running and gave the right passphrase at startup.

---

### Post by Spydr4590 on 2008-02-07
Thank you tact :) You've been very helpful! Cheers! The drive is encrypted for anyone that was wondering.

---

