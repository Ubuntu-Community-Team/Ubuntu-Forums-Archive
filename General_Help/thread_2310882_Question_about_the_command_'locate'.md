---
title: "Question about the command 'locate'"
date: 2016-01-22
forum: General Help
---

### Post by GrouchyGaijin on 2016-01-22
Hi Guys,

I had cloned a directory from github and installed a program to sync Ubuntu with OneDrive.
It didn't work out so well and I removed the program.

My question is why when I run: ```
locate onedrive
``` in the terminal, do I see this:

```

Today is Fri Jan 22 @ 22:55:37 ~ $ locate onedrive
/home/john/onedrive-master
/home/john/.config/onedrive

```

Yet if I try to cd to onedrive-master (or actually open the file manager and look for the directory) there is no directory called onedrive-master. (Which makes sense because I deleted it)
The same thing happens with the directory that was at ```
/home/john/.config/onedrive
```.  I deleted it, yet when I run ```
locate
``` it still appears in the list.

Put another way, why do files and directories that I have deleted still appear in the list of matching files and directories when I run the locate command?

---

### Post by steeldriver on 2016-01-22
The locate command uses a database that is updated (at least, by default) only once per day. You can run

```

sudo updatedb

```

to refresh the database

---

### Post by GrouchyGaijin on 2016-01-22
Thank you!

---

