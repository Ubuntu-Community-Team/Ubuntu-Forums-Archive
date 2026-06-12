---
title: "How do I use the .zip file to install Limewire?"
date: 2006-10-14
forum: General Help
---

### Post by DiscoSamurai on 2006-10-14
I downloaded the .rpm file from limewires homepage, and that one isn't compatable with Ubuntu, so I downloaded the .zip but I have no clue how to use it to install Limewire. Help? I'm huge newbie, so please be as simple as possible and explain everything for me. Thanks.

---

### Post by adwait on 2006-10-15
1)The rpm is not directly compatible with Ubuntu, but you can use alien to convert it to a deb.
```
sudo alien whatever.rpm
```
This will create a .deb file, which you can install using
```
sudo dpkg -i whatever.deb
```

2)You could use frostwire which is available in the repos of Ubuntu which is exactly like limewire and connects to the same network but is much easier to install since it is in the repos and can be installed through Synaptic/Adept.

---

### Post by taurus on 2006-10-15
And make sure you have java (from either Sun or Blackdown) install first before you plan to run LimeWire or FrostWire...

---

### Post by breid on 2006-10-18
I also had probs running Frostwire but following adwait's instructions about downloading Limewire using Alien ............ no probs!!! Thanks adwait.

---

### Post by magog45 on 2006-10-19
Just unzip the file into your home directory, it will create its own Limewire directory there. Then look for a file called runLime.sh and create links as needed. That's all I did and it works fine.

---

