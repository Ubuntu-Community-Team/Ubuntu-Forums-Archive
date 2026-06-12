---
title: "What App is Sync'ing Dropbox?"
date: 2016-09-06
forum: General Help
---

### Post by webmanoffesto on 2016-09-06
Files I add to my Dropbox via cellphone are added to my DropBox folder on my laptop (Ubuntu Gnome). But I don't see what app is doing that on my laptop. According to "Software" in Gnome I have not yet installed the app "Installing this package will download the proprietary dropbox binary from dropbox.com". So what app/system is sync'ing DropBox?

---

### Post by CantankRus on 2016-09-06
What does the terminal command 
```
apt policy dropbox
```
tell you?

I have dropbox installed but I think I downloaded the deb directly from [https://www.dropbox.com/install](https://www.dropbox.com/install)

Ubuntu Software shows "Dropbox" not installed but is really showing nautilus-dropbox is not installed.
[ATTACH=CONFIG]271010[/ATTACH]

Synaptic gives a clearer picture of what's installed...
[ATTACH=CONFIG]271011[/ATTACH]

---

### Post by webmanoffesto on 2016-09-06
dropbox:
  Installed: 2015.10.28
  Candidate: 2015.10.28
  Version table:
 *** 2015.10.28 500
        500 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by CantankRus on 2016-09-06
So dropbox is installed.
Is dropbox running?
```
dropbox status
```

---

