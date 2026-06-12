---
title: "E: Unable to locate package xfce4-whiskermenu-plugin"
date: 2013-12-27
forum: General Help
---

### Post by Buntu Bunny on 2013-12-27
That error occured when trying to download Whiskermenu version 1.2.2-0ppa1~precise1 from gottcode/gcppa. Has the package been moved? Removed? Lost? Done for?

(I'm using Xfce 4.8)

---

### Post by Toz on 2013-12-27
Are you on Precise (12.04)?

Looks like its still there. Did you run "sudo apt-get update" after adding the repository? This worked for me:
```
sudo add-apt-repository ppa:gottcode/gcppa
sudo apt-get update
sudo apt-get install xfce4-whiskermenu-plugin
```

---

### Post by Buntu Bunny on 2013-12-27
> **Toz said:**
> Are you on Precise (12.04)?

Looks like its still there. Did you run "sudo apt-get update" after adding the repository? This worked for me:
```
sudo add-apt-repository ppa:gottcode/gcppa
sudo apt-get update
sudo apt-get install xfce4-whiskermenu-plugin
```

Yes, I'm on Precise 12.04 and yes, I ran exactly the same codes you did. But then I've been having a few issues with installing things, so let me try again.

.............

Okay, I got it this time! This is so puzzling. I had error messages the first time I tried to install Xfce goodies and also Conky Manager. It took two or three tries each. 

Toz, thanks for the reply. It prompted me to try again and this time, success!

---

