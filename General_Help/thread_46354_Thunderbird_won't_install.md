---
title: "Thunderbird won't install"
date: 2005-07-04
forum: General Help
---

### Post by jc3835 on 2005-07-04
Anyone else tried to get thunderbird from synaptic lately?
It's in there, but it spits out an error when I try to install: 

```
 
E: /var/cache/apt/archives/mozilla-thunderbird_1.0.2-1_i386.deb: corrupted filesystem tarfile - corrupted package archive: Success

``` 

Anybody have any ideas?
Thanks.

JC

---

### Post by gibbsnich on 2005-07-04
hi!
Already tried

sudo apt-get autoclean
or 
sudo apt-get clean

?

HTH!

Michael

---

### Post by jc3835 on 2005-07-07
OK, figured it out...
Apparently the package on the CD was bad. I removed the CD from the repository list and loaded Thunderbird from the web thru synaptic and it worked.

JC

---

