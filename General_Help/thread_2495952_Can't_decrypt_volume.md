---
title: "Can't decrypt volume"
date: 2024-03-09
forum: General Help
---

### Post by john163 on 2024-03-09
I have Ubunto 22.03 on my work laptop for about a year now.  LUKS enabled, working for a long time.  A few boots ago, I had to try a couple of times to get it to take the passphrase, then all was well.  A couple of boots later, it would not take the passphrase until I did a hard reboot.  I just did an update (Software Updater) yesterday, and now... I cannot decrypt at all.  I've hard rebooted, I've run MemTest86+ (passed), and am now booted to a live USB.

```
ubuntu@ubuntu:~$ sudo cryptsetup luksDump /dev/nvme0n1p3
LUKS header information
Version:           2
Epoch:             3
Metadata area:     16384 [bytes]
Keyslots area:     16744448 [bytes]
UUID:              f707aadf-9d1a-417a-81d5-bdd2998d6bd6
Label:             (no label)
Subsystem:         (no subsystem)
Flags:           (no flags)

Data segments:
  0: crypt
    offset: 16777216 [bytes]
    length: (whole device)
    cipher: aes-xts-plain64
    sector: 512 [bytes]

Keyslots:
  0: luks2
    Key:        512 bits
    Priority:   normal
    Cipher:     aes-xts-plain64
    Cipher key: 512 bits
    PBKDF:      argon2id
    Time cost:  10
    Memory:     1048576
    Threads:    4
    Salt:       f6 f7 8f 32 e4 d6 91 5d 92 fe 8e ea cf c6 d6 8e 
                16 e3 a2 4d c1 9e 29 96 3b 0c 09 57 cd f2 17 29 
    AF stripes: 4000
    AF hash:    sha256
    Area offset:32768 [bytes]
    Area length:258048 [bytes]
    Digest ID:  0
Tokens:
Digests:
  0: pbkdf2
    Hash:       sha256
    Iterations: 355690
    Salt:       6c a2 eb 8d 86 9e 6b 21 a3 7a fd e9 fe 2b 5b a4 
                16 cd f2 47 2d a4 aa 8b 3b 0b 92 62 e7 82 44 73 
    Digest:     c9 78 01 e3 86 d5 ea 8c 82 59 d7 32 44 dc af 84 
                e7 e3 e8 30 94 de dd 8b 46 b8 96 f6 e4 3e fe 09
```

I've been searching and experimenting.  Nothing has worked so far.

Oh, and no, I am ***NOT*** mis-typing the passphrase.  I have it written down.

```
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/nvme0n1p3 foo
Enter passphrase for /dev/nvme0n1p3: 
No key available with this passphrase.
```

---

### Post by MAFoElffen on 2024-03-09
Please post the results of this within CODE tags:
```

lsblk -e7 -o name,label,size,fstype,model

```
How was it originally installed? Was it installed with any Volume Manager?

The reason i ask is that, if from the Installer, depending on which options you used to install it, it may be a LUKS locaked hidden volume that contains a hidden partition with a key-file that is used to unlock the main LUKS volume... Where more info is needed to unlock that, to use that file to unlock the other volume. 

An example of this here:
[https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin/blob/main/CHROOT-ZFS-ENCRYPTED--UBUNTU-INSTALLER.md](https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin/blob/main/CHROOT-ZFS-ENCRYPTED--UBUNTU-INSTALLER.md)

---

