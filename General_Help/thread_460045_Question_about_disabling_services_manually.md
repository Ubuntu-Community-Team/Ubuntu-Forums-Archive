---
title: "Question about disabling services manually"
date: 2007-05-31
forum: General Help
---

### Post by dshuck on 2007-05-31
For starters, I do know about update-rc.d, but I have a question about managing services manually.  I am curious about a README that I found in /etc/rc5.d.  In it, it says the following:
> To disable a service in this runlevel, rename its script in this directory
so that the new name begins with a 'K' and a two-digit number, where the
number is the difference between the two-digit number following the 'S'
in its current name, and 100.  To re-enable the service, rename the script
back to its original name beginning with 'S'.

So, if I understand that right, if I have S22my-awesome-app, it would become K78my-awesome-app.

Huh?  Why does this matter?  I understand the numbers as they relate to the way services are started, but why would the order that they are ignored come into play?

As a test, it appears that I can change to K22my-awesome-app, and the service is still disabled.  Could someone please explain the logic of the 100-(original number) thing?

Thanks!

---

### Post by Ufo on 2007-06-08
From "Debian reference" ([http://www.debian.org/doc/manuals/reference/index.en.html):](http://www.debian.org/doc/manuals/reference/index.en.html):)

When entering a runlevel all scripts in /etc/rcrunlevel.d/ are executed. The first letter in the name of the script determines the way in which the script is run: scripts whose names begin with K are run with the argument stop. Scripts beginning with S are run with the argument start. The scripts are run in the alphabetical order of their names; thus "stop" scripts are run before "start" scripts and the two-digit numbers following the K or S determine the order in which the scripts are run.

The idea is that scripts are killed in opposite order than they are started.
Example if you have some program that uses mysql tables, you would want it to start after mysql but stopped before mysql.

Even if service is never started, it's nice to have right numbers in case you later want to add it.

---

