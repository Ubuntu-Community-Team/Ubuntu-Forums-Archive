---
title: "upgrading firefox"
date: 2007-03-17
forum: General Help
---

### Post by petunia50 on 2007-03-17
I'm a complete rookie.  I've installed Ubuntu 6.06lts & the updates thereto.
I downloaded the firefox update (firefox-2.0.0.2.tar.gz).  How do I install this update?
Please bear in mind that I am very new to this.  Don't hesitate to dumb it WAY down.
You won't offend me by doing that. Will someone provide me with a step by step procedure?
petunia50

---

### Post by kevinlyfellow on 2007-03-17
try this shell script
[http://pykeylogger.sourceforge.net/installnewfirefox.sh](http://pykeylogger.sourceforge.net/installnewfirefox.sh)
download it to your home folder, open up your terminal and type
```
chmod 777 installnewfirefox.sh
sudo ./installnewfirefox.sh
```

don't delete that shell script, because it will be able to update to the latest version.  To patch firefox, just sudo ./installnewfirefox again

---

### Post by Kateikyoushi on 2007-03-17
I would rather recommend the script on this page, will be easier to install. [LINK]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by kelbizzle on 2007-03-17
uhhhh wth is that?

---

### Post by kevinlyfellow on 2007-03-17
> **Kateikyoushi said:**
> I would rather recommend the script on this page, will be easier to install. [LINK]("http://www.psychocats.net/ubuntu/firefox")

Same script... but better instructions :-)

---

