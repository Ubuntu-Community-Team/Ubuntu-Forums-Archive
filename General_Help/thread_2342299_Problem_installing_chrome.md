---
title: "Problem installing chrome"
date: 2016-11-05
forum: General Help
---

### Post by Tom_Carr on 2016-11-05
Using ubuntu 16.04
I want to install chrome so I can watch netflix.

I went here and downloaded chrome

[https://www.google.com/intl/en/chrome/browser/desktop/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-IN-ha-bk&utm_medium=ha&utm_term=%2Bchrome](https://www.google.com/intl/en/chrome/browser/desktop/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-IN-ha-bk&utm_medium=ha&utm_term=%2Bchrome)

I clicked on the package it downloaded and it brought up a software center screen for chrome.  I clicked on the install button, it said installing for about3 seconds, then went back to the regular install button.  Nothing was installed.

---

### Post by kevdog on 2016-11-05
Try these commands since you need to install google-chrome using a ppa repository

```

sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list'
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt update
sudo apt install google-chrome-stable

```

These instructions were taken from this site:[http://www.ubuntumaniac.com/2016/04/install-google-chrome-50-on-ubuntu-1604.html](http://www.ubuntumaniac.com/2016/04/install-google-chrome-50-on-ubuntu-1604.html)

---

### Post by Tom_Carr on 2016-11-05
That worked.  Thanks.

---

