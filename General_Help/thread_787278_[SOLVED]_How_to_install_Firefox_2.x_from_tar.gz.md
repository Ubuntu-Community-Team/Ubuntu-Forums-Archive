---
title: "[SOLVED] How to install Firefox 2.x from tar.gz"
date: 2008-05-08
forum: General Help
---

### Post by Tasc0 on 2008-05-08
I've trying to find a way but I can't get it to work. I have Ubuntu 8.04 and   I'd like to get rid of Firefox 3 and use 2.x. The only way I think I can do this is by unistalling Firefox 3, downloading Firefox 2.x and install it from the file in my desktop.

Thanks in advance.

[SIZE="6"][COLOR="Red"]**_Solved:_**[/COLOR][/SIZE]
**Solution can be found in post number [#19]("http://ubuntuforums.org/showpost.php?p=5088004&postcount=19").**

---

### Post by tamoneya on 2008-05-08
```
sudo apt-get install firefox-2
```They left it in the repositories.

---

### Post by Tasc0 on 2008-05-08
> **tamoneya said:**
> ```
sudo apt-get install firefox-2
```They left it in the repositories.
That installs the English version, I'm looking for the Spanish version. I forgot to mention that. Thanks for the reply.

---

### Post by tamoneya on 2008-05-08
cant you just install the english version and then install the spanish locale?
EDIT: if that doesnt work you probably have to install from source (tar.gz)  You can find instructions here: [http://ubuntuforums.org/showthread.php?t=706813](http://ubuntuforums.org/showthread.php?t=706813)

---

### Post by sports fan Matt on 2008-05-08
I also found this: [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

---

### Post by Tasc0 on 2008-05-08
> **tamoneya said:**
> cant you just install the english version and then install the spanish locale?
EDIT: if that doesnt work you probably have to install from source (tar.gz)  You can find instructions here: [http://ubuntuforums.org/showthread.php?t=706813](http://ubuntuforums.org/showthread.php?t=706813)
In that link all I see is "how to install Ubuntu" and the only part of "installing software" it says by doing it with "Add/Remove" or "sudo apt-get..."

Maybe I missed something. And no, I can't install the language package, I don't know why but it says it is not compatible.

---

### Post by Tasc0 on 2008-05-08
> **sox fan Matt said:**
> I also found this: [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)
I have that file, Firefox in Spanish but I only can RUN it from the folder. I'd like to install it on the system.

---

### Post by tamoneya on 2008-05-08
sorry that was meant to be posted in a different thread and it was stuck in my clipboard.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Tasc0 on 2008-05-08
> **tamoneya said:**
> sorry that was meant to be posted in a different thread and it was stuck in my clipboard.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
Still don't find anything useful there. Maybe [this]("http://monkeyblog.org/ubuntu/installing/#source")?

---

### Post by tamoneya on 2008-05-08
it is down all the way at the bottom of the page however your guide will work again.  If you get stuck on yours look at the psychocats page again.

---

### Post by Tasc0 on 2008-05-08
> **tamoneya said:**
> it is down all the way at the bottom of the page however your guide will work again.  If you get stuck on yours look at the psychocats page again.
Ok, I saw it, tried it and didn't work.

---

### Post by tamoneya on 2008-05-08
what error messages did you get.  What commands exactly did you run. Copy and paste the output from terminal (you have to use ctrl-alt-c to copy in terminal)

---

### Post by Tasc0 on 2008-05-09
> **tamoneya said:**
> what error messages did you get.  What commands exactly did you run. Copy and paste the output from terminal (you have to use ctrl-alt-c to copy in terminal)
What I tried was this [http://www.psychocats.net/ubuntu/installingsoftwareold]("http://www.psychocats.net/ubuntu/installingsoftwareold")

The commands I tried were:
```

 ./configure
(ERROR)

sudo make install
(ERROR)

```

I don't post the error messages because they are in Spanish.

---

### Post by aysiu on 2008-05-09
The Firefox .tar.gz files are not usually source files to be compiled. They are precompiled binaries.

Someone earlier mentioned using the Spanish locale. Why not?

These instructions will help you get Firefox 2 installed - just make you also mark *mozilla-firefox-locale-es-es* package for installation in addition to *firefox-2*:
[http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy)

---

### Post by Tasc0 on 2008-05-09
> **aysiu said:**
> The Firefox .tar.gz files are not usually source files to be compiled. They are precompiled binaries.

Someone earlier mentioned using the Spanish locale. Why not?

These instructions will help you get Firefox 2 installed - just make you also mark *mozilla-firefox-locale-es-es* package for installation in addition to *firefox-2*:
[http://www.psychocats.net/ubuntu/firefox2hardy](http://www.psychocats.net/ubuntu/firefox2hardy)

That's the same thing than using this
```
sudo apt-get install firefox-2
```

I can install it, but in English only. I tried also the language package you noted, it's installed but not working.

---

### Post by aysiu on 2008-05-09
That's unfortunate.

Try this, then:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Tasc0 on 2008-05-10
> **aysiu said:**
> That's unfortunate.

Try this, then:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
Still on English. :(

---

### Post by Tasc0 on 2008-05-10
Any help?

---

### Post by Tasc0 on 2008-05-31
I've found a way to install Firefox 2.x in the Spanish version:

1. Uninstall all the Firefoxs. 
2. Delete the following directory:** /home/username/.mozilla/firefox/**.
3. Go to Synaptic and search for **firefox-2** and select it to install it.
4. Now you have the last 2.x version and in Spanish (only if you have Ubuntu in Spanish).

---

### Post by A$h X on 2008-06-05
I've successfully removed FF3 form hardy and replaced it with FF2. it works but with one problem:

When I click a link or button etc from an external program which SHOULD open a link in firefox, nothing happens. eg In deluge you can click a button to test your active port to see if it's open. After getting rid of FF3 it no longer seems to work.

Any ideas?

---

