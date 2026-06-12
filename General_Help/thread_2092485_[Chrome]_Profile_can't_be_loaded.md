---
title: "[Chrome] Profile can't be loaded"
date: 2012-12-08
forum: General Help
---

### Post by dli7319 on 2012-12-08
I know this has been said many times but having tried everything, I'm going to start this thread anyways. This happened without any changes (no installation or removal of related software) 
[ATTACH]228357[/ATTACH]
What I have tried:
Delete .config/google-chrome folder
purge and reinstall chrome
chmod 777 -R google-chrome
chown & chgrp
Nothing seems to work, it simply reappears after i log into chrome
btw, i'm on ubuntu 12.04 lts x64

---

### Post by scouser73 on 2012-12-08
You'll need to delete the Google Chrome profile and start again, before you do this though make sure you backup your bookmarks by clicking on **Settings > Advanced Sync Settings > OK**

Now, go to your Home folder, press **CTRL & H**, which shows the hidden files and then click on **.config** and then delete the entire folder named **google-chrome**.

Then restart Google Chrome, once you've done this a new chrome profile will be created, simply sign into Google Chrome and your bookmarks will appear.

---

