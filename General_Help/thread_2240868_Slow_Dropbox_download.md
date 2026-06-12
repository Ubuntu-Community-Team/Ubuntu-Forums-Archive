---
title: "Slow Dropbox download"
date: 2014-08-22
forum: General Help
---

### Post by hamiltonpb on 2014-08-22
I do not know if it is only happening to me, but since the new version of nautilus-dropbox, the downloads are very, very slow. In my laptop with windows, this problem does no happen.
 Anyone has the same problem? (I have 14.04 Ubuntu installed)

---

### Post by fabiomb on 2014-08-23
same problem here, the technical support from dropbox is useless even when i'm a paying customer.

since a few days my notebook (Ubuntu 14.04) stopped syncing, reinstalled a few times, tryed everything, but nothing happens.

dropbox starts with the indexation fine, but when it start to download files the speed is near 0.4kb per second or nothing. 

I have deleted everything, reconfigured, selected only a single folder to sync, and the same situation. I have 2 other computers synced, one with Windows 7 and another with Ubuntu without problem, but the third one stopped working

---

### Post by hamiltonpb on 2014-08-23
I suppose the problem is not with Dropbox, but with nautilus. So, it does not happens either in windows PC or using old versions of nautilus.

---

### Post by adrin5 on 2015-04-09
I experienced the same problems. Watching System monitor on Debian 7 Wheezy I saw an irregular download. 
I used command: "$dropbox status" to observe that it was doing. While I were testing possibles solutions I saw that when I stopped to launch commands or grafical satus... Download became faster, then I launched the command: "$dropbox status" again I saw diferent downloading status appearing (LAN), and it was downloading correctly, but when I launched the same command again "(LAN)" doesn't appear and download became to be slowly (between 0.2Kb/s & 1.7 Kb/s).

Well I tried to disable LAN sync and apparently it's working correctly downloading around 2.5 Mb/s (my high download speed).

I have attached a [picture ]("http://postimg.org/image/i5y0u0la3/")so that you can observe the change
Maybe this can help you. 

**Forgive my English I am improving

---

