---
title: "Pipe Trouble - Plumber Required!!"
date: 2007-11-19
forum: General Help
---

### Post by neilbain on 2007-11-19
I am planning on moving several directories of data using Tar to archive then restore them.

I have no problem using Tar but I want to record the output of Tar (especially any errors that occur) so that I can troubleshoot any issues that arise.  I thought that could pipe the output like this...

```
tar -xpkjf my_backup.tar.bz2 > my_record_of_activities.txt
```

... but it doesn't work :(

I am no expert in using pipes so grateful for any help offered.

---

### Post by Seisen on 2007-11-19
Try

```
tar -xpkjf my_backup.tar.bz2 | my_record_of_activities.txt
```

---

### Post by mali2297 on 2007-11-19
> 
tar -xpkjf my_backup.tar.bz2 > my_record_of_activities.txt

With this, you will only get the standard output from tar, not the error messages. Instead, try

```

tar -xpkjf my_backup.tar.bz2 2> my_record_of_activities.txt

``` 
..redirects error messages.

```

tar -xpkjf my_backup.tar.bz2 > my_record_of_activities.txt 2>&1

```
..redirects both standard output and error messages.

```

tar -xpkjf my_backup.tar.bz2 >> my_record_of_activities.txt 2>&1

```
..does the same but without overwriting previous content of my_record_of_activities.txt.

---

### Post by neilbain on 2007-11-19
Top answer Mali...  Many thanks

---

