---
title: "My Downloads Folder is gone"
date: 2020-07-06
forum: General Help
---

### Post by acpt on 2020-07-06
Today, all of a sudden, my downloads folder was gone. I've restarted the system, and my torrent files referring to downloads folder was then also got broken, and the system asked me if I want to change the names of my download folder, I've said no and nothing hs changed. Now there is a referral on naitulus but it goes to nowhere.

I don't know what to do..ç

---

### Post by HermanAB on 2020-07-06
Hmm, make a new folder and install a different torrent client that has different bugs...

---

### Post by acpt on 2020-07-06
It is not just about torrents though, my all downloads folder is gone with everything inside. It wasn't also about the torrent client since the download folder of the client was not the 'downloads' folder of my home directory but on an external HDD. I really doubt that it was about the torrent client.

---

### Post by ajgreeny on 2020-07-06
What does command **locate Downloads** show you as output?

I assume you have looked in the Trash?  Unless you have specifically deleted that Downloads folder it will still be somewhere in your system and That locate com and should find it.
NB. You may need to run command **sudo updatedb**  Before running the locate command.

---

### Post by HermanAB on 2020-07-06
$ find / -name Downloads

---

### Post by ActionParsnip on 2020-07-06
also try:
```

cd $HOME
ls -la

```

Maybe you hid it

---

### Post by TheFu on 2020-07-06
Besides all the ideas above, someone needs to start creating daily backups for anything that would be a hardship to loose.  The fact that you posted here about a missing directory and contents means it needs to be backed up, daily.

---

### Post by ActionParsnip on 2020-07-06
Yes backups. Always always backups

---

### Post by VMC on 2020-07-06
*testdisk* might recover those files. At least give it a try.

---

