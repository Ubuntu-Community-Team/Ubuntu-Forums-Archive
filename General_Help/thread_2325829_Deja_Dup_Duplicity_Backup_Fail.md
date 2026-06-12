---
title: "Deja Dup Duplicity Backup Fail"
date: 2016-05-25
forum: General Help
---

### Post by xcrunner78 on 2016-05-25
I cannot figure this one out. This is my first backup on my new System 76 Lemur. This is the error that I receive and I do not know how to solve it:

Failed with an unknown error.

Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1519, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1513, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1370, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1483, in do_backup
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 560, in full_backup
    globals.backend)
  File "/usr/bin/duplicity", line 421, in write_multivol
    globals.gpg_profile, globals.volsize)
  File "/usr/lib/python2.7/dist-packages/duplicity/gpg.py", line 333, in GPGWriteFile
    bytes_to_go = data_size - get_current_size()
  File "/usr/lib/python2.7/dist-packages/duplicity/gpg.py", line 325, in get_current_size
    return os.stat(filename).st_size
OSError: [Errno 2] No such file or directory: '/home/jason/.cache/deja-dup/tmp/duplicity-ueRBKn-tempdir/mktemp-pNZi3g-140'

I looked through the hidden files and that file is missing. Should there be one? I'm using Ubuntu 15.10. What other information do you need to help me solve this problem?

Thanks a lot!!!!
Jason

---

### Post by xcrunner78 on 2016-06-03
Tried to run it again after loading the PPA into the library and this is the new error. If someone could give me advise, it would be much appreciative!

---

### Post by xcrunner78 on 2016-06-07
Bump

---

### Post by leunam12 on 2016-06-07
Sorry for not being able to help you with your particular problem, but why don't you try other system for backup such as clonezilla, tar, fsarchiver or rsync?

---

### Post by xcrunner78 on 2016-06-09
> **leunam12 said:**
> Sorry for not being able to help you with your particular problem, but why don't you try other system for backup such as clonezilla, tar, fsarchiver or rsync?

Thanks [**[COLOR=#000000]leunam12[/COLOR]**]("http://ubuntuforums.org/member.php?u=1449887"), I'll give it a try. What do you use as a back-up program?

---

### Post by speartip on 2016-06-09
Backintime has always worked flawlessly for me & easy to setup.
If you are more adventurous & want a steeper learning curve you could try Areca:
[http://www.areca-backup.org/](http://www.areca-backup.org/)

---

### Post by xcrunner78 on 2016-06-12
> **speartip said:**
> Backintime has always worked flawlessly for me & easy to setup.
If you are more adventurous & want a steeper learning curve you could try Areca:
[http://www.areca-backup.org/](http://www.areca-backup.org/)

Thanks [**[COLOR=#000000]speartip[/COLOR]**]("http://ubuntuforums.org/member.php?u=1776664")! Went and started using backintime. It has been a while since I used it because I didn't think that the PPA was being upkept.  I see that it is now! Now this is my latest problem of a backup. Attached is the scrrenshot with the error. I have no clue what this means. Thanks to whomever can help me.

---

### Post by speartip on 2016-06-12
your problem appears to be not the program but a permissions problem, indicating that the folders you're trying to save your backups to, are not owned by you as they should be, but are owned by root.
Right click the folders in your screenshot, click properties, then permissions & see who the "owner" is.
It may be that by changing the ownership of the folder back to yourself, the problems you're facing may be resolved.

edit. In fact looking again, those folders are root folders. They need to be omitted from your backup, then it might work. Also make sure the folder you're saving to, is also owned by you & isn't a root folder.

---

### Post by xcrunner78 on 2016-06-12
> **speartip said:**
> your problem appears to be not the program but a permissions problem, indicating that the folders you're trying to save your backups to, are not owned by you as they should be, but are owned by root.
Right click the folders in your screenshot, click properties, then permissions & see who the "owner" is.
It may be that by changing the ownership of the folder back to yourself, the problems you're facing may be resolved.

edit. In fact looking again, those folders are root folders. They need to be omitted from your backup, then it might work. Also make sure the folder you're saving to, is also owned by you & isn't a root folder.

Thanks [**[COLOR=#000000]speartip[/COLOR]**]("http://ubuntuforums.org/member.php?u=1776664")! I'll omit them from the back-up. I'm saving to a 1TB external to a folder that I just added to the external before the first time I did the back-up. I'll write back if with an update later when I try to do a back-up this evening and if I have no problems, then I'll make this thread as solved.

Thanks again [**[COLOR=#000000]speartip[/COLOR]**]("http://ubuntuforums.org/member.php?u=1776664")!!!!
Jason

---

### Post by speartip on 2016-06-12
No problem, hope that resolves your issue.

---

