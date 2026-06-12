---
title: "Delete  3 oldest files"
date: 2018-08-09
forum: General Help
---

### Post by raleigh3 on 2018-08-09
Trying to delete my 3 oldest files

This shows the files.

```
ls -1r /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Ubuntu_Documents.zip_* | tail -n+6 

```
adding this on did not work.

```
| -exec rm {}
```

---

### Post by rwalkerIII on 2018-08-09
The "-exec" is a parameter for the "find" command, so you can't pipe to it since it's not a command itself.

There's probably quicker ways, but one way is in multiple steps:
lst=$(ls -t /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Ubuntu_Documents.zip_*|tail -3)
for f in $lst;do if [ -f $f ];then rm -rf $f;fi;done

---

### Post by raleigh3 on 2018-08-09
The problem with it, is it keeps deleting files until there are none left.

I want there to be at least 1 or 2 copies left after it runs.

---

### Post by QIII on 2018-08-09
Hello!

You will need to capture the count of files, and then control execution to remove no more than 3 files, limited to the original count -2 (or whatever), whichever is least.

---

### Post by Claus7 on 2018-08-09
Hello,

enter the folder in question, where you want to delete the 3 oldest files:
cd /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
and then:
ls -t /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/tail -3 | xargs rm

you can modify the paths according to the place and the files you want to delete.

Regards!

---

### Post by raleigh3 on 2018-08-09
It will not work because I will have ubuntu_scrips.zip, ubuntu_docs.zip etc.

I need just the 3 oldest ubuntu_scrips.zip deleted etc.

I can have them named either of two ways if it makes it any easier.

Ubuntu_Documents_09Aug2018_20_49.zip
or
2018-08-09-16_Ubuntu_Scripts.zip

---

### Post by raleigh3 on 2018-08-10
This is what I have so far.
Seems to be working o.k.

I did not worry about not having the minutes in the file name.

That's because if I have to use Clonezilla to restore an image, that image will contain files older than those in my backup partition.



```
#!/bin/bash
# Ubuntu Mate 18.04 LTS 
#  BACKUP IMPORTANT FILES TO 2nd MAXTOR DRIVE 
# 
#  USE GXMESSAGE TO SHOW A MESSAGE
#   CONTAINS PW !!!
# Much help from https://www.unix.com/shell-programming-and-scripting/
# Especially MadeInGermany and Neo (Admin)
# AND https://ubuntuforums.org/
# BACKUP MY DOCUMENTS
gxmessage -fg red -font  'sans 30' -timeout 3  ' BACKING UP FILES FOR UBUNTU_MATE 18.04.3 LTS'
cd ~/Documents
zip -u -q Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg 
rsync -av --update Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
# ------------------------------------------------------------------------------------------------------------
cp Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Ubuntu_Documents_`date +"%Y-%m-%d-%H"`.zip # date is in year/month/day/hour format
# This deletes those unneeded date files which are zero bytes
find . -type f -size 0b -delete
sleep 1
touch $( date '+%m-%d-%Y_%I:%M-%p' )
```

---

