---
title: "Simple backup won't restore. Gutsy Corruption?"
date: 2008-01-16
forum: General Help
---

### Post by wheezer on 2008-01-16
I have never tried to restore a file from my simplebackups. Now I need a single file.

1) So I choose the restore catalog, and select the file.

I press "Restore as" and enter a file name.

Suddenly, a small, totally  BLANK message box appears, as if I am being asked for a confirm. But it's blank, so all I can do is close it.  The fire is never restored.

I just upgraded to Gutsy, Is this yet another problem?

2)  I figure I should reinstall Simple backup, but do NOT want to lose my extensive lists in includes and excludes.   Where does Simple Backup store this date. Can I back it that up so I don't have to restore them all manually?   Will are reinstall preserve them? (Doubtful)

---

### Post by Zill on 2008-01-16
wheezer:
> 2)  I figure I should reinstall Simple backup, but do NOT want to lose my extensive lists in includes and excludes.   Where does Simple Backup store this date. Can I back it that up so I don't have to restore them all manually?   Will are reinstall preserve them? 
/etc/sbackup.conf is the Simple Backup configuration file.  This file can be saved temporarily under a different name and then used to replace the new config file after reinstallation if you wish to retain the same config settings. eg:
```
sudo cp /etc/sbackup.conf /etc/sbackup.conf_temp
```

---

### Post by wheezer on 2008-01-16
> **Zill said:**
> wheezer:

/etc/sbackup.conf is the Simple Backup configuration file.  This file can be saved temporarily under a different name and then used to replace the new config file after reinstallation if you wish to retain the same config settings. eg:
```
sudo cp /etc/sbackup.conf /etc/sbackup.conf_temp
```


Thanks Zill.  So would you just reinstall simple backup?

---

### Post by Zill on 2008-01-17
wheezer:
I use sbackup on Dapper without any problems.  Although sbackup *should* work on Gutsy, I don't know if anyone has had any problems with this.

I suggest reinstalling sbackup and running it with all the default options to see if it works correctly.  If it does you could then try replacing the default sbackup.conf file with your old sbackup.conf_temp file to see if it works OK with your settings.  If it doesn't then it looks like your old config file has some wrong syntax in it!

---

### Post by wheezer on 2008-01-17
I found a post on the net, saying that the blank dialog box was simply supposed to say "Restore in progress" and does not affect the restore itself. 

It just takes a long time for the program to restore the file. But it does work

---

### Post by Zill on 2008-01-17
wheezer:  Yes, sbackup *does* take a long time to restore file(s)!  I hoped that this would be better with later versions, as used in Gutsy, but this doesn't appear to be the case :-(

Anyway, I am glad you got it working :-)

---

### Post by abhiroopb on 2008-05-09
Just had to do a restore of one single doc file. Took about 1-3 minutes (didn't really keep time). It worked really well otherwise. At first I thought maybe my hard drive was slow. Anyway it worked and I guess I don't have to do it very often, but would be good if it could be faster!!

---

### Post by eivind on 2008-05-13
I don't know what backup media you use, but if you use a VFAT/FAT32 formatted external drive, it may be that your file doesn't exist - see

[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/209314](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/209314)

and

[https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719](https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719)

Sbackup can create files larger than 4GB, and won't tell you if a backup failed. I lost data because of this, and normally discourage people from using sbackup *in its current state*: it doesn't tell you if your backup failed. This, of course, is a problem once you try to restore files.

---

