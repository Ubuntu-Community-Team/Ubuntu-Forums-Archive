---
title: "MScorefonts installer? On Ubuntu machine!?!?"
date: 2016-12-15
forum: General Help
---

### Post by Rick St. George on 2016-12-15
Anybody know where this is coming from? Getting a pop-up window showing the following info;

> 
Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.


With two buttons, "try again" and "close". There is no title, mfg., brand, or software name other than the mention of Microsoft!
This on an UBUNTU machine!
HHHmmm?!?!?

---

### Post by howefield on 2016-12-15
You have downloaded the package ttf-mscorefonts-installer in order to get Microsoft fonts, if you didn't do it knowingly perhaps it was installed as a dependency of something else.

Try the fix suggested here.. [https://ubuntuforums.org/showthread.php?t=2346459](https://ubuntuforums.org/showthread.php?t=2346459)

---

### Post by Rick St. George on 2016-12-15
Ran the Code;

> 
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer


But nothing happened ???
Or it showed nothing in terminal.

---

### Post by howefield on 2016-12-15
> **Rick St. George said:**
> But nothing happened ???

And hopefully it will stay that way, the idea is to prevent the popup pestering you further.

---

