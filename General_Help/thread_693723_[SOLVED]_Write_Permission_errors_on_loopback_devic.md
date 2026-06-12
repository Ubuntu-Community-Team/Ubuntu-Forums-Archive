---
title: "[SOLVED] Write Permission errors on loopback device"
date: 2008-02-11
forum: General Help
---

### Post by jbkerns on 2008-02-11
Playing with loopback devices in Linux (Ubuntu Gutsy 32bit.)  I am making and using a simple loopback volume before playing with AES encryption.
 
```

dd if=/dev/zero of=./vol_none bs=1k count=1024
losetup /dev/loop0 ./vol_none
mkdosfs /dev/loop0 
mkdir ./test_mountpoint
mount /dev/loop0 ./test_mountpoint
echo "This is a text test file" > ./test_mountpoint/SHORT_TEXT.txt

```
I get permission denied.
 
I have tried both dos and ext2 filesystems.  
I have tried permissioning test_mountpoint to 777 before mounting.
 
Afterward, I plan to:
```

umount ./test_mountpoint
losetup -d /dev/loop0
losetup -a 

```

Any help is appreciated. Your examples would be great. Thanks in advance. Being a n00b sucks.

---

### Post by jbkerns on 2008-02-11
Solution: My problem was sudo vs su. This works under su, not sudo. Thanks!

---

