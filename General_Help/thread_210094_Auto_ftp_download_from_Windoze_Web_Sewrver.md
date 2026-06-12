---
title: "Auto ftp download from Windoze Web Sewrver"
date: 2006-07-06
forum: General Help
---

### Post by hairshirt on 2006-07-06
Hi all,

is there a way I can automatically download via ftp a set of *.zip files created by a backup program running on the said (title) server?

I would like to set this up and have it downloaded whilst I sleep.

I've had a look around this forum but have been unable to find any real tips on how this could be done.

Many thanks in advance of help help, Mark.

---

### Post by lamego on 2006-07-06
First make sure you have the universe/multiverse repositories enabled. Install ncftp (a command line ftp client):
```
sudo apt-get install ncftp
```
It will provide you an ncftpget which you can use to get the files over ftp, for more information type "man ncftpget" .

---

