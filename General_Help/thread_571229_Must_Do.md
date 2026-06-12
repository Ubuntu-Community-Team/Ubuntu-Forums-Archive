---
title: "Must Do"
date: 2007-10-09
forum: General Help
---

### Post by taffyman on 2007-10-09
HI, as an absolute beginner to Ubuntu, and linux, is there a( must do!) to inhance my enjoyment of this O.S. Many thanks,

---

### Post by Sef on 2007-10-09
What do you want to do that you can't do now?

---

### Post by nick_h on 2007-10-09
I suggest you read the [Ubuntu Starter Guide](http://ubuntuguide.org/wiki/Ubuntu:Feisty).

If you use an LCD monitor try out the improved sub-pixel font rendering.

---

### Post by anaconda on 2007-10-09
Yeah.

First you need to install support for:
-codecs(eg. mp3) 
-flash
- java  
-playing DVDs 
-restricted drivers for your display card (if needed)

and all the programs you want to install.

---

### Post by taffyman on 2007-10-09
many thanks friends for your help,i will try and do most things but my schooldays are far in the past and old age has its companions.

---

### Post by strabes on 2007-10-09
To install all the multimedia stuff that anaconda mentioned, (and assuming you're using feisty) open a terminal (Applications > Accessories > Terminal) and paste in the following commands:```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install w32codecs libdvdcss2 ubuntu-restricted-extras
```

For more information see:
[http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com)
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by taffyman on 2007-11-05
hi there where do i find A TERMINAL, FOR INSTALLING A TARBALL FILE. many thanks taffyman:)

---

### Post by shad0w_walker on 2007-11-05
Applications > Accessories > Terminal

---

