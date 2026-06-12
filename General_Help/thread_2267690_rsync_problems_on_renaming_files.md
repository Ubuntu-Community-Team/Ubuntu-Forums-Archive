---
title: "rsync problems on renaming files"
date: 2015-03-03
forum: General Help
---

### Post by nerdtron on 2015-03-03
Hi All

I'm running this rsync command on my nightly backup script:

```
rsync -avvrhu --log-file=$LOGS  --delete --partial /root/backup/Quickbooks/ /mnt/QBBackup/QBBackup-$DATE/ > /dev/null
```

It works on most nights, but sometimes I get the following error that rsync can't rename the file. 

[COLOR=#000000][FONT=Courier New]```
2015/03/03 00:18:18 [22084] rsync: rename "/mnt/QBBackup/QBBackup-2015-03-02/Quickbook2013/PBL/.PBL.QBW.ND.mKDgLs" -> "Quickbook2013/PBL/PBL.QBW.ND": File exists (17)
```[/FONT][/COLOR]

It doesn't happen on all files though so I don't know how I get that error. See below other files transfer fine.


```
[COLOR=#000000][FONT=Courier New][COLOR=#000000][FONT=Courier New]2015/03/03 00:18:19 [22084] >f+++++++++ Quickbook2013/PBL/Restored_PBL_Files/Spell_Checker/UserDictionary.tlx 
2015/03/03 00:18:19 [22084] cd+++++++++ Quickbook2013/Properties/ 
2015/03/03 00:18:19 [22084] >f+++++++++ Quickbook2013/Properties/Properties..ND 
2015/03/03 00:18:20 [22084] >f+++++++++ Quickbook2013/Properties/Properties..QBW[/FONT][/COLOR]
[/FONT][/COLOR]
```

Also if this helps, the source directory is a local Linux filesystem folder and the destination is a mounted Windows share.

Any thoughts are appreciated.

---

### Post by nerdtron on 2015-03-04
I'll just bump this.. maybe someone good on rsync can explain me on how it creates those temp files.

---

