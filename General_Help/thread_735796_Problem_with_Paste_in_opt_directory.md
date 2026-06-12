---
title: "Problem with Paste in /opt directory"
date: 2008-03-26
forum: General Help
---

### Post by MicroBoy on 2008-03-26
**I'm New to ubuntu. When i Try to paste a program to /opt it says like in the photo:**
[IMG]http://img249.imageshack.us/img249/7875/screenshotfk1.png[/IMG]

---

### Post by aysiu on 2008-03-26
Read these two links:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by MicroBoy on 2008-03-26
**Now it's ok I can paste in /opt directory but when i go to the terminal to unzip the firefox it says:**

> edonit@edonit-desktop:~$ sudo tar -C /opt -jxvf firefox-2.0.0.13.tar.gz
tar: firefox-2.0.0.13.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by aysiu on 2008-03-26
Why are you installing Firefox 2.0.0.13 manually?

---

### Post by MicroBoy on 2008-03-26
> **aysiu said:**
> Why are you installing Firefox 2.0.0.13 manually?**How to do that automaticlly?**

---

### Post by dcstar on 2008-03-26
> **MicroBoy said:**
> **How to do that automaticlly?**

Firefox is installed by default in Ubuntu, if the newer version is important it will appear automatically as an update soon.

---

### Post by aysiu on 2008-03-26
> **MicroBoy said:**
> **How to do that automaticlly?**
```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by MicroBoy on 2008-03-26
> **dcstar said:**
> Firefox is installed by default in Ubuntu, if the newer version is important it will appear automatically as an update soon.**It doesn't appear. Meaby because my Ubuntu version is 6.06 LTS and my Firefox Version it's : 1.5.0.13**
> 
edonit@edonit-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by aysiu on 2008-03-26
Don't worry. The Firefox 1.5 in Ubuntu 6.06 is still getting all the security updates until June 2009.

If, for some reason, you still want the latest Firefox, one of these links should help:
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

