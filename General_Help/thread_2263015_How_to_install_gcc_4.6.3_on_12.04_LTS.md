---
title: "How to install gcc 4.6.3 on 12.04 LTS"
date: 2015-01-28
forum: General Help
---

### Post by ufarmer on 2015-01-28
I would like to install gcc 4.6.3 using apt, if possible, but I cannot seem to choose a version any more specific than just 4.6 and, when I choose this, apt tries to install 4.6.4 even though the files in the repo still appear to be for version 4.6.3.  I have tried to install 4.6.3 directly from source but the installation fails.

If someone could advise me how to 1) install 4.6.3 using apt or 2) point me to some reliable installation instructions for 4.6.3 it would be appreciated.

---

### Post by deadflowr on 2015-01-28
Do you have any added ppa's, which may be why you see 4.6.4.
Just a thought...

---

### Post by ufarmer on 2015-01-28
Hadn't thought of that.  I suppose it's possible.  I have always just added whatever ppa's I have needed whenever I have needed them.  How would I check?

---

### Post by deadflowr on 2015-01-29
Well, software sources (which you can access through the software center, synaptic>if installed, or the settings button in the update manager) in the *Other Software* tab
will show you all the added ppa's you have.

Of course to simplify things you could run an apt-cache policy on gcc
```
apt-cache policy gcc
```
then look at where it says the version(s) is coming from
Here's what mine currently looks like for precise
```
gcc:
  Installed: 4:4.6.3-1ubuntu5
  Candidate: 4:4.6.3-1ubuntu5
  Version table:
 *** 4:4.6.3-1ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```
If it's available in some ppa then it'll show a line for that ppa's launchpad address, typically.
( of course ppa's are not limited only to launchpad addresses, but they are the most common)

***Though, I think technically ppa's are all launchpad addresses, I'm using ppa as term for a catchall for all 3rd party repositories here.
(If that makes sense)

---

### Post by ufarmer on 2015-01-29
I broke gcc somehow and tried to reinstall it.  At the moment, gcc is not install but, when I try to reinstall it with apt-get, I get this odd message:

> >> sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]

If I do try to reinstall it fails with this message:

> Errors were encountered while processing:
 gcc
E: Sub-process /usr/bin/dpkg returned an error code (1)

In fact, it seems I cannot install anything at the moment.  I thought apt might be choking on this failure but no amount of purging, cleaning, reconfiguring or any other solution I have found Googling has had any effect.

Do you have any suggestions?

---

### Post by deadflowr on 2015-01-29
Have you tried a
```
sudo apt-get install -f
```
to see if it'll fix it? -- the fix broken package command?

(I assume it was one of the google things you tried, but am not sure, so...)

---

### Post by ufarmer on 2015-01-29
Yes, I did.  That command fails with the same error.

---

### Post by ufarmer on 2015-01-29
Here is a larger version of the error message.  I did try to run the configure script while trying to manually install gcc 4.6.3.

> Setting up gcc (4:4.8.2-1ubuntu6) ...
update-alternatives: error: alternative path /usr/bin/gcc doesn't exist
dpkg: error processing package gcc (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

