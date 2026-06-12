---
title: "ttf-mscorefonts-installer error: Failure to download extra data files"
date: 2017-01-30
forum: General Help
---

### Post by David4321 on 2017-01-30
I'm not sure what is causing this, or even really how it got installed, probably as a dependency of something I installed recently. This error pops up daily now. I run the advised action, and terminal opens, then closes after operation, but something is not resolved. I've tried uninstalling and reinstalling ttf-mscorefonts-installer with both gdebi and synaptic, no joy.

[ATTACH=CONFIG]273451[/ATTACH]

---

### Post by Bashing-om on 2017-01-30
David4321; Hey ;


I am aware of this;
[https://ubuntuforums.org/showthread.php?t=2346763](https://ubuntuforums.org/showthread.php?t=2346763)
Maybe will work for you .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by howefield on 2017-01-31
If what Bashing-om said doesn't work you could purge the package and install a newer version of it.

```
sudo apt purge ttf-mscorefonts-installer
```

to purge the existing failed package

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

to download the new package to your Downloads folder, and
 
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

to install it.

---

### Post by Autodave on 2017-01-31
Do what howefield says: works every time. :-)

---

