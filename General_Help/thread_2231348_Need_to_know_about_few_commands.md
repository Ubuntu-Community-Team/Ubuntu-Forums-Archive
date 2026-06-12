---
title: "Need to know about few commands"
date: 2014-06-25
forum: General Help
---

### Post by adnansanni on 2014-06-25
Guys,
Are "mkfs.ext4" and "mkfs -t ext4" same?
I'm using 64bit ubuntu 14.04 LTS. To run "Packet Tracer" (Cisco) software, I have to run:
```

#sudo dpkg --add-architecture i386
#sudo apt-get install libnss3-1d:i386 libqt4-qt3support:i386 libssl1.0.0:i386 libqtwebkit4:i386 libqt4-scripttools:i386

```

I'm littile bit confused about what actually does with "add-architecture i386"?

---

### Post by HermanAB on 2014-06-25
Yup, it is the same.  There are various 'shortcut' commands, such as mkfs.ext4, mkfs.ntfs etc.  Details are in the man page.  This is one of those commands where I *always* have to read the darn man page.

---

