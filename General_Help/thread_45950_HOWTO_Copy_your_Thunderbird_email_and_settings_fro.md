---
title: "HOWTO: Copy your Thunderbird email and settings from Windows XP to Ubuntu."
date: 2005-07-02
forum: General Help
---

### Post by davidpronk on 2005-07-02
When moving from Windows XP to Ubuntu I had to move all my Thunderbird email and settings to Ubuntu.

Open Thunderbird on your Ubuntu system and cancel the 'account wizard' and remove any accounts if any exist. Close Thunderbird again. If this is the first time you opened Thunderbird, a 'something'.default folder is now created in /home/username/.mozilla-thunderbird/

Locate the Thunderbird Mail folder on your Windows PC. Mine was in the following path:
C:\Documents and Settings\david pronk\Application Data\Thunderbird\Profiles\skj7gifb.default


Copy the Mail folder all of it's contents and prefs.js from your XP system to /home/username/.mozilla-thunderbird/'something'.default on your Ubuntu system.

The next time you start Thunderbird on your Ubuntu system all the email and settings should available.

---

### Post by ow50 on 2005-07-02
Does it really work just like that? Looking at prefs.js, the file uses absolute pathnames to your mail and news data directories.

If it does work, this thread belongs to "Hoary 5.04 Customization Tips & Tricks" forum.

---

### Post by davidpronk on 2005-07-02
I overlooked the absolute paths in the prefs.js, but I have not experienced any problems sending and receiving email after I copied the file and my email to my Ubuntu machine up till now.

If I come across a problem caused by these paths I will change my HOWTO immediatelly.

---

### Post by dudinatrix on 2005-07-02
Check out this link to share Thunderbird and Firefox on a dual boot Windows XP/Ubuntu installation.

[http://www.plaintivemewling.com/?p=20](http://www.plaintivemewling.com/?p=20)

---

### Post by hz04 on 2007-02-19
I have tried that. But my windows thunderbird folder is not named xxxx.default, instead it is named default.esd.

Does anyone know how to migrate settings from windows to ubuntu with when my folder name is xxxx.esd?

Thanks.

---

