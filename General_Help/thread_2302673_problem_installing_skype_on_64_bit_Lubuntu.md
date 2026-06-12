---
title: "problem installing skype on 64 bit Lubuntu"
date: 2015-11-12
forum: General Help
---

### Post by rezbd on 2015-11-12
Tried to install skype multiple times on Lubuntu 15.10, 64 bit following the instructions at [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)  After running ```
sudo apt-get install skype 
``` I get the following outputs:  ```
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9.4-3_i386.deb  504   [IP: 91.189.91.13 80]  E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.2d-0ubuntu1_i386.deb  504   [IP: 91.189.91.13 80]  E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcap2/libcap2_2.24-9_i386.deb  504   [IP: 91.189.91.13 80]  E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu8_i386.deb  504   [IP: 91.189.91.13 80]  E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
```

---

### Post by matt_symes on 2015-11-12
Please do not start multiple threads on the same subject. 

It dilutes community effort and creates unnecessary work for the forums staff.

I have jailed your other thread as it's identical to this one.

Please be patient and if someone can help, then they'll post.

---

### Post by Habitual on 2015-11-12
Says "maybe run apt-get update" so I'd maybe try that.

---

### Post by ajgreeny on 2015-11-12
Make sure you have the partner repos enabled in software-sources, run sudo apt-get update, and try again

---

