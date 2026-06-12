---
title: "Recovering ex 8.04 partition, not being recognized by anything"
date: 2012-12-02
forum: General Help
---

### Post by zedx555 on 2012-12-02
Installed ubuntu 12.04 on a computer with ubuntu 8.04 previously on it (kept it as back up if something happens and couldn't bother to download everything for an upgrade). Now grub doesn't recognize the 8.04 partition and I can't mount it as well. How can I recover it? I want to access it and give more space to the 12.04 partition. Pretty sure it was running fine before I removed Arch and installed ubuntu 12.04. Here are the results of some commands :

```


-ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 Dec  2 09:05 be3031a4-30dc-4549-9e65-ee80d98e27aa -> ../../sda3


sudo mount -t ext3 /dev/sda1 /mnt/dist/ 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

When I run dmesg:

```

[11906.608848] Valid eCryptfs headers not found in file header region or xattr region, inode 631001
[11906.608856] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[11911.610442] Valid eCryptfs headers not found in file header region or xattr region, inode 631001
[11911.610457] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[11911.610501] Valid eCryptfs headers not found in file header region or xattr region, inode 631001
[11911.610509] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[11916.611323] Valid eCryptfs headers not found in file header region or xattr region, inode 631001
[11916.611336] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[11916.611381] Valid eCryptfs headers not found in file header region or xattr region, inode 631001
[11916.611388] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO

```

I manually tried to add it to grub by having the following script to /etc/grub.d/ :


```

#!/bin/sh



menuentry "Ubuntuu 8.04" {
    set root=(hd0,0)
    linux /boot/vmlinuz-2.6.24-16-generic  
    initrd /boot/initrd.img-2.6.24-16-generic
}

```



but it doens't add :

```

Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/8_linux: 9: /etc/grub.d/8_linux: menuentry: not found
/etc/grub.d/8_linux: 10: /etc/grub.d/8_linux: Syntax error: "(" unexpected

```

---

