---
title: "Update problem"
date: 2007-05-25
forum: General Help
---

### Post by dryder on 2007-05-25
Hi

Updates told me yesterday (and today) that I have updates available.

They are:
Importasnt security:
linux-libc-dev  Version 2.6.20-16.28:
nvidia-glx

Recommended:
Python
Python-gdbm
Python-minimal
Python2.5
Python2.5-minimal

I don't know how to copy and paste the text message in the details box but all of these display "serious bugs of ..[package name] at least once per package and Are you sure you want to install/upgrade the above packages (Y/N)?

What should I do please? If I say N then updates notifier remains telling me there are updates available.

Many thanks,
David

---

### Post by Happy_Man on 2007-05-26
Open up a terminal (System -> Accessories -> Terminal) and type:
```
sudo apt-get clean
```

to get rid of all those broken packages. Now, redownload them using update manager.

---

### Post by dryder on 2007-05-26
Hi,

I cleaned them out and re-downloaded them. Thanks for telling me how to clean out corrupt packages.

Unfortunately, though, to no avail.

Importasnt security:
linux-libc-dev Version 2.6.20-16.28:
"grave bugs of linux-libc-dev (2.6.20.15.17->2.6.20-16.28) <pending> ....
(I can't copy the whole message)
Are you sure you want to install/upgrade the above packages (Y/N)?

and all the others give errors too.

My system doesn't seem to be broken - I have not encountered any problems.

This is the first time in edgy or in this feisty I've had a problem like this.

---

### Post by Happy_Man on 2007-05-26
Do you need libc-dev? Couldn't you just make do with libc?

---

### Post by dryder on 2007-05-26
Thanks for your help.

> Do you need libc-dev? Couldn't you just make do with libc?
As far as _I_ am concerned, no (edited word), unless a program I have installed uses it.

Evolution uses Python which is presumably why the Python updates come up - which also all have errors when trying to update.

I did sudo apt-get autoremove to remove unused packages but libc-dev still comes up as an update.

Just not installing them means the updates icon will show all the time which is a nuisance.

---

### Post by nealmcb on 2007-12-23
Yeah - this "grave bugs" part is confusing. It turns out to come from apt-listbugs as
discussed here:
[http://ubuntuforums.org/showthread.php?t=531951](http://ubuntuforums.org/showthread.php?t=531951)

and I doubt that going ahead with the install would hurt anything.

[I'm just replying now (late!) so others who stumble across this in search of help (like I did) will see a more complete picture.  ]

---

### Post by dryder on 2007-12-24
Thanks, nealmcb! :-)

---

