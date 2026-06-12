---
title: "restoring  rdiff back up files"
date: 2014-02-06
forum: General Help
---

### Post by albert14 on 2014-02-06
Hello. I am attempting to restore files from an RDiff back-up  performed  some  2/3 years ago. I have tried the rdiff-backup -r command  but not  getting very far. Here is a screen grab of the files I have.
Could anyone please tell me how to restore the back up files?  BTW - the   increments folder is empty. Bakup log lists all the files backed up.   (See attachments)Thanks in advance.

---

### Post by albert14 on 2014-02-06
what a nightmare.
I tried to attach some images; I was told to drag and drop
I do that and post the message - I get gobbledeegook
I try to edit, firefox freezes on me causing me to to   FORCE QUIT
So I try to delete the damn post and start all over again
you guessed right -  I CAN'T FIND A DELETE POST  button.  
I'll have to start another post now. DAMN

---

### Post by albert14 on 2014-02-06
aLL i WANTED TO DO WAS GET HELP TO RESTORE  files from an rdiff back up from 3 years ago. A backup that was necessitated from yet another hard disk failure thanks to ubuntu. WHY ME:mad:

---

### Post by thereillys1 on 2014-02-06
Do you get a list of backed up files when you run an rdiff-backup -l <filename>?

---

### Post by albert14 on 2014-02-06
Thanks thereillys1 - I got the following error message when I ran the command rdiff-backup -l <filename>.  The <filename> in question is actually a zip file (.gz)  DO I need to issue an inline command to unpack in the list command you provided?

albert@albert-QOSMIO-X870:~$ cd Desktopalbert@albert-QOSMIO-X870:~/Desktop$ cd rdiff-backup-dataalbert@albert-QOSMIO-X870:~/Desktop/rdiff-backup-data$ rdiff-backup -l file_statistics.2012-03-06T07:22:55Z.data.gz
Exception '('rdiff-backup-data', 'file_statistics')' raised of class '<type 'exceptions.AssertionError'>':
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 286, in take_action
    elif action == "list-increments": ListIncrements(rps[0])
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 712, in ListIncrements
    rp = require_root_set(rp, 1)
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 729, in require_root_set
    if not restore_set_root(rp):
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 704, in restore_set_root
    from_datadir[1].startswith('increments'))), from_datadir

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 30, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 286, in take_action
    elif action == "list-increments": ListIncrements(rps[0])
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 712, in ListIncrements
    rp = require_root_set(rp, 1)
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 729, in require_root_set
    if not restore_set_root(rp):
  File "/usr/lib/python2.7/dist-packages/rdiff_backup/Main.py", line 704, in restore_set_root
    from_datadir[1].startswith('increments'))), from_datadir
AssertionError: ('rdiff-backup-data', 'file_statistics')
albert@albert-QOSMIO-X870:~/Desktop/rdiff-backup-data$

---

### Post by albert14 on 2014-02-06
Just to add that I am unable to extract the data file from the zip folder it is held in.. I attach screen grab

---

### Post by thereillys1 on 2014-02-06
What is the name of the file you are trying to recover?
If it is file_statistics, then you should run rdiff-backup -i file_statistics (or [COLOR=#000000]~/Desktop/rdiff-backup-data/file_statistics)

[/COLOR]

---

### Post by sandyd on 2014-02-06
> **albert14 said:**
> what a nightmare.
I tried to attach some images; I was told to drag and drop
I do that and post the message - I get gobbledeegook
I try to edit, firefox freezes on me causing me to to   FORCE QUIT
So I try to delete the damn post and start all over again
you guessed right -  I CAN'T FIND A DELETE POST  button.  
I'll have to start another post now. DAMN

done that for you

---

