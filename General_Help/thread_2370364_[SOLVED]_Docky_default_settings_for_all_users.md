---
title: "[SOLVED] Docky default settings for all users"
date: 2017-09-02
forum: General Help
---

### Post by wvoutlaw2k on 2017-09-02
This in reference to [this thread]("https://ubuntuforums.org/showthread.php?t=2224503").

I found the easiest way to make Docky default settings for all users.

First, you set up Docky in the way you want it to look - apps, theme, etc. - for all users.

Second, you open a terminal and execute the following two commands:

**gconftool-2 --dump /apps/docky-2 > docky.xml**

[B]sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load /home/user/docky.xml

[/B](Make sure you substitute **user **with your user name.)

These settings will now be the default Docky settings for all users, and if you re-master Ubuntu, these Docky settings will be the default settings in your Ubuntu re-master.

---

