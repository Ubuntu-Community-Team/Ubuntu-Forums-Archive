---
title: "Firefox error message"
date: 2006-07-13
forum: General Help
---

### Post by shickidyshade on 2006-07-13
I'm using firefox and i try to go to edit/prefrences and this is what comes up

XML Parsing Error: syntax error
Location: chrome://browser/content/preferences/preferences.xul
Line Number 1, Column 1:ssed = true;
^](*,) 
what can i do

---

### Post by jordilin on 2006-07-13
I would try to redo your firefox profile, because it can get corrupted. Follow this post [http://www.ubuntuforums.org/showpost.php?p=1247543&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1247543&postcount=9) in which I explained how to do that. Hope it can help you.

---

### Post by shickidyshade on 2006-07-13
what do u mean when you say going to your home

---

### Post by jordilin on 2006-07-13
Going to your home means going to your cd /home/username/ or doing cd ~ or just type cd

---

### Post by jordilin on 2006-07-13
Follow these steps:
cd ~
tar -czvf firefoxbackup.tgz .mozilla/firefox (It does a backup of your firefox profile)
rm -rf ~/.mozilla/firefox/xxxx.default where xxxx are random characters
firefox -ProfileManager and create a new profile

---

### Post by shickidyshade on 2006-07-14
thank you so much ur awesome

---

