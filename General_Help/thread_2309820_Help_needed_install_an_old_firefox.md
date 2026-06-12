---
title: "Help needed install an old firefox"
date: 2016-01-13
forum: General Help
---

### Post by nwpll on 2016-01-13
Hi

I have an old machine i want to get back in use i need to use an old Firefox addon to make what i want work. When i click the link for the Firefox it just times out. the links are all below. I put the first line into a terminal but it keeps timing out. I am using 12.04 and the machine details are listed below. If i can't cure the timing out problem any ideas as to how to install Firefox 30?

Thanks

wget [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/30.0/linux-i686/en-US/firefox-30.0.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/30.0/linux-i686/en-US/firefox-30.0.tar.bz2)
 tar -xjvf firefox-30.0.tar.bz2
sudo rm -rf /opt/firefox*
sudo mv firefox /opt/firefox30.0
sudo ln -sf /opt/firefox30.0/firefox /usr/bin/firefox

Dell 
Memory 746.4 mb
Processor intel Celeron CPU 2.53GHz
OS 32 bit
Disk 456.4 gb
Pertition 34gb

---

### Post by Habitual on 2016-01-13
try  
```
wget https://ftp.mozilla.org/pub/firefox/releases/30.0/linux-i686/en-US/firefox-30.0.tar.bz2
```

---

### Post by mörgæs on 2016-01-14
A browser is a security weakness and an old browser is a security breach. 

If your 12.04 version is X/L/Kubuntu it's out of support (Ubuntu is still supported). In that case I recommend a fresh install of 15.10.

---

