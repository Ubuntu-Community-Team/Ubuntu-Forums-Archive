---
title: "Need to completely remove wine and utorrent! Please help"
date: 2007-05-27
forum: General Help
---

### Post by olavjunior on 2007-05-27
When I woke up this morning, utorrent wouldn't start! Got some errors when I tried to run it through terminal, didn't mind writing them down thoug. 

I used the wine software uinstaller, and removed utorrent, reinstalled it, but still it wouldn't work. So I decieded to reinstall wine, and then install utorrent again. But now, when I try to add a torrent, utorrent locks up, and the prossess cannot be terminated :S So I have to restart the whole machine, and that's a pain in the ....

I need some help here! Removing wine doesn't completely remove the files wine use, so I manually deleted the .wine folder. I also found some files named utorrent in the .locale shared folder. How do I remove everything, and make a clean install of wine and utorrent again??

And i also wonder how I can get to chose the utorrent to be the default app for opening torrents? Now the old entry is registrered as the default for torrents. I alos have two different utorrent-entrys in alt+f2 (how do I remove them?)

(When I start wine file now, the browser just hangs. I just reinstalled it. Somethings really wrong :S)

---

### Post by drs305 on 2007-05-27
Nevermind this post. I think you already tried what I was suggesting.

---

### Post by yopnono on 2007-05-27
If you delete the.wine folder all you wine settings utorrent files etc are gone, unless it's still running as a process. Try to remove everything and reboot/logout/ or check the ps -e and kill all wine processes.

---

### Post by olavjunior on 2007-05-27
I have uinstalled wine, deleted the .wine, and rebooted, reinstalled wine. But now, when I launch "wine file", and try to browse, the browser hangs up! Wine suddently just isn't working :S And when it runs, I cannot terminate the prosess in the system monitor! It says that the prosess can not be stopped. (why?)

---

### Post by Raptor45 on 2007-05-27
you can try wineprefixcreate, and make sure you set up everything in winecfg again after deleting .wine

---

### Post by olavjunior on 2007-05-28
> **Raptor45 said:**
> you can try wineprefixcreate, and make sure you set up everything in winecfg again after deleting .wine

Could you be  a little more spesific? :)

---

### Post by olavjunior on 2007-05-28
Oh... 
Found my problem. As my problems just got bigger, I realized that it couldn't be wine...
Moved back into windows, and then it hit me (and I'm so embarrassed) that the last time I used xp, I went in standby
As this is the first time I've used xp under Feisty, I wasn't avare of the signs. Under Edgy it wouldn't start if home was locked.

So there it was, the solution! Checkdisk fixed some errors, and now I'm all good :)

---

