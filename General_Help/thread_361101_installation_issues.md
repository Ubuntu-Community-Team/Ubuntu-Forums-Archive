---
title: "installation issues"
date: 2007-02-14
forum: General Help
---

### Post by potti on 2007-02-14
"
E: Package libdvdcss2 has no installation candidate
"

i get this error OVER AND OVER again 

please help me

---

### Post by rsambuca on 2007-02-14
Instructions [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by aysiu on 2007-02-14
Just paste these two commands into the terminal: ```
wget -c http://medibuntu.sos-sts.com/repo/pool/edgy/free/i386/libdvdcss2_1.2.9-2medibuntu2_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_i386.deb
``` **or...** 

Follow [these instructions](http://medibuntu.sos-sts.com/repository.php) and then ```
sudo aptitude update
sudo aptitude install libdvdcss2
```

---

