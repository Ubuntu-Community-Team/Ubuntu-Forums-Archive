---
title: "[Solved] Problem Installing MakeHuman From .deb File"
date: 2015-05-19
forum: General Help
---

### Post by jonathantmayer1 on 2015-05-19
This is the log from installing from the .deb file using the Ubuntu Software Center GUI.

```
(Reading database ... (Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 279133 files and directories currently installed.)
Preparing to unpack .../makehuman-1.0.2_all.deb ...
Unpacking makehuman (1:1.0.2) ...
dpkg: error processing archive /home/me/Downloads/makehuman-1.0.2_all.deb (--install):
 trying to overwrite '/usr/share/makehuman/data/bvhs/example1.bvh', which is also in package makehuman-data 1.0.0~alpha6-5ubuntu3
dpkg-deb (subprocess): decompressing archive member: internal bzip2 write error: Broken pipe
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg-deb (subprocess): cannot copy archive member from '/home/me/Downloads/makehuman-1.0.2_all.deb' to decompressor pipe: failed to write (Broken pipe)
Errors were encountered while processing:
 /home/me/Downloads/makehuman-1.0.2_all.deb
```

Edit: Running Ubuntu 14.04

Edit 2: Make sure you delete makehuman-data when removing makehuman.

---

### Post by monkeybrain20122 on 2015-05-19
You have another package called makehuman-1.0.0 alpha6. Remove that first. Also, you can install makehuman 1.0.2 from the getdeb repository

[http://www.getdeb.net/software/makehuman](http://www.getdeb.net/software/makehuman)

Instructions
[http://www.getdeb.net/updates/Ubuntu/15.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/15.04#how_to_install)

---

### Post by jonathantmayer1 on 2015-05-19
That getdeb package says it's for 1.0.2, but it installs 1.0.0 alpha6.

---

### Post by QDR06VV9 on 2015-05-19
Mine shows 1.0.2 Downloaded from there site [http://www.makehuman.org/](http://www.makehuman.org/)
You have to remove all make-human pkgs.
I used gdebi to install not that it matters
Regards

---

### Post by jonathantmayer1 on 2015-05-19
I already did the following...

```
sudo apt-get purge makehuman
```

If that is what you're asking me to do.

---

### Post by QDR06VV9 on 2015-05-19
Yes or even this.
```
sudo apt-get remove makehuman*
```;)

---

### Post by monkeybrain20122 on 2015-05-19
makehuman-data 1.0.0~alpha6-5ubuntu3 is apparently still in your system, you have to remove that too (removing makehuman doesn't remove makehuman-data)

---

### Post by jonathantmayer1 on 2015-05-19
I see, forgot about removing makehuman-data. Thanks!

---

### Post by QDR06VV9 on 2015-05-19
> **monkeybrain20122 said:**
> makehuman-data 1.0.0~alpha6-5ubuntu3 is apparently still in your system, you have to remove that too (removing makehuman doesn't remove makehuman-data)

Skimmed right over that important bit of info.
Good Job monkeybrain20122;)
If you are having troubles finding that it is in /usr/share/makehuman

---

