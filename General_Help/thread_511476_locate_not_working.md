---
title: "locate not working?"
date: 2007-07-27
forum: General Help
---

### Post by dannyboy79 on 2007-07-27
Hi there, I can't seem to figure out why locate isn't finding some files that I know are there? I have even read the updatedb man pages as well as locate. Even when I do sudo updatedb -u which should create a database of all files within the / it still doesn't find the files? I am simply trying to find ALL files or folders that have ncaa in the title. So I issued
sudo locate -i ncaa
and it returns only this:
 locate -i ncaa
/home/daniel/Desktop/xbmedia_from_xbox/scripts/XSportScores/images/banner-ncaaw.gif
/home/daniel/Desktop/xbmedia_from_xbox/scripts/XSportScores/images/banner-ncaab.gif
/home/daniel/Desktop/xbmedia_from_xbox/scripts/XSportScores/images/banner-ncaaf.gif
BUT I am looking right at a foilder that's called NCAA_blahblah located within /media/500gb/blahblah BUT it's not finding it.

Any tips would be appreciated.

---

### Post by mikewhatever on 2007-07-27
Perhaps because NCAA are all capital letters? How about locate NCAA?

---

### Post by jyba on 2007-07-27
In the updatedb man page it says that it uses the config file /etc/updatedb.conf.

If you look in /etc/updatedb.conf you'll see that /media is one of the paths which are not searched when the database is built...
```
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media"
export PRUNEPATHS
```
If you edit the config file and then rebuild the database then the file you're searching for should show up.

---

### Post by dannyboy79 on 2007-07-28
> **mikewhatever said:**
> Perhaps because NCAA are all capital letters? How about locate NCAA?

thanks but the -i means case doesn't matter.

---

### Post by dannyboy79 on 2007-07-28
> **jyba said:**
> In the updatedb man page it says that it uses the config file /etc/updatedb.conf.

If you look in /etc/updatedb.conf you'll see that /media is one of the paths which are not searched when the database is built...
```
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media"
export PRUNEPATHS
```
If you edit the config file and then rebuild the database then the file you're searching for should show up.

thank you. I did read the man page and I did that it parses that .conf file but didn't think to look in it because I wouldn't think that by default it would NOT include all folders. I'll give that a try. thanks again!

---

