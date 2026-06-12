---
title: "[SOLVED] K3b"
date: 2008-02-03
forum: General Help
---

### Post by bij33 on 2008-02-03
Hi all,

K3B issues an error and does not accept a mp3 file as an input when I try to burn an audio CD. See the attached image. I use version 7.10 and the latest updates.

I appreciate any help...

---

### Post by xc3RnbFO8P on 2008-02-03
In Synaptic Package Manager install:

libmad0
libmad0-dev
python-pymad

Check if you got intalled (In Synaptic Package Manager):

libk3b2-extracodecs

---

### Post by y-lee on 2008-02-03
I had the same problem once, the code below fixed it.

```
sudo apt-get install arts
artsd &
sudo apt-get install libk3b2-mp3
```

[URL="http://tipotheday.com/2008/01/22/quick-tip-k3b-on-ubuntu-with-gnome/"]
see this link[/URL]

---

### Post by bij33 on 2008-02-03
[SOLVED] Thanks guys for the help,

"sudo apt-get install libk3b2-mp3" took care of the problem...

---

### Post by hyperair on 2008-02-03
Click on Thread Tools->Mark as Solved.

---

