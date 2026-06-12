---
title: "flash plugin installed but not working :("
date: 2007-12-24
forum: General Help
---

### Post by ELD on 2007-12-24
I have installed flash via the GUI when you go to a site with flash telling you to download, but it still says i need to download it, i go to do it, and it says its installed.

:(

---

### Post by Perpetual on 2007-12-24
It is a known issue with the latest adobe release of the flash plugin.  You can check [here]("https://answers.launchpad.net/ubuntu/+question/19584") for a fix.  It should soon show up in backports as an update also.

---

### Post by DemonDomen on 2007-12-24
First uninstall flash:

Type into terminal:
```
sudo apt-get remove flashplugin-nonfree
```

Then download the rpm from [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")

Go look if you have Alien installed, if not, type
```
sudo apt-get install alien
```

Close firefox and go in the folder with the file (in terminal) and install it:
```
sudo alien -i flash-plugin-9.0.115.0-release.i386.rpm
```

Now it should work.

EDIT: Sorry Perpetual, I wrote my post when you submitted yours.

---

### Post by ELD on 2007-12-24
> **Perpetual said:**
> It is a known issue with the latest adobe release of the flash plugin.  You can check [here]("https://answers.launchpad.net/ubuntu/+question/19584") for a fix.  It should soon show up in backports as an update also.

Thanks a lot, fixed it :)

---

### Post by Perpetual on 2007-12-24
No problem.  Had to go through it myself after doing an install lately.

---

### Post by Perpetual on 2007-12-24
> **DemonDomen said:**
> 
EDIT: Sorry Perpetual, I wrote my post when you submitted yours.

No worries.  That's the good thing about Ubuntu forums, posts get answered fast!

---

### Post by TheNation7 on 2008-02-17
> **Perpetual said:**
> It is a known issue with the latest adobe release of the flash plugin.  You can check [here]("https://answers.launchpad.net/ubuntu/+question/19584") for a fix.  It should soon show up in backports as an update also.

kind of a late response, but finally the fix after about 2 hours of trying to get it to work, thanx man

---

