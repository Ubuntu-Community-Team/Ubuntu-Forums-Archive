---
title: "Which is the best GUI software to local backup user folder and files?"
date: 2016-02-29
forum: General Help
---

### Post by WD_SeaSerpent on 2016-02-29
I'm looking for a simple GUI software to do the backup of my data files (not systema files). I'm going to use an external USB drive. I need incremental + continous backup support. What linux software do you use?

---

### Post by newbie-user on 2016-02-29
Rsync is good for that. For GUI, use grsync

---

### Post by WD_SeaSerpent on 2016-03-04
Hi guys, I dint't have any time to try grsync but I'm trying BackInTime downloaded from Muon (software downloader dor Kubuntu). It's great! Based on rsync and very complete -> [http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by kurt18947 on 2016-03-05
I've been using luckybackup from the repositories. It can either synch 2 folders or copy files from one folder to a backup. The only thing to be aware of is that luckbackup seems to want to delete files in the source folder once it copies them to the destination folder. This is easily disabled but it's something to be aware of. It has a 'dry run' mode which should show if any files will be deleted. Grsync & Unison work as well. They're all graphical frontends for rsync.

---

### Post by sammiev on 2016-03-05
+1 for luckybackup from the repositories. 

Been using it for sometime now.

---

### Post by amanchesterman on 2016-03-05
I use ukopp, which allows me to backup chosen folders but also to exclude chosen files within those folders: it's very flexible and suits the way I have my data stored. I found that some of the programs listed above would only backup entire folders. I got it from the software centre.

---

