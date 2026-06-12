---
title: "Firefox new release"
date: 2017-11-22
forum: General Help
---

### Post by christon74 on 2017-11-22
Good morning fellow Ubunters:D
I am having trouble updating Firefox. I have downloaded it three times (Firefox 57.0) but I don't know which I should choose from "Archive mounter, Ark, GDebi package installer. GDeb does not work and I get a message saying the package might be corrupted.Why is it always so difficult to install the next version of a browser?
OS: Ubuntu 16.04 LTS

---

### Post by deadflowr on 2017-11-22
Just run
```
sudo apt update
sudo apt upgrade
```
unless something is broken with your package manager, firefox will get updated to 57 for you.

---

### Post by speartip on 2017-11-22
It seems that you're searching the web for a package that will be updated for you anyway through the updates channel.
It's not difficult at all to install the next version of a Browser. Just keep your system up to date, and it will be done automatically.

---

### Post by christon74 on 2017-11-22
Hello again to both Deadflowr and Speartip:)
Problem solved! I remember a previous answer from another Ubunter who told me there was something wrong with the repositories, that they probably were broken, hence the problems with updates. I opened a terminal window a few minutes ago and pasted: 
sudo -i software-properties-gtk

And it did the trick. Everything is back to normal now
 and I have just updated Firefox plus a bunch of other packages. 
Thanks again to both of you. Have a nice Wednesday;)

---

