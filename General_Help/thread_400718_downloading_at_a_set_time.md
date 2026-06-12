---
title: "downloading at a set time"
date: 2007-04-03
forum: General Help
---

### Post by Islander85 on 2007-04-03
Hi everybody  I am looking for a downloader to down load big files at like 0200 h,

offpeak adsl rates i am running ubuntu edgy.   

Thanks Islander85  [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by spin2cool on 2007-04-03
One way is to set up a cron job (either by editing your crontab or using gnome-schedule).  Then use wget to pull down the files.

wget -i <list of files to download>

---

### Post by Islander85 on 2007-04-03
Thanks for that just what I was looking for.

Islander85

---

