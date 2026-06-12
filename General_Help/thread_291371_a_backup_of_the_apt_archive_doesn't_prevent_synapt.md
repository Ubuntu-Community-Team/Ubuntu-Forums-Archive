---
title: "a backup of the apt archive doesn't prevent synaptic from redownloading the deb files"
date: 2006-11-02
forum: General Help
---

### Post by Isoss on 2006-11-02
I took a backup of the cached apt packages running (tar cvpzf archive.tgz /var/cache/apt/archive) so whenever I wanted to install a system for my uses I would have synaptic install the selected packages fast without the need to re-download these packages, so it would detect the deb files in the cached apt archive and install them. But it actually didn't detect them after extracting the backup using  ( tar xvpfz archive.tgz ) so instead it re-downloaded them as if overwriting the files in the archive! ... any idea why is this happening? 

of course if there is a better way of doing that I'll appreciate it.

---

### Post by Ramses de Norre on 2006-11-02
I guess apt stores a list of downloaded packages somewhere and doesn't run through the archive dir..

```
sudo dpkg -i /var/cache/apt/archives/*
```
will install them all.

---

### Post by dannyboy79 on 2006-11-02
it's because your packages are being told were to look according to your sources.list, you would need to comment out all the websites and make a new location for your computer to look at for where it should retrieve the debs from. for example, you can chose to have apt-get look at cd-rom's or even custom folders which is what you want.  i know if you enter snynaptic, look for a way to add a repo, then add your folder location. don't forget to temp comment out all your other repos in your sources.list before you do a aptitude update && aptitude upgrade

---

### Post by Isoss on 2006-11-02
> **Ramses de Norre said:**
> I guess apt stores a list of downloaded packages somewhere and doesn't run through the archive dir..

```
sudo dpkg -i /var/cache/apt/archives/*
```
will install them all.



Thanks Ramses de Norre, I thought of it, but -correct me i I am wrong- thought maybe that would cause some problems because some packages maybe for the same program but different versions, and as I see when installing packages with synaptic sometimes as you choose some package it would force you to uninstall another package, for example, if you have totem-xine installed and want to install totem-gstreamer it would force you to remove totem-xine, but that wouldn't remove the deb file from the archive!


> **dannyboy79 said:**
> it's because your packages are being told were to look according to your sources.list, you would need to comment out all the websites and make a new location for your computer to look at for where it should retrieve the debs from. for example, you can chose to have apt-get look at cd-rom's or even custom folders which is what you want.  i know if you enter snynaptic, look for a way to add a repo, then add your folder location. don't forget to temp comment out all your other repos in your sources.list before you do a aptitude update && aptitude upgrade

Thanks dannyboy79. That's a good idea! I'll see what I can do.

---

### Post by Ramses de Norre on 2006-11-02
> **Isoss said:**
> Thanks Ramses de Norre, I thought of it, but -correct me i I am wrong- thought maybe that would cause some problems because some packages maybe for the same program but different versions, and as I see when installing packages with synaptic sometimes as you choose some package it would force you to uninstall another package, for example, if you have totem-xine installed and want to install totem-gstreamer it would force you to remove totem-xine, but that wouldn't remove the deb file from the archive!

Hmm, indeed, I don't know how it will react on that neither.

---

