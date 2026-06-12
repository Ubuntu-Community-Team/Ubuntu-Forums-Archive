---
title: "Google chrome will not install."
date: 2016-11-25
forum: General Help
---

### Post by Hewjr100 on 2016-11-25
Downloaded 64 bit deb file, click on it.  Software opens up, and when I click on install nothing happens.  Clicked install several times.

Henry

PS Is there another gui package that can install google chrome.

---

### Post by Hewjr100 on 2016-11-25
Never mind, finally got software center to install google chrome.

Henry

---

### Post by howefield on 2016-11-26
Software Centre seems to be a bit flaky these days, GDebi can do it but it doesn't come installed by default so you would need to search for it in the Software Centre and install from there or use the command line..

```
sudo apt install gdebi
```

Then right click on a deb package and select Properties > Open With tab and set gdebi as the default, then any time you double click a deb package it will load with gdebi.

I know you don't care for the terminal but apt can now install local deb packages.. eg, installing Opera browser with the no-install-recommends option to stop it trying to install flash.

```
sudo apt install --no-install-recommends ~/Downloads/opera-developer_43.0.2412.0_amd64.deb
```

---

### Post by Hewjr100 on 2016-11-26
Ok thanks.

Henry

---

