---
title: "[Azureus] change download location during session"
date: 2005-06-12
forum: General Help
---

### Post by DFreeze on 2005-06-12
Hello all,

I've tried to find the answer to this one, but couldn't find it. In the process of getting Azureus to work, I set one of my downloads to write the files to my Ubuntu-disk, but that disk can not hold the whole thing (8+ Gigabytes). 

Now my disk is full (Ubuntu suffering in performance), and the download is somewhere around 80%. I'd hate to start downloading all over again, but I can't get Azureus to change the download location (and move the files to another, bigger disk).

Does anyone know how I can move the files, change the download location to the new folder and still have Azureus recognizing the files and resuming correctly?

thanks in advance!

---

### Post by jeremy on 2005-06-12
I haven't tried this, but it should work:
Close Azureus.
Move the partially downloaded files to new location.
Back up, then edit your ~/.Azureus/downloads.config file to show the new location.
Start Azureus

(note that /.Azureus is a hidden folder.)

---

### Post by Leif on 2005-06-12
What jeremy said should work. Alternatively (and I have done this), stop and remove the torrent, close azureus, move the data to the new location, start azureus, change the path in the settings, and then reopen the .torrent file (it should be stored under .azureus/torrents).

---

### Post by SGC on 2005-06-12
Close Azureus and move the downloaded file to the bigger disk. Open Azureus and go to: 
file > open > torrent file no defualt save

open the same torrent that you used previuosly and when asked for the save location choose the folder where you move your file (in the biggger disk)

Azureus will then take few minutes to check the file and will resume the download.

---

### Post by DFreeze on 2005-06-13
Thanks!

I tried the last suggestion and it worked out perfect!

---

