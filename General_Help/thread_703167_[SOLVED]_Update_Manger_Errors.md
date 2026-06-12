---
title: "[SOLVED] Update Manger Errors"
date: 2008-02-21
forum: General Help
---

### Post by Fahadcom on 2008-02-21
Hello,
when I'm try updating the Ubuntu 7.10  i get this error in Update Manager Window "software updates correct errors, eliminate security vulnerabilities and provide new features"

Any Help ?

---

### Post by kesman on 2008-02-21
That's not an error, it just tells you that updates correct these problems and add extra functionality sometimes. Just continue with your updates.

---

### Post by Fahadcom on 2008-02-21
Unfortunately I'm trying to do the updates many times but it won't start correctly this tow message appear very fast like 1 or 2 second! 
Any Idea?

---

### Post by phrawzty on 2008-02-21
> **Fahadcom said:**
> Unfortunately I'm trying to do the updates many times but it won't start correctly this tow message appear very fast like 1 or 2 second! 
Any Idea?

Based on the message and thumbnails you posted, there doesn't appear to be any problem.  Perhaps you could explain the issue further ?  Does the update process fail to finish ?  Do you receive any additional errors ?

You might wish to try an update via the command line as well, as it will provide additional output that could be useful.  Make sure that the graphical update tool is not active, then do the following from a shell :
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

This will do the same thing as the update manager, but in text-only format, meaning that any error messages will be easier to copy and paste.  As well, error conditions may be easier to describe, as the text can be scrolled through after the fact.

---

### Post by Fahadcom on 2008-02-23
> **phrawzty said:**
> 
You might wish to try an update via the command line as well, as it will provide additional output that could be useful.  Make sure that the graphical update tool is not active, then do the following from a shell :
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

This will do the same thing as the update manager, but in text-only format, meaning that any error messages will be easier to copy and paste.  As well, error conditions may be easier to describe, as the text can be scrolled through after the fact.

OK i got this message when i enter these command : 
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

```
fahad@fahad-ubuntu:~$ sudo apt-get update
[sudo] password for fahad:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
fahad@fahad-ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fahad@fahad-ubuntu:~$ 

```

and i have one more Q how can i active or disactive the graphical update tool?

thank You,,, :)

---

### Post by Fahadcom on 2008-02-23
thank you all 
i "solved" the problem ,,,,

---

