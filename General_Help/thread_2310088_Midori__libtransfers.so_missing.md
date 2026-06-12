---
title: "Midori  libtransfers.so missing"
date: 2016-01-16
forum: General Help
---

### Post by Claude_Sutton on 2016-01-16
Ubuntu 14.04

Midori will not run.

When midori is entered in the terminal, I get the message that it can not find /usr/lib/midori/libtransfers.so

I can not find the solution.

Midori was installed from the Midori web site using their PPA.

I got the same result when installing from Ubuntu software center.

Any help will be appreciated.

---

### Post by Bucky Ball on 2016-01-16
Did you uninstall the version from their site prior to installing the one from Software Centre? Best to look in Software Centre first rather than manually adding PPAs.

---

### Post by Claude_Sutton on 2016-01-16
I have used midori for years and messed it up somehow trying to find a substitute for adobe flash.
The original was installed from the software center.

I uninstalled using the software center and reinstalled using it.

After trying multiple times to get it to run, I uninstalled, did an apt-get autoclean, auto remove, and then tried the ppa.

---

### Post by vasa1 on 2016-01-16
Do you get any error messages when you run **sudo apt-get update**?

Have you tried **sudo apt-get -f update**?

What about **sudo apt-get install --reinstall midori**?

What's the output of **sudo dpkg -C**?

---

### Post by Claude_Sutton on 2016-01-16
> **vasa1 said:**
> Do you get any error messages when you run **sudo apt-get update**?

Have you tried **sudo apt-get -f update**?

What about **sudo apt-get install --reinstall midori**?

What's the output of **sudo dpkg -C**?

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 libjson0:amd64       JSON manipulation library (transitional package)


apt-get install reports that the first is installed and is the latest ver. and the second is unknown.

I do not understand the midSums control file comment.

---

### Post by Claude_Sutton on 2016-01-16
I ran apt-get remove  midori.

apt-get autoremove

apt-get autoclean

apt-get install --reinstall libjson0:amd64 

And that cured the libjson0:amd64 missing message.

I then reinstalled midori from the software center and it works.

The install --reinstall libjson0:amd64 

 was the real solution.

Thanks for that clue.

I forgot how to mark the thread as solved.  It has been along time since I have posted here.

---

### Post by vasa1 on 2016-01-16
> **Claude_Sutton said:**
> ... I forgot how to mark the thread as solved.  It has been along time since I have posted here.
That's here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

