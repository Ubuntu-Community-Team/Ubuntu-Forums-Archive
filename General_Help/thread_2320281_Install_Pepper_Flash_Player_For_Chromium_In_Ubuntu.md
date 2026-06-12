---
title: "Install Pepper Flash Player For Chromium In Ubuntu Via PPA"
date: 2016-04-12
forum: General Help
---

### Post by daniell59 on 2016-04-12
[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

I would appreciate assistance. 

The last part is giving me trouble. I don't know how to use the text editor to put the command in.

Thanks in advance

---

### Post by slickymaster on 2016-04-12
Since you already add the PPA to your system, all you have to now is to open **/etc/chromium-browser/default** file in a text editor and add the following line to the end of the file:```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```Restart Chromium, and load the chrome://plugins page to verify that the plugin is active.

---

### Post by daniell59 on 2016-04-12
> **slickymaster said:**
> Since you already add the PPA to your system, all you have to now is to open **/etc/chromium-browser/default** file in a text editor and add the following line to the end of the file:```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```Restart Chromium, and load the chrome://plugins page to verify that the plugin is active.

I opened the text editor. I am ashamed to say that I don't how to find Chromium.

---

### Post by slickymaster on 2016-04-12
What text editor do you have installed? Also, please post back the output you get from running the following in a terminal window```
apt-cache policy gksu
```

---

### Post by daniell59 on 2016-04-12
daniel@daniel-N68SA-M2S:~$ apt-cache policy gksu
gksu:
  Installed: 2.0.2-6ubuntu2
  Candidate: 2.0.2-6ubuntu2
  Version table:
 *** 2.0.2-6ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status
daniel@daniel-N68SA-M2S:~$ 

I was trying to us Getit

---

### Post by slickymaster on 2016-04-12
OK, so here's what you'll do.
Open up a terminal window and run```
gksu gedit /etc/chromium-browser/default
```It will prompt you for your password, enter it and then you'll have the **/etc/chromium-browser/default** file opened in Gedit. Scroll down to the bottom and copy/past the following into it```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```Save and close Gedit and then just restart Chromium, load the **chrome://plugins** page to verify that the plugin is active. (Note that if you see a Flash plugin with a version of 11.2 or lower, then that is an old, non-PPAPI version of Flash. A current version of Pepper Flash will be 11.7 or higher.)

---

### Post by deadflowr on 2016-04-12
For what it is worth: you can put the whole thing in a terinal to open the file directly in the text editor, like so:
```
gksu gedit /etc/chromium-browser/default
```

But having said that, ditch the ppa.

You can install pepperflash without it.
Simply open the program called Software and Updates,
go to the section marked Other Software
 Enable (check) the Canonical Partners.
Close Software and Updates.
And if it ask to reload, let it.
(If it does not ash to reload, run:
```
sudo apt-get update
```

after it reloads, now all you need to do is add the package: adobe-flashplugin
once install, you have pepperflash, up-to-date.
Easy peasy.

Hope it helps.

---

### Post by daniell59 on 2016-04-12
Thanks, it worked.

---

### Post by O)9(yo&amp;# on 2016-04-12
Will this also work for Opera?

---

### Post by howefield on 2016-04-12
> **michael_diemer said:**
> Will this also work for Opera?

The above may well work, but certainly enabling the partners repository and installing adobe-flashplugin will do it for opera.

---

