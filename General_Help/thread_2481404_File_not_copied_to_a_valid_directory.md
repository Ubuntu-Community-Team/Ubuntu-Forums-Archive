---
title: "File not copied to a valid directory"
date: 2022-11-28
forum: General Help
---

### Post by raleigh3 on 2022-11-28
Ubuntu_Documents.zip is not being copied to Local_Backup_Dir?

/home/andy/Backup/Ubuntu_Mate_20.04/ does exist.

Other files are being copied to that directory.

Can someone offer some things I can check?

Thanks.

```
Backup_Directory="/media/andy/Maxtor/Backup/"
Local_Backup_Dir="/home/andy/Backup/Ubuntu_Mate_20.04/"

cd $DOCS
touch Blank.odt
zip -u Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg *.csv *.xls *.jpg 
## ONLY copy file if it's newer than destination file
##
rsync --progress -r -u Ubuntu_Documents.zip $Backup_Directory
rsync --progress -r -u Ubuntu_Documents.zip $Local_Backup_Dir


```

---

### Post by aljames2 on 2022-11-28
In your scripting it is best to use the full path to your commands, such as:
/path/to/rsync
/path/to/zip

Use whereis command to find the correct path to the commands you wish to run, such as:
```
whereis rsync
```

Also, use the full path to your source & destination locations.  You do not need to script directory changes before executing commands as you might do manually from a command line.  Instead, script using full paths as already mentioned.  Not sure what you are doing with cd & touch in your script.

I don’t use zip.  Zip does not retain linux ownerships, groups & other attributes on files it contains.  Unless you are really really strapped for storage resources, you could forego the zipping & go straight to rsync.  If you must compress, tar would be a better option for retaining linux attributes, but depending on your file sizes there could be limitations here to.

---

### Post by raleigh3 on 2022-11-29
I really appreciate the feedback.

 I will implement those changes. :-)

---

