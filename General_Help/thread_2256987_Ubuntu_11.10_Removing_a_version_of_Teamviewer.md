---
title: "Ubuntu 11.10: Removing a version of Teamviewer"
date: 2014-12-16
forum: General Help
---

### Post by babakflame on 2014-12-16
Greetings All

  I had installed TeamViewer 10 on my ubuntu 11.10 ( I need to stay on 11.10 for some reasons related to programming). The installed version of TeamViewer (i.e. version 10)  did not work for me that I think appeared due to incompatibility. I decided to uninstall it by directive:

```
sudo apt-get remove teamviewer*


```

Then I downloaded TeamViewer 6 and by installing it via Terminal I got:

```
babak@babak-VPCEA26FG:~$ sudo dpkg -i teamviewer_linux_x64.deb
[sudo] password for babak: 
dpkg: regarding teamviewer_linux_x64.deb containing teamviewer6:
 teamviewer conflicts with teamviewer6
  teamviewer6 (version 6.0.9380) is to be installed.
dpkg: error processing teamviewer_linux_x64.deb (--install):
 conflicting packages - not installing teamviewer6
Errors were encountered while processing:
 teamviewer_linux_x64.deb


```

Would some body PLZ hint me how can I remove the prior version successfully and install TeamViewer 6?

  Best Regards
    Bobi

---

### Post by mörgæs on 2014-12-16
> **babakflame said:**
> I need to stay on 11.10 for some reasons related to programming.

Have you considered to open a thread focusing on these problems in order to get away from 11.10?

---

### Post by babakflame on 2014-12-16
Dear Morgas

  I have some codes installed on my ubuntu 11.10 related to Computational Fluid Mechanics that are recommended with ubuntu 11.10. However, I think maybe it 's time to upgrade my Operating System.
  But what about my problem. I think I did not uninstall teamviewer 10 successfully. Is it possible to hint me on this issue?

  Best,
    Bobi

---

### Post by mörgæs on 2014-12-16
I prefer not to deal with unsupported software.
If you have the space you could install 14.04 in a dual boot to see if you can install your programming environment here. My guess is that it works and that no compatibility is lost.

---

### Post by Bucky Ball on 2014-12-16
As morgaes suggests, it is hard for us to help with a release that has not been supported for over two years. A lot can change in that time. We rarely see anything that old here so very few of us have the expertise to know (or remember) how to offer support for it. The LTS releases are now supported for five years. May suit your purposes better. You may like to have a look at [THIS]("http://ubuntuforums.org/showthread.php?t=2229730") link. 

Hopefully you should be able to upgrade directly to 12.04 LTS (supported until 2017) without a reinstall. [This thread]("https://help.ubuntu.com/community/EOLUpgrades") might help. morgaes' suggestion about installing 14.04 LTS on another partition and migrating to that is a good one, though. That way, you have 11.10 to fall back on if anything goes pear-shaped (although you should always back up your stuff before installing any OS). 

Good luck with it all. ;)

---

### Post by babakflame on 2014-12-18
Greetings All

 Thanks for your replies. I am going to see what can I do.

---

