---
title: "Resize cryptswap for encrypted ZFS install"
date: 2022-07-06
forum: General Help
---

### Post by bernhard-gehl-gmail on 2022-07-06
While trying to enable the hibernate option on my laptop, I tried to resize the swap partition to accomodate the 32 GB of RAM. That was, when I realized that the automated ZFS-encryptied-setup option of 22.04 only provided a 2 GB partition for the cryptoswap device. Now - I know what ZFS is and does and I've been using it on my basement server for quite some time - but I have no idea of how to resize cryptoswap without breaking something.

Could someone please help?

snippet from lsblk:
```

zd0              230:0    0   500M  0 disk  
&#9492;&#9472;keystore-rpool 253:0    0   484M  0 crypt /run/keystore/rpool
nvme0n1          259:0    0 931,5G  0 disk  
&#9500;&#9472;nvme0n1p1      259:1    0   512M  0 part  /boot/grub
&#9474;                                           /boot/efi
&#9500;&#9472;nvme0n1p2      259:2    0     2G  0 part  
&#9474; &#9492;&#9472;cryptoswap   253:1    0     2G  0 crypt [SWAP]
&#9500;&#9472;nvme0n1p3      259:3    0     2G  0 part  
&#9492;&#9472;nvme0n1p4      259:4    0   927G  0 part  
```

---

### Post by TheFu on 2022-07-07
If it were me, I'd disable all swap, delete the cryptoswap, then create a new cryptoswap of the size + a tiny bit more and add the new swap to the fstab.  I don't know ZFS on Linux, so hopefully, someone else will chime in.
I'm not a fan of hibernation, but I use sleep/standby mode nightly on my laptop, which is LUKS encrypted.

---

