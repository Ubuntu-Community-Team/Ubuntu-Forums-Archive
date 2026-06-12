---
title: "apt update reporting hash sum mismatch when downloading bionic-updates i386"
date: 2022-09-08
forum: General Help
---

### Post by ghstridr2 on 2022-09-08
[solved]
I'm not using anything out of that repo, but I thought it was worth reporting and a search didn't show any mention of it.
This seems to have been happening for a few days now.
```
Err:15 http://archive.ubuntu.com/ubuntu bionic-updates i386 Contents (deb)
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:2183679437 [weak]
   - SHA256:e6f95b4ac0a7da589601e00ade2242ff55e6d6ab95acfa7e3b1d578e627d8ee3
   - SHA1:be72b2868739f7f6de76a119bdd6fb789c801715 [weak]
   - MD5Sum:b9ee13a24d504c9e97d4aeb460a1a597 [weak]
  Hashes of received file:
   - SHA256:0f51b1fd8d31e8511fdb8de526ea3dccbf106dbd3c3608e2e32533d05eb62bc9
   - SHA1:5b87aa3afef250b4c280a4e7f0284706668fb811 [weak]
   - MD5Sum:6e497685ba0cf61b71ee17db62510ac6 [weak]
   - Filesize:192285196 [weak]
  Release file created at: Thu, 08 Sep 2022 18:34:34 +0000
Err:16 http://archive.ubuntu.com/ubuntu bionic-updates amd64 Contents (deb)


Fetched 254 kB in 8s (30.0 kB/s)
Reading package lists... Done
E: Failed to fetch store:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_bionic-updates_Contents-i386.gz  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:2183679437 [weak]
    - SHA256:e6f95b4ac0a7da589601e00ade2242ff55e6d6ab95acfa7e3b1d578e627d8ee3
    - SHA1:be72b2868739f7f6de76a119bdd6fb789c801715 [weak]
    - MD5Sum:b9ee13a24d504c9e97d4aeb460a1a597 [weak]
   Hashes of received file:
    - SHA256:0f51b1fd8d31e8511fdb8de526ea3dccbf106dbd3c3608e2e32533d05eb62bc9
    - SHA1:5b87aa3afef250b4c280a4e7f0284706668fb811 [weak]
    - MD5Sum:6e497685ba0cf61b71ee17db62510ac6 [weak]
    - Filesize:192285196 [weak]
   Release file created at: Thu, 08 Sep 2022 18:34:34 +0000
E: Failed to fetch store:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_bionic-updates_Contents-amd64.gz
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by #&amp;thj^% on 2022-09-08
Please have a good back-up in place, 
```

sudo rm -r /var/lib/apt/lists/partial/*  
sudo rm -r /var/lib/apt/lists/*
```
Now run your update and upgrade commands.

---

### Post by ghstridr2 on 2022-09-08
Tarball for the backup.
Looks like that worked.
Thanks!

---

### Post by #&amp;thj^% on 2022-09-08
Good Job on the back-up. ;)
Enjoy

---

