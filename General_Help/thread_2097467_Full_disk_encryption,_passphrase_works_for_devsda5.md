---
title: "Full disk encryption, passphrase works for /dev/sda5 but not /dev/sda1"
date: 2012-12-23
forum: General Help
---

### Post by latestversion on 2012-12-23
I installed Ubuntu 12.10 and set the option of full disk encryption, and entered a passphrase when prompted. I enter this passphrase on the bootup screen when prompted. I wanted to do some recovery work so I put in a Clonezilla live DVD and did the following:
```

cryptsetup luksOpen /dev/sda1 first
cryptsetup luksOpen /dev/sda5 second
```

I enter the same passphrase when prompted for both above, but it only works for the second, which becomes available at /dev/mapper/second. For the first, it says the password doesn't work. I try entering no password, that also doesn't work. Any idea how I can mount the encrypted /dev/sda1?

I know it is encrypted because when using gparted (not from recovery mode, but from regular mode), it says both /dev/sda1 and /dev/sda5 filesystem type is 'crypt-luks'. When I do 'mount /dev/sda1 /mnt/mountpoint' from recovery mode it says "mount: unknown filesystem type 'crypto_LUKS'".

---

