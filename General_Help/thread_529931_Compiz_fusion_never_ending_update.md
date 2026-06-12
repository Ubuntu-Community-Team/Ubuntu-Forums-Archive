---
title: "Compiz fusion never ending update"
date: 2007-08-19
forum: General Help
---

### Post by Atrio05 on 2007-08-19
Hi. I just installed Compiz Fusion useing this [guide]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") can someone help me as to why the update never completes? 

error below

[ATTACH]41116[/ATTACH]

---

### Post by aldenhg on 2007-08-19
I can't tell you why, but I had the same problem. I ended up switching back to trevino's repos and reinstalling Compiz.

---

### Post by Atrio05 on 2007-08-19
ok. so how will i go about doing that and has that been stable for you ever since?

---

### Post by nimajiman on 2007-08-19
I am having the same never-ending update loop of compiz-core also, after switching to Amaranth's repo. Trouble is Trevinos seems to be down at the moment, so I can't switch back. 

Guess I'll just have to wait and see if it comes back up soon to try and fix it.

---

### Post by aldenhg on 2007-08-19
**NOTE** As someone previously stated, the repos are down at the time this was written. They'll probably be back up soon, but I'd wait a day or so before embarking on this just to make sure. It'd be a shame to remove CF and all that just to find you can't get the working version back


To get Trevino's repos installed and a more working version of CF installed, follow these instructions.
First, edit your /etc/apt/sources.list and add these lines at the bottom:
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
and comment out the lines that you added when you first installed CF. I also recommend labeling all the sources you add so you know what does what when you need to. In case you don't know, commenting something just means that you put a # at the beginning of it's line. 
After that, you'll want to import Trevino's GPG key so you don't have to deal with manually OKing all the updates from here on out:
```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```
Next, remove all traces of CF on your machine. Note that this step will remove all of your CF settings, so back them up first if you don't care to lose them. Put this in a console and watch the lines fly:
```
sudo apt-get --purge remove compiz* libcompizconfig*
```
After all that jazz, you'll want to update your sources, which can be done with 
```
sudo apt-get update
```
Once you're all updated with no errors (if you have errors, just run the command again. If they persist, the repo is down and you'll have to wait until it's up) all that's left to do is install.
```
sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra
```
Restart X and you're good to go.

---

### Post by Atrio05 on 2007-08-20
okay well thank you very much for the help it works perfect now!!

---

### Post by deep-z on 2007-08-22
This can break the system, as it wants to uninstall **ubuntu-desktop**!

---

### Post by deep-z on 2007-08-22
Kinda found solution:
[URL="http://ubuntuforums.org/showthread.php?p=3236000"]
http://ubuntuforums.org/showthread.php?p=3236000[/URL]

Enjoy!

---

### Post by g2g591 on 2007-08-22
> **deep-z said:**
> This can break the system, as it wants to uninstall **ubuntu-desktop**! wrong, ubuntu desktop is just a metapackage depending on the packages the make up the gnome version of ubuntu (like installing kubuntu-desktop will install all the kubuntu packages, but can safely be removed if you don't want all of those packages), as long as it doesn't uninstall any other packages, you're fine.

---

### Post by deep-z on 2007-08-23
> **g2g591 said:**
> wrong, ubuntu desktop is just a metapackage depending on the packages the make up the gnome version of ubuntu (like installing kubuntu-desktop will install all the kubuntu packages, but can safely be removed if you don't want all of those packages), as long as it doesn't uninstall any other packages, you're fine.

Yes, if you install kubuntu-desktop, it will install KDE. So I assume in my case, it would uninstall Gnome, what I don't need/want.

---

