---
title: "How to install Kmymoney 4.6.3"
date: 2013-08-14
forum: General Help
---

### Post by lumaja2 on 2013-08-14
Ubuntu 12.04 precise I just download Kmymoney 4.6.3.tar.bz2 extract the files. How to install this application Appreciate your help Thank you

---

### Post by PaulW2U on 2013-08-14
You might find the package in Claydoh's PPA easier to install:

[https://launchpad.net/~claydoh/+archive/kmymoney2-kde4?field.series_filter=precise](https://launchpad.net/~claydoh/+archive/kmymoney2-kde4?field.series_filter=precise)

Assuming you already have kmymoney 4.61 installed as you're running Precise, then in a terminal type the following commands:

```
sudo add-apt-repository ppa:claydoh/kmymoney2-kde4
sudo apt-get update
sudo apt-get upgrade

```

As with all software installed from PPAs, install at you're own risk! :)

Edit: I see from [http://ubuntuforums.org/showthread.php?t=2167260](http://ubuntuforums.org/showthread.php?t=2167260) that you already have kmymoney 4.61 installed so the above commands should upgrade your system to kmymoney 4.63.

---

