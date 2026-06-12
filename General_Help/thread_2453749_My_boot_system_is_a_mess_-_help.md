---
title: "My boot system is a mess - help"
date: 2020-11-16
forum: General Help
---

### Post by nathancatt on 2020-11-16
First off, I'm trying to resurrect my old tower now that I junked my old laptop. It's got some old Ubuntu installs on it from years ago. 

Why can't I boot - possibly because the boot menu tries to mount an encrypted drive - it accepts the password but then enters a recovery prompt which doesn't seem to work very well (giving pdkg, grub and fsck options but unable to use arrow keys to select options). 
Anyway, managed to run boot-repair from a live usb and generate this result:
[http://paste.ubuntu.com/p/tnZPXmcbgw/](http://paste.ubuntu.com/p/tnZPXmcbgw/)
But it's asking me to run a 64 bit version of boot-repair before it can help. This is the code I was using to run the other version:

*sudo apt install software-properties-common; sudo add-apt-repository "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) $(lsb_release -sc) universe"; sudo add-apt-repository -y ppa:yannubuntu/boot-repair; sudo apt-get update; sudo apt-get install -y boot-repair && boot-repair*

But it seems I can't just change instances of boot-repair for boot-repair-disk-64bit. 

Firstly, can I run boot-repair-disk-64bit from live CD and if so how. 

Secondly, is the encrypted drive an issue?

Any advice you have would be really appreciated.

---

### Post by tea for one on 2020-11-16
> **nathancatt said:**
> First off, I'm trying to resurrect my old tower now that I junked my old laptop. It's got some old Ubuntu installs on it from years ago. 

Do you need to recover any personal files or data from the [COLOR="#0000FF"]old tower[/COLOR]?

It appears to me that you haven't used it for years, therefore why worry about booting it at all?

Why not make a USB/DVD with a suitable Ubuntu Family ISO and explore a newer version?

---

### Post by nathancatt on 2020-11-16
Good point.

---

