---
title: "ldd (GNU libc) 2.6.1"
date: 2007-11-05
forum: General Help
---

### Post by pedja_portugalac on 2007-11-05
After installing gutsy updates rkhunter check give fallowing warning:

[00:52:00] /usr/bin/ldd                                      [ Warning ]
[00:52:00] Warning: The file properties have changed:
[00:52:00]          File: /usr/bin/ldd
[00:52:00]          Current inode: 2345251    Stored inode: 2343543
[00:52:00]          Current file modification time: 1193274171
[00:52:00]          Stored file modification time : 1191200505
[00:52:00] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.

**Is there anybody who knows more about this, please help me? **

---

### Post by luckykar on 2007-11-05
I have the exact same message since the update...does anybody else get it as well.

[10:27:21] /usr/bin/ldd                                      [ Warning ]
[10:27:21] Warning: The file properties have changed:
[10:27:21]          File: /usr/bin/ldd
[10:27:21]          Current inode: 10635670    Stored inode: 10633847
[10:27:21]          Current file modification time: 1193274171
[10:27:21]          Stored file modification time : 1191200505
[10:27:21] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.

---

### Post by pedja_portugalac on 2007-11-05
Now I know that the script come inside update package libc6_2.6.1-1ubuntu10_i368.deb and that it's OK, but I still don't know how to tell rkhunter it's OK:( I have tried to put "#" before the "SCRIPTWHITELIST=/usr/bin/ldd" but it still warn me.:( Anybody knows how to do that???

---

### Post by pedja_portugalac on 2007-11-05
No way. I have tried to remove rkhunter.log file and rkhunter.log.old but no way to calm warnings of a rootkit hunter. :(

---

### Post by luckykar on 2007-11-06
> **pedja_portugalac said:**
> No way. I have tried to remove rkhunter.log file and rkhunter.log.old but no way to calm warnings of a rootkit hunter. :(

To reset  rkhunter do  sudo rkhunter --propupd this will stop the warning on this file ,  and it will reset the data file of stored values with the current values.

The md5sums of the suspect file is exactly the same as the file it replaced so its looks like a False Positive...

Anyone else find this warning  , i have two boxes that have been updated and they both have the same error.

---

### Post by pedja_portugalac on 2007-11-06
> **luckykar said:**
> To reset  rkhunter do  sudo rkhunter --propupd this will stop the warning on this file ,  and it will reset the data file of stored values with the current values.

The md5sums of the suspect file is exactly the same as the file it replaced so its looks like a False Positive...

Anyone else find this warning  , i have two boxes that have been updated and they both have the same error.

 sudo rkhunter --propupd  
[ Rootkit Hunter version 1.3.0 ]
File updated: searched for 150 files, found 122

**Still Warning :( **

---

### Post by luckykar on 2007-11-06
All mine have come back clean , (no warnings) after running sudo rkhunter --propupd  . Are you still getting the same warning or a different one on another file.


System checks summary
=====================

File properties checks...
    Files checked: 122
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 1 minute and 12 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

---

### Post by pedja_portugalac on 2007-11-07
System checks summary
=====================

File properties checks...
    Files checked: 122
    Suspect files: 1

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 58 seconds

/usr/bin/ldd                                             [ Warning ]

fckmi, can you tell me please step by step how did you get this?

---

### Post by luckykar on 2007-11-07
Just open a terminal and type in : sudo rkhunter  --propupd hit enter it will ask for your password and it should fix the issue.

Just be aware that if you are pasting this into the terminal it contains a space after rkhunter and two - -  of these side by side sometimes the forums display characters wrong and this may be the cause.

sudo rkhunter --propupd

sudo rkhunter --update

sudo rkhunter --checkall --nocolors

see how that goes.

---

### Post by OrangeCrate on 2007-11-07
> **luckykar said:**
> 
see how that goes.


It worked fine, thanks.

System checks summary
=====================

File properties checks...
    Files checked: 122
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

---

### Post by ameba on 2007-11-26
=

---

### Post by paul.matthijsse on 2007-12-10
hidden files/dirs: rkhunter always reports some (3 or so), always the same as well, don't worry about that (better: I don't worry about that)

to see the log:
sudo gedit /var/log/rkhunter.log

---

