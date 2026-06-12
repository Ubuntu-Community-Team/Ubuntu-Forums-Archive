---
title: "Netflix Install in Ubuntu 14.04 - Silverlight errors"
date: 2014-06-04
forum: General Help
---

### Post by Buschbarber on 2014-06-04
I have searched for answers as to how to run Netflix in Ubuntu. I installed Netflix and I installed Pipelite. Whether I set Firefox or Chrome as the default Browser, the Netflix site loads, however, when I launch a movie, I receive the message that Silverlight is not installed and must be reinstalled.

---

### Post by QIII on 2014-06-04
Hello!

Could you describe how you did the installation?  Did you follow a tutorial?  If so, could you let us know what it is?

---

### Post by Buschbarber on 2014-06-04
I first followed the following directions and when I launched Netflix, the app never loaded.

[http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/](http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/)

I then followed these directions and the Netflix page loads, but I get the Silverlight error when I try to play a movie.

[http://linuxg.net/how-to-install-netflix-desktop-0-8-7-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/](http://linuxg.net/how-to-install-netflix-desktop-0-8-7-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/)

---

### Post by monkeybrain20122 on 2014-06-04
The netflix desktop has long deprecated. The developers have gone on to pipelight. Remove and purge all Netflix desktop packages and install pipelight
[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)
Then enable silverlight (follow the link "enabling plugins" from the above)

For netflix you need [https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/) 
set it to Firefox/Windows

---

### Post by Buschbarber on 2014-06-04
What is the syntax for Purging all Netflix packages?

---

### Post by monkeybrain20122 on 2014-06-04
To remove the package
```

sudo apt-get autoremove --purge netflix-desktop

```

I assume that you installed the netflix-desktop with [https://launchpad.net/~ehoover/+archive/compholio/]("https://launchpad.net/~ehoover/+archive/compholio/?")

Then to remove the repository

```
sudo add-apt-repository --remove ppa:ehoover/compholio
```
Alternatively, in Software & Update, go to Other Software and simply uncheck the box with the ehoover ppa.

Checking the ehoover ppa the netflix-desktop package is uploaded quite recently, so I am wrong that it is deprecated, but you don't need it if you run pipelight anyway, and pipelight is more  efficient in that it just installs the silverlight plugin instead of emulating the whole Windows version of Firefox. It also allows you to install other Windows plugins (unity 3d, flash etc)

---

### Post by Buschbarber on 2014-06-04
Thanks! That worked. I can now run Netflix in Firefox.

---

