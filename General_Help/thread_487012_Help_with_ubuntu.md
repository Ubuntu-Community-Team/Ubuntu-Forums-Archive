---
title: "Help with ubuntu"
date: 2007-06-28
forum: General Help
---

### Post by LinuxLovesMJ on 2007-06-28
How do i install warcraft 3 on ubuntu? is it possible

---

### Post by Dread Knight on 2007-06-28
With wine.
[http://appdb.winehq.org/appview.php?versionId=1177](http://appdb.winehq.org/appview.php?versionId=1177)

The steps are like this:
sudo apt-get install wine
install war3, then the tft expansion
apply latest patch or whatever
do the open gl registry stuff 
Then i've used this for 1.21a to bypass the cd requirement bug [http://rapidshare.com/files/32999732/w3battle_121a.rar](http://rapidshare.com/files/32999732/w3battle_121a.rar)

---

### Post by stchman on 2007-06-28
> **Dread Knight said:**
> With wine.
[http://appdb.winehq.org/appview.php?versionId=1177](http://appdb.winehq.org/appview.php?versionId=1177)

The steps are like this:
sudo apt-get install wine
install war3, then the tft expansion
apply latest patch or whatever
do the open gl registry stuff 
Then i've used this for 1.21a to bypass the cd requirement bug [http://rapidshare.com/files/32999732/w3battle_121a.rar](http://rapidshare.com/files/32999732/w3battle_121a.rar)

He will first need to add the proper entries to his software sources.  Follw this procedure while ignoring the IE stuff.

[http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

---

### Post by Dread Knight on 2007-06-29
> **stchman said:**
> He will first need to add the proper entries to his software sources.  Follw this procedure while ignoring the IE stuff.

[http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

Wine is in one of the Ubuntu repositories already, you don't need to add the source manually, just activate the repository. Oh well...

---

### Post by stchman on 2007-06-29
> **Dread Knight said:**
> Wine is in one of the Ubuntu repositories already, you don't need to add the source manually, just activate the repository. Oh well...

I was not aware of that.  I thought WINE was part of budgetdedicated.

Ok

If you go to WINE's site they tell you to install it that way for Ubuntu 7.04.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Just going by what they say.

---

