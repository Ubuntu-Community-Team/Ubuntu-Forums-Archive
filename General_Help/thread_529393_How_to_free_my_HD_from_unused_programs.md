---
title: "How to free my HD from unused programs?"
date: 2007-08-19
forum: General Help
---

### Post by bladexp210 on 2007-08-19
Hello,

I'm using ubuntu 7.04 since May and I'm very happy (run Windows once a month to update avast). But I have a small problem : because I'm still new to linux I was installing and uninstalling lot of software (with Synaptic) to find those who I prefer. Now I have only 6 GB left in my linux partition out of 45 GB, the data take only 12 GB.
I think that the problem is that Synaptic do not delete backups (should I say?) of deleted softwares because I can reinstall them without downloading them a second time. I have tried to delete theme completely with Synaptic options but It dose not work.

Now I think seriously about reinstalling the hole OS a second time, but I don't have that much time and I don't want to keep my bad habits from my past "windows era".

Thanks a lot,

---

### Post by infinitejones on 2007-08-19
All of the .deb packages that apt/aptitude/synaptic downloads are stored in /var/cache/apt/archive. So do this:

```
cd /var/cache/apt/archive
ls
```

to see them all. You can either go through one by one deleting them - you'll need administrator privileges so do this:

```
sudo rm [package name].deb
```

or you could delete them all in one go:

```
sudo rm *.deb
```

This won't affect anything that's already installed, it just means the .deb package will need to be downloaded again if you want to reinstall anything.

---

### Post by bladexp210 on 2007-08-19
Thanks a lot, You really saved me!
Hope I can return the favor to you in the future.

Have a nice weekend

---

### Post by ajgreeny on 2007-08-19
For future reference, you can also do this in **synaptic >Preferences >Files tab >Delete cached package files.**

---

### Post by FuturePilot on 2007-08-19
You can also remove any unused dependencies by ```
sudo apt-get autoremove
```

---

