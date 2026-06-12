---
title: "Problem Updating Gimp"
date: 2007-08-02
forum: General Help
---

### Post by sleepy566 on 2007-08-02
When I try to download the latest updates for Ubuntu, it starts fine but then gives me this error very suddenly:

> E: /var/cache/apt/archives/python2.5_2.5.1-0ubuntu1_amd64.deb: files list file for package `gimp' is missing final newline

and then everything closes because it failed. I have tried replacing the file with a new one found online, but to no avail. Anybody know what's going on?

---

### Post by Theimon on 2007-08-02
Try running the following in a terminal:
```
sudo aptitude autoclean
``` That will clean out the archives. Then run update and upgrade again.

---

### Post by sleepy566 on 2007-08-02
I tried, and I got

> E: /var/cache/apt/archives/python2.5_2.5.1-0ubuntu1_amd64.deb: files list file for package `gimp' is missing final newline

again.

I also tried downloading the updates without gimp or python and I got this instead:

> E: /var/cache/apt/archives/language-pack-de_1%3a7.04+20070601_all.deb: files list file for package `gimp' is missing final newline

---

### Post by Theimon on 2007-08-02
What happens when you uninstall Gimp first and then reinstall the newest version?

---

### Post by sleepy566 on 2007-08-02
It just keeps giving me the same errors, I can't remove it either.

---

### Post by yorkie on 2007-08-02
some info

[http://finkproject.org/faq/faq.en.html](http://finkproject.org/faq/faq.en.html)

look at Q5.19

---

### Post by yorkie on 2007-08-02
Community Announcements & News:

[http://ubuntuforums.org/showthread.php?t=515566](http://ubuntuforums.org/showthread.php?t=515566)
 found this thread I don`t know if this has anything to do with your problem its worth a look

---

### Post by sleepy566 on 2007-08-02
The first link was best, but when I tried to do what it said I got the following:

> sudo apt-get install --download-only python2.5_2.5.1-0ubuntu1_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python2.5_2.5.1-0ubuntu1_amd64.deb


---

### Post by sleepy566 on 2007-08-03
I couldn't fix it, so I switched to Ubuntu 7.10: Gutsy. Everything works great now.

---

