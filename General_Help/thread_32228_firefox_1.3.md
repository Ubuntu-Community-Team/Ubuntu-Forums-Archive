---
title: "firefox 1.3"
date: 2005-05-06
forum: General Help
---

### Post by sprucio on 2005-05-06
I added universe and mulitiverse to /etc/apt/sources.list. After running apt-get update && apt-get dist-upgrade, I didn't see an entry for firefox 1.3. Is this version included with Hoary?

---

### Post by 23meg on 2005-05-06
no, but it's in the backports repository. Ubuntu does not provide package updates after releases for stability purposes, but many things are backported; check out [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) .

also note that the distro packed 1.0.2 that comes with Hoary has most of the fixes included in the regular 1.0.3 .

---

### Post by angkor on 2005-05-06
not yet, it's still on 1.0.2. You can install 1.03 from 

[http://www.mozilla.org/products/firefox/](http://www.mozilla.org/products/firefox/)

---

### Post by sprucio on 2005-05-06
The reason why I want v1.3 is because I read that there was a security flaw. Has this been patched in v1.2 that shipped with Hoary?

---

### Post by 23meg on 2005-05-06
the 1.0.3 update includes several security fixes, and to the best of my knowledge, only some of these are in Hoary's 1.0.2 . please do a search on the forum for firefox 1.0.3; there are many threads on the subject.

---

### Post by crazybill on 2005-05-06
Get firefox-1.0.3.installer.tar.gz at 
[B]
[http://download.mozilla.org/?product=firefox-1.0.3&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-1.0.3&os=linux&lang=en-US)[/B]

.. or go to [http://www.mozilla.org](http://www.mozilla.org) and follow links.

It is an 8.4 MB file ...... so waiting, waiting..... done.

I saved it to my desktop.

Go to the directory where  you save it.. for me it was.

***# cd /home/myusername/Desktop***

***# gunzip firefox-1.0.3.installer.tar.gz***

(that will change file name to  firefox-1.0.3.installer.tar in the same directory)
[I]
**# tar xvf firefox-1.0.3.installer.tar**[/I]

(that will create a subdirectory called **firefox-installer **. You will see an icon on your desktop.

This is what is in that directory:



```
root@ubuntu1:/home/teacher/Desktop/firefox-installer # ls
config.ini         firefox-installer-bin  install.ini  watermark.png
firefox-installer  header.png             license.txt  xpi
```

firefox-installer is your installation program

---

### Post by jodef on 2005-05-06
[QUOTE=angkor]not yet, it's still on 1.0.2. You can install 1.03 from 

[http://www.mozilla.org/products/firefox/](http://www.mozilla.org/products/firefox/)[/QUOTE]Firefox 1.03 is in the backports for quite a while I have it installed currently enable the backports repository as per the ubuntuguide and install. Easier and less work than mozilla-installer.

---

### Post by sprucio on 2005-05-08
The real reason why I want firefox 1.3 is because I believe that some security updates were released with this new version.

From what I'm reading, Ubuntu does NOT update a version of any app once it's been released as stable. This is absolutely fine but how do I know that my current firefox (1.2) has the updates that have been released with 1.3?

Because I installed Kunbutu only about three days ago my guess is that the firefox package has been patched already with the 1.3 updates.

If v.1.4 is relaesed with new security updates, will I see something regarding the firefox package when I run apt-get update?

---

### Post by crazybill on 2005-05-15
By the way Mozilla firefox now has version 1.0.4, so you will want to udate to that version.

---

