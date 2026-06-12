---
title: "Gutsy: luksaddkey -&gt; &quot;Failed to setup dm-crypt key mapping.&quot;"
date: 2007-11-16
forum: General Help
---

### Post by Master One on 2007-11-16
I was playing around all day, and this is really weird. I can set up an encrypted partition with luks just fine, but I can not add another passphrase or keyfile:```
~$ sudo cryptsetup luksFormat /dev/sda1
WARNING!
========
This will overwrite data on /dev/sda1 irrevocably.
Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase: 
Verify passphrase: 
Command successful.

~$ sudo cryptsetup luksOpen /dev/sda1 sda1_crypt
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.

~$ sudo cryptsetup status sda1_crypt
/dev/mapper/sda1_crypt is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 128 bits
  device:  /dev/sda1
  offset:  1032 sectors
  size:    490222380 sectors
  mode:    read/write

~$ sudo cryptsetup luksDump /dev/sda1
LUKS header information for /dev/sda1

Version:        1
Cipher name:    aes
Cipher mode:    cbc-essiv:sha256
Hash spec:      sha1
Payload offset: 1032
MK bits:        128
MK digest:      6c f9 e1 32 90 ad 63 39 96 23 fa a6 5c ad b9 f8 06 bb c3 44 
MK salt:        29 11 17 10 e0 d0 17 96 63 8e 2f da 8f 80 47 3e 
                ca 5e d8 e1 0f a4 52 2a a1 01 31 d2 2b fd 08 7b 
MK iterations:  10
UUID:           dc89c1f5-e5b2-4742-bbfc-f34b529dd3b4

Key Slot 0: ENABLED
        Iterations:             315146
        Salt:                   9b f4 8c b0 21 fa 23 a6 6f e5 c0 a3 96 9a 41 09 
                                cf 42 1e 9d 34 f2 51 a0 b2 ba 04 64 ab b1 a1 87 
        Key material offset:    8
        AF stripes:             4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED

~$ sudo cryptsetup luksAddKey /dev/sda1
Enter any LUKS passphrase: 
key slot 0 unlocked.
Enter new passphrase for key slot: 
Verify passphrase: 
Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sda1 contains at least 261 sectors.
Failed to write to key storage.
Command failed.

~$ sudo cryptsetup luksAddKey /dev/sda1 /root/data.key
Enter any LUKS passphrase: 
key slot 0 unlocked.
Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sda1 contains at least 261 sectors.
Failed to write to key storage.
Command failed.
```
I checked the luks-FAQ, this has nothing to do with missing modules or dm-crypt not properly installed, becaues creation of the encrypted partition is not the problem, but adding another key or keyfile is.

This is a fresh Edubuntu Gutsy 64bit installation, I didn't do anything except updating after the initial installation, so there has to be something wrong in General.

What am I missing here?

---

### Post by Master One on 2007-11-17
For future reference: My problem was related to ***[this](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/132373) ***bug, and ***[this](http://archive.ubuntu.com/ubuntu/pool/main/c/cryptsetup/cryptsetup_1.0.5-2ubuntu5_amd64.deb)*** new version of cryptsetup fixed the issue.

---

