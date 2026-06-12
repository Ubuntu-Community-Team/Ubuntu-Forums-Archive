---
title: "How to install VLC on Ubuntu?"
date: 2013-10-12
forum: General Help
---

### Post by carmen2012 on 2013-10-12
I've used the package manager and have VLC version 2.0.6 installed.  However, a certain feed that I want to watch recommends that I have version 2.10 installed.

I went to the VLC website ( [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) ) and it says the recommended way to install VLC is through the Ubuntu Software Center.  How can I bypass it to get version 2.10 which isn't in there?  Is there a command line command to install it.

Thank you

---

### Post by GWBouge on 2013-10-12
Does the feed still work with 2.0.6?

[Videolan maintains a PPA]("https://launchpad.net/~videolan/+archive/stable-daily") (software source) for Ubuntu 12.04+, their daily stable build is currently 2.1.0.  You can add it to your sources and update VLC with the following 2 commands:

```
sudo add-apt-repository ppa:videolan/stable-daily
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by mastablasta on 2013-10-13
or in a GUI way - you add the repository to software sources in software center and then refresh it and then new version will appear that can be installed.

---

