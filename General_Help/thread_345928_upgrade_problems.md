---
title: "upgrade problems"
date: 2007-01-24
forum: General Help
---

### Post by m.musashi on 2007-01-24
Recently, when I run apt-get upgrade I get a message about beryl and linux-restricted-modules being held back. I did some searching and the solution seemed to be to run dist-upgrade. I tried that and now I get this:
```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  nvidia-glx
The following NEW packages will be installed:
  libberyldecoration0
The following packages will be upgraded:
  beryl linux-restricted-modules-2.6.17-10-generic
2 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 7717kB of archives.
After unpacking 13.8MB disk space will be freed.
Do you want to continue [Y/n]?
```
I suppose this is somehow related to beryl but I'm pretty sure I don't want to remove nvidia-glx. Or should I just run the dist-upgrade and then reinstall nvidia-glx?

Thanks.

---

### Post by Kayne on 2007-01-25
Yeah, I the exactly the same problem, so an answer would be really appreciated! :)

---

### Post by m.musashi on 2007-01-26
> **Kayne said:**
> Yeah, I the exactly the same problem, so an answer would be really appreciated! :)

Yes, I would like to find a solution. I could just run the dist-upgrade and see what happens but I'd rather not break something if it can be avoided. Because beryl and glx seem to be involved in my situation I wonder if [this thread](http://ubuntuforums.org/showthread.php?p=2057713) might be related.

Any help, advice, input would be appreciated.

Thanks.

---

### Post by Kayne on 2007-01-26
> **m.musashi said:**
> Yes, I would like to find a solution. I could just run the dist-upgrade and see what happens but I'd rather not break something if it can be avoided. Because beryl and glx seem to be involved in my situation I wonder if [this thread](http://ubuntuforums.org/showthread.php?p=2057713) might be related.

Any help, advice, input would be appreciated.

Thanks.
Well, I tried and now I don't have a X-Server :D
I didn't try anything about this any further, so now I'm using windows...

---

