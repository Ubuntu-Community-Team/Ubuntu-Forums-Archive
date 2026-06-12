---
title: "[SOLVED] cannot rename a file in recovery mode"
date: 2007-02-25
forum: General Help
---

### Post by unebaguettesvp on 2007-02-25
I'm having this same exact problem as

[http://ubuntuforums.org/showthread.php?p=1681531#post1681531](http://ubuntuforums.org/showthread.php?p=1681531#post1681531)

but with a different file. When I boot up in recovery mode and try to use the cp command I get a "this a read only file system"

All I want to do is rename a file

/etc/init.d/rsC.old -> /etc/init.d/rsC

Any clue how I can do that?


More information on what I am doing:

So before grub boots up the default, I hit escape and select recovery mode. After awhile, I get a terminal. It reads

root@(none):~$

Then i navigate to

cd /etc/init.d

That works. Now:

rm rsC

That gives me an error saying that it can't remove because it is a read-only file system. Then I try

mv rsC.old rsC

Same error: read only file system

What am I doing wrong? Right now I'm using the Installation CD and searching for help online. Any help would be greatly appreciated!!!

---

### Post by finer recliner on 2007-02-25
to rename files via the command line i use the move comand (but move it to the same location it already is ;) 

```

mv oldfilename newfilename

```

if the file is read only, you may need to change it's permissions to have write access. although you're logged in as root....so maybe something else is wrong...?

EDIT: oops it looks like you already tried the mv command. maybe someone else has a better idea. sorry

---

### Post by yopnono on 2007-02-25
What is the output of ```
ls -l
```

---

### Post by koenn on 2007-02-25
seeing that the error is "this a read only _file system_"
you probaly have to remount it read/write : 

```
mount -o remount,rw /
```
If that doesn't work (it might not), just type "mount" to find out where "/" is mounted. Let's say it is on /dev/sda2. You'd then type:
```
mount -o remount,rw /dev/sda2
```

Then go ahead with the mv cp rm commands yuou've tried before

---

### Post by unebaguettesvp on 2007-02-25
THANK YOU! THANK YOU! THANK YOU! THANK YOU! THANK YOU! THANK YOU! THANK YOU!

mount -o remount,rw /
did the trick!

you saved my computer!

---

### Post by koenn on 2007-02-25
> THANK YOU! THANK YOU! THANK YOU! THANK YOU! THANK YOU! THANK YOU! THANK YOU!
:) 

you're welcome.

---

