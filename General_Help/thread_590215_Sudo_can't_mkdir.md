---
title: "Sudo can't mkdir"
date: 2007-10-24
forum: General Help
---

### Post by CulleyS on 2007-10-24
This has me totally confused, so I must be missing something obvious.  All of a sudden today, I cannot create directories like this:

"sudo mkdir /something/something"

$ sudo mkdir /something/something
mkdir: cannot create directory `/something/something': No such file or directory


And running "mkdir /something/something" gives me this error:

$ mkdir /something/something
mkdir: cannot create directory `/something/something': Permission denied


I _can_ doing something like this though:

$ sudo mkdir /something

Any clues?  Programs are suddenly erroring out on install because of this.  They error out when it comes to making the directories.

Thanks,

Culley

---

### Post by kebes on 2007-10-24
If you try to do "mkdir /somedir/subdir" and "somedir" does not already exist, you will get an error. You can add the "-p" switch to make it work, though:
mkdir -p /somedir/subdir

---

### Post by CulleyS on 2007-10-24
Aha, thanks.  That's good to know.  Hadn't really ever encountered this before. :)  I usually do as you suggested:

sudo mkdir /something
sudo mkdir /something/subdir

In that order.

Thanks again.

---

