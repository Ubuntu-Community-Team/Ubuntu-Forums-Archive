---
title: "[SOLVED] Need a script - Any writers available?"
date: 2008-03-22
forum: General Help
---

### Post by Bruce M. on 2008-03-22
Hi folks,

First and foremost I am not a programmer by any stretch of the imagination.

So I'm hoping someone can help me.

Every day I open a folder and delete three files.

I'd like a script that would do that automatically.

What I do: I open /media/sdb1/Back-ups/Schedule/  in there, there are 24 files....

***config_backup_2008.03.14.tgz***
config_backup_2008.03.15.tgz
config_backup_2008.03.16.tgz
config_backup_2008.03.17.tgz
config_backup_2008.03.18.tgz
config_backup_2008.03.19.tgz
config_backup_2008.03.20.tgz
config_backup_2008.03.21.tgz
***home_backup_2008.03.14.tgz***
home_backup_2008.03.15.tgz
home_backup_2008.03.16.tgz
home_backup_2008.03.17.tgz
home_backup_2008.03.18.tgz
home_backup_2008.03.19.tgz
home_backup_2008.03.20.tgz
home_backup_2008.03.21.tgz
***system_backup_2008.03.14.tgz***
system_backup_2008.03.15.tgz
system_backup_2008.03.16.tgz
system_backup_2008.03.17.tgz
system_backup_2008.03.18.tgz
system_backup_2008.03.19.tgz
system_backup_2008.03.20.tgz
system_backup_2008.03.21.tgz

I delete the oldest one of each.

I would like a script that would delete the oldest one by date and then clean the trash bucket.
**EDIT:** Something I could create a launcher for and run once a day, with a safety feature to delete the 8th (9th, 10th - in case I miss doing it) but never the 7th file or lower.

Is it possible?  The problem as I see it is when months change and then years.
Any takers?

Thanks
Bruce

---

### Post by ajmorris on 2008-03-22
hi there,
is it possible to change the format that those backups are being saved as?
because, it might be possible to do a bash script that greps the date command output, then deletes anything in that folder with that date, or, just  config_backup_<grep from date> etc.

---

### Post by Bruce M. on 2008-03-22
> **ajmorris said:**
> hi there,
is it possible to change the format that those backups are being saved as?
because, it might be possible to do a bash script that greps the date command output, then deletes anything in that folder with that date, or, just  config_backup_<grep from date> etc.

Unfortunately, no.  That's the way the program creates them.  :(

---

### Post by lloyd_b on 2008-03-22
In a terminal window:
```
find {directory} -mtime +7 -type f -delete
```
will search in {directory}, locate any file more than 7 days old, and delete any that are found.  Note that this searches based on the "last modified time", which depending on how those files are used may or may not be the same as the date/time the file was created.

Lloyd B.

---

### Post by Bruce M. on 2008-03-23
> **lloyd_b said:**
> In a terminal window:
```
find {directory} -mtime +7 -type f -delete
```
will search in {directory}, locate any file more than 7 days old, and delete any that are found.  Note that this searches based on the "last modified time", which depending on how those files are used may or may not be the same as the date/time the file was created.

Lloyd B.

Hey, that looks good, the files are created and then just sit there unless I need to restore.
And usually that would be the last one created.

Can this be created as a script similar to what I use to start my conky?

ie:

```

#!/bin/bash
cd /media/sdb1/Back-ups/Schedule &
find -mtime +7 -type f -delete

```

or
```

#!/bin/bash
find /media/sdb1/Back-ups/Schedule -mtime +7 -type f -delete

```

... saving it as dob (**D**elete**O**ld**B**ackups) for example, and make it executable?

Bruce

---

### Post by Bruce M. on 2008-03-23
```
bruloo@bruloo [117] --> cd Schedule
-(/media/sdb1/Back-ups/Schedule)------------------------------(11:58 Sun Mar 23)
bruloo@bruloo [118] --> find -mtime +7 -type f -delete 
-(/media/sdb1/Back-ups/Schedule)------------------------------(11:59 Sun Mar 23)
bruloo@bruloo [119] --> 
```

Doesn't work.
The 8th file of each type still exists.  :(

---

### Post by teryowen on 2008-03-23
```
find /media/sdb1/Back-ups/Schedule -mtime +7 -type f -exec rm '{}' \;
```

try that command.

edit:
or maybe its like this:
```
find /media/sdb1/Back-ups/Schedule -mtime +7 -type f -exec rm '{}' +;
```

---

### Post by lloyd_b on 2008-03-23
> **Bruce M. said:**
> ```
bruloo@bruloo [117] --> cd Schedule
-(/media/sdb1/Back-ups/Schedule)------------------------------(11:58 Sun Mar 23)
bruloo@bruloo [118] --> find -mtime +7 -type f -delete 
-(/media/sdb1/Back-ups/Schedule)------------------------------(11:59 Sun Mar 23)
bruloo@bruloo [119] --> 
```

Doesn't work.
The 8th file of each type still exists.  :(

The "-mtime +7" is *extremely* literal in defining what's "more than seven days old".  Specifically, it's "files that are more than 7 days * 24 hours * 60 minutes * 60 seconds, or 604800 seconds, old".

Hmm - rereading your posts, I suspect that it should be "-mtime +6" instead - the first backup will be 0 days old, the second 1 day old, etc, so that anything more than 6 days old is what you want deleted.

Try this in a terminal window: 
```
find /media/sdb1/Back-ups/Schedule -mtime +6 -type f
```
and see if it finds the files you want deleted (without the "-delete", it won't do anything, just list them).

As for your script ideas, 
```
#!/bin/bash
find /media/sdb1/Back-ups/Schedule -mtime +6 -type f -delete
```
should work just fine (once we figure out the correct "-mtime" value)- save it to a file ("dob") and "chmod 700 dob" to make it executable.  

Lloyd B.

---

### Post by Bruce M. on 2008-03-23
> **lloyd_b said:**
> The "-mtime +7" is *extremely* literal in defining what's "more than seven days old".  Specifically, it's "files that are more than 7 days * 24 hours * 60 minutes * 60 seconds, or 604800 seconds, old".

Hmm - rereading your posts, I suspect that it should be "-mtime +6" instead - the first backup will be 0 days old, the second 1 day old, etc, so that anything more than 6 days old is what you want deleted.

Try this in a terminal window: 
```
find /media/sdb1/Back-ups/Schedule -mtime +6 -type f
```
and see if it finds the files you want deleted (without the "-delete", it won't do anything, just list them).

As for your script ideas, 
```
#!/bin/bash
find /media/sdb1/Back-ups/Schedule -mtime +6 -type f -delete
```
should work just fine (once we figure out the correct "-mtime" value)- save it to a file ("dob") and "chmod 700 dob" to make it executable.  

Lloyd B.

Hi Lloyd,

Yea, that did it:

```
-(~)----------------------------------------------------------(17:01 Sun Mar 23)
bruloo@bruloo [119] --> find /media/sdb1/Back-ups/Schedule -mtime +6 -type f
/media/sdb1/Back-ups/Schedule/config_backup_2008.03.15.tgz
/media/sdb1/Back-ups/Schedule/home_backup_2008.03.15.tgz
/media/sdb1/Back-ups/Schedule/system_backup_2008.03.15.tgz
-(~)----------------------------------------------------------(17:01 Sun Mar 23)
bruloo@bruloo [120] --> 
```

So delete should work now.

Here is is with -mtime +0

```
bruloo@bruloo [123] --> find /media/sdb1/Back-ups/Schedule -mtime +0 -type f
/media/sdb1/Back-ups/Schedule/config_backup_2008.03.18.tgz
/media/sdb1/Back-ups/Schedule/home_backup_2008.03.20.tgz
/media/sdb1/Back-ups/Schedule/system_backup_2008.03.16.tgz
/media/sdb1/Back-ups/Schedule/home_backup_2008.03.18.tgz
/media/sdb1/Back-ups/Schedule/home_backup_2008.03.17.tgz
/media/sdb1/Back-ups/Schedule/config_backup_2008.03.17.tgz
/media/sdb1/Back-ups/Schedule/system_backup_2008.03.18.tgz
/media/sdb1/Back-ups/Schedule/system_backup_2008.03.17.tgz
/media/sdb1/Back-ups/Schedule/system_backup_2008.03.21.tgz
/media/sdb1/Back-ups/Schedule/home_backup_2008.03.16.tgz
/media/sdb1/Back-ups/Schedule/home_backup_2008.03.19.tgz
/media/sdb1/Back-ups/Schedule/config_backup_2008.03.16.tgz
/media/sdb1/Back-ups/Schedule/home_backup_2008.03.21.tgz
/media/sdb1/Back-ups/Schedule/system_backup_2008.03.19.tgz
/media/sdb1/Back-ups/Schedule/system_backup_2008.03.20.tgz
/media/sdb1/Back-ups/Schedule/config_backup_2008.03.20.tgz
/media/sdb1/Back-ups/Schedule/config_backup_2008.03.19.tgz
/media/sdb1/Back-ups/Schedule/config_backup_2008.03.21.tgz
-(~)----------------------------------------------------------(17:03 Sun Mar 23)
bruloo@bruloo [124] --> 
```

Perfect... now to dob.sh it  :)

Bruce

---

### Post by Bruce M. on 2008-03-23
> **teryowen said:**
> ```
find /media/sdb1/Back-ups/Schedule -mtime +7 -type f -exec rm '{}' \;
```

try that command.

edit:
or maybe its like this:
```
find /media/sdb1/Back-ups/Schedule -mtime +7 -type f -exec rm '{}' +;
```

Hi fellow Canuck, teryowen

As seen above it would be -mtime +6, but yes, I think that ReMove command would work, I'll have to check out the {} thing in the man page first though.

Thanks for your input.
Again it proves there is more than one way to do things.

CHIMO!
Bruce

---

