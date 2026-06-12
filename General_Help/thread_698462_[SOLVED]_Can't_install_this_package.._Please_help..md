---
title: "[SOLVED] Can't install this package.. Please help..."
date: 2008-02-16
forum: General Help
---

### Post by geo909 on 2008-02-16
Hello everybody.
I was using 'Audio Tag Tool' for a long time to manage my music files but after sometime I did a format.
Now I am trying to install it again. It can be found as "tagtool" in the repositories.
Here's what happens when I try to install it using apt-get:

```

jorge@jorge-desktop:~$ sudo apt-get install tagtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tagtool: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages
jorge@jorge-desktop:~$ 

```

I was really used to this tool and it's very frustrating I can't get it installed..
Please, any ideas?!

---

### Post by drs305 on 2008-02-16
I just tried installing it via synaptic and it worked fine (although I have the 64bit version). Have you tried getting it through synaptic instead of via apt-get?

Edited: if you don't use synaptic much, perhaps Edit, Reload Package Information before installing might get you the latest version and dependencies. If it already shows up as installed there, mark for complete removal and then try again.

---

### Post by mwx10 on 2008-02-16
are you sure that the package is not corrupt?

you could try downloading it of there website and see if they have any bianary packages or you could download the source code and build it your self (autoconf and gcc)

---

### Post by geo909 on 2008-02-16
I've tried through synaptic, too. Same problem:

[LEFT][[IMG]http://www.imageshack.gr/files/b4k27ss14u7o96boaiqt.png[/IMG]](http://www.imageshack.gr/view.php?file=b4k27ss14u7o96boaiqt.png)[/LEFT][RIGHT][[IMG]http://www.imageshack.gr/files/i7pmu2bijbapishlzkmy.png[/IMG]](http://www.imageshack.gr/view.php?file=i7pmu2bijbapishlzkmy.png)[/RIGHT]

In their homesite they had a deb package that didn't work either...

@drs305:
You said it was fine with synaptic.. Do you think it's something with the repositories?

---

### Post by geo909 on 2008-02-16
And that's what I get with the 'deb' package:
[CENTER][IMG][[IMG]http://www.imageshack.gr/files/v8yi5067eoab9zglgj2h.png[/IMG]](http://www.imageshack.gr/view.php?file=v8yi5067eoab9zglgj2h.png)[/IMG][/CENTER]

---

### Post by drs305 on 2008-02-16
> @drs305:
You said it was fine with synaptic.. Do you think it's something with the repositories?

Synaptic says it is getting it from the multimedia / Universe (multiverse) repository. The version is 0.12.3-2ubuntu0.1  It is possible the 32 bit version is numbered different but probably not.

---

### Post by MighMoS on 2008-02-16
Sounds like a bug. If you haven't done so already, I'd recommend submitting a bug at [http://launchpad.net](http://launchpad.net).

---

### Post by oldos2er on 2008-02-16
Try running "sudo aptitude install -f", then "sudo aptitude update".

 If that still doesn't work, go to System, Administration, Software Sources, and make sure all the boxes are check under 'Downloadable from the Internet.'

---

### Post by geo909 on 2008-02-16
Feel so stoopid! :oops:

It was just about repositories. Indeed, I had to "check every box in there", that did the job..
Thanks for your answers!

---

