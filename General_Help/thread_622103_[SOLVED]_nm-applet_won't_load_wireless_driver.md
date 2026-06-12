---
title: "[SOLVED] nm-applet won't load wireless driver"
date: 2007-11-24
forum: General Help
---

### Post by macaholic on 2007-11-24
I just switched from a standard gutsy x86 to a 64 bit one. Some things are giving me problems, on such thing is nm-applet. I installed my driver via ndiswrapper, and did the whole ndiswrapper -m, things, and added  "ndiswrapper" to my /etc/modules file, but nm-applet refuses to acknowledge its existence. (It just shows the ethernet ports) This is getting very annoying since every time I want to connect I have to go into System > Administration > Network, and go into configure and re type my password, then it has to sit there for about 10 seconds reconfiguring it. Any help on this would be great.

---

### Post by gepatino on 2007-11-24
In order to get wireless working in mi MacBoock (64btis) I had to compile the module by hand, otherwise I wouldn't work.

This happens to madwifi cards, and it's solved with the following commands:

```
sudo aptitude install build-essential
wget http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz
tar -zxvf madwifi-trunk-current.tar.gz
cd madwifi<TAB>
make
sudo make install
```

---

### Post by macaholic on 2007-11-24
mad wifi won't work on a Mac Pro. I have wireless, just not through nm-applet.

---

### Post by macaholic on 2007-11-25
Randomly fixed itself after a hardy update.

---

