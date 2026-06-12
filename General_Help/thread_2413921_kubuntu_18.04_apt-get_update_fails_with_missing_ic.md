---
title: "kubuntu 18.04 apt-get update fails with missing icon @2 files"
date: 2019-03-03
forum: General Help
---

### Post by gobo7 on 2019-03-03
using a local mirror, apt-get update on kubuntu 18.04 fails with the following error:

```

Err:8 file:/mnt/reposB/ubuntu18041/mirror/archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64@2 Icons
  File not found - /mnt/reposB/ubuntu18041/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar (2: No such file or directory)
Get:19 file:/mnt/reposB/ubuntu18041/mirror/archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64@2 Icons [1,024 B]
Ign:19 file:/mnt/reposB/ubuntu18041/mirror/archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64@2 Icons
Reading package lists... Done
E: Failed to fetch file:/mnt/reposB/ubuntu18041/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar  File not found - /mnt/reposB/ubuntu18041/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar (2: No such file or directory)
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

this condition only occurs with kubuntu.  ubuntu desktop and xubuntu complete without issue.
can anyone point me to the corrective measures?

thanks!

ps: should this be posted in a kubuntu forum?

---

### Post by QIII on 2019-03-03
Regarding your post script:

The Ubuntu Forums are for community support for all official flavors.  Since Kubuntu is one, this is the right Forum.

Cheers!

---

### Post by gobo7 on 2019-03-04
the InRelease file for ../dists/bionic has the following:

```

f2a3e3d9c8545708b98d9bea8d54be9d063f658d3f04b9f1da91f0a0b4bea09a           687104 main/dep11/icons-128x128.tar
 4a7db49d7f8bd673262341cc2fc9d261a209047b375a6137966dcef15dd5bd2e           601609 main/dep11/icons-128x128.tar.gz
 5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef             1024 main/dep11/icons-48x48@2.tar
 4fb74242855b6d269bc1b213bf1474c7ace757acbe0d4e0fb114f96e116ca765           314368 main/dep11/icons-64x64.tar
 5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef             1024 main/dep11/icons-64x64@2.tar
 39e0f680c56897c556fd4ce0dbba71e2622b0d1989f2e3fd5ab391d2c7c5c57f           162304 main/dep11/icons-48x48.tar
 72a445c7d354db04d1ffca6f52f7ab66953a3fa889bb66bf6d3210d3ab100f14           118319 main/dep11/icons-48x48.tar.gz
 7989bb311baa38ef545250282aa065d23281c46dfb8faabe4c653487bdbded5c               29 main/dep11/icons-64x64@2.tar.gz
 57f27cd53b92604cbf5c549382eec53d66ef2500fbdd54692688fd3675786aeb           244564 main/dep11/icons-64x64.tar.gz
 5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef             1024 main/dep11/icons-128x128@2.tar
 7989bb311baa38ef545250282aa065d23281c46dfb8faabe4c653487bdbded5c               29 main/dep11/icons-48x48@2.tar.gz
 7989bb311baa38ef545250282aa065d23281c46dfb8faabe4c653487bdbded5c               29 main/dep11/icons-128x128@2.tar.gz

```

the log files for the 64x64@2 file:
```

dep11-log.2:--2019-02-21 07:22:36--  http://archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar.gz
dep11-log.2:File ‘archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar.gz’ not modified on server. Omitting download.
dep11-log.3:--2019-02-13 07:27:19--  http://archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar.gz
dep11-log.3:File ‘archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar.gz’ not modified on server. Omitting download.

```

the directory has:
```

root@t400:/mnt/reposB/ubuntu18041/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/dep11# ls -l
total 3208
-rw-r--r-- 1 root root 678025 Apr 26  2018 Components-amd64.yml.gz
-rw-r--r-- 1 root root 477268 Apr 26  2018 Components-amd64.yml.xz
-rw-r--r-- 1 root root 677314 Apr 26  2018 Components-i386.yml.gz
-rw-r--r-- 1 root root 477188 Apr 26  2018 Components-i386.yml.xz
-rw-r--r-- 1 root root 601609 Apr 26  2018 icons-128x128.tar.gz
-rw-r--r-- 1 root root 118319 Apr 26  2018 icons-48x48.tar.gz
-rw-r--r-- 1 root root 244564 Apr 26  2018 icons-64x64.tar.gz

```

so the 64x64@2 file is in InRelease, the log shows the .gz file was ignored, and yet it is not there.  none of the .tar files are there either.  this should be telling me something, but i don't know enough about apt.

---

