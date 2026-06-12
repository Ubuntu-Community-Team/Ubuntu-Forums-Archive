---
title: "Problem with half-installed conexant driver"
date: 2007-08-09
forum: General Help
---

### Post by switchcode on 2007-08-09
Hello =)
After months of coping with a terrible dial up connection fr my ubuntu edgy install, DSL finally arrived on the island I live on. Im happily connected to my wireless AP @ 2mb/s, thanks to an edgy package and distro upgrade.. HOWEVER;
  Every time I try to install anything new from synaptic, or from terminal, I have an error report about the old conexant drivers. Im afraid I cannot remember if i tried to uninstall these drivers or not.. I went into synaptic to try to completely remove the conexant drivers, and got this error;
```
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant

```

As yet, I know nothing about ubuntu linux (or any flavour of linux, for that matter), but it seems that the uninstall information is missing from wherever it should be.. 
  How do I finally remove these half-installed conexant drivers?

---

### Post by kevinlyfellow on 2007-08-09
try this
```

sudo dpkg --force-remove <packagename>

```
Replace <packagename> with the name of the package of course.

---

### Post by switchcode on 2007-08-09
i tried that, and got this;
```
dpkg: unknown force/refuse option `remove'
```

=/

Edit: Grrr I cant install anything now either; conexant is locked as "remove".. Every time I try to install anything by any method, the install aborts because it tries to remove conexant first =(

---

### Post by kevinlyfellow on 2007-08-09
oops, my bad, that's not an option...
try this instead.
```
sudo dpkg --force-all <packagename>
```

You can also try
```
sudo apt-get -f install
```

---

### Post by switchcode on 2007-08-09
sudo dpkg --force-all conexant
Returned with:
```
dpkg: need an action option
```
sudo apt-get -f install
Returned with;
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  conexant
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1851kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 119341 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant
E: Sub-process /usr/bin/dpkg returned an error code (1)
:~$ sudo dpkg--force-all conexant
sudo: dpkg--force-all: command not found
```

Sorry about this =( and thank you for trying

---

### Post by kevinlyfellow on 2007-08-09
not at all, I should be the one apoligizing, I can't seem to get that simple command right!

But I've been looking at what I was suggesting, and that was crap too.

Let's hope this suggestion doesn't have a similar fate ;-)  Let's make it think those modules exist
```

cd /proc/modules
sudo touch hsfserial hsfengine hsfbasic2 hsfosspec

```

and then try to install something.

---

### Post by switchcode on 2007-08-10
ugh =/
I got so annoyed with it that I just reinstalled everything..
Im now back to my beautiful edgy + beryl, stable and smiling, installing everything I wanted (vmware player namely..)
Whats bugging me now is that your last suggestion looks like it would have probably worked.
A huge thank you for trying, Kevinlyfellow, and again I apologise for wasting your time;
  I know that in future I will have too many personal docs and collected progs on here to warrant a full reinstall. Im trying my hardest to learn fast, and hopefully contribute on ubuntuforums, paying forward your effort!

---

### Post by kevinlyfellow on 2007-08-10
> **switchcode said:**
> ugh =/
I got so annoyed with it that I just reinstalled everything..
Im now back to my beautiful edgy + beryl, stable and smiling, installing everything I wanted (vmware player namely..)
Whats bugging me now is that your last suggestion looks like it would have probably worked.
A huge thank you for trying, Kevinlyfellow, and again I apologise for wasting your time;
  I know that in future I will have too many personal docs and collected progs on here to warrant a full reinstall. Im trying my hardest to learn fast, and hopefully contribute on ubuntuforums, paying forward your effort!

Don't worry about it, I help people on the forums because I enjoy doing so, not because someone is pointing a gun to my head :-).  If I were just beginning I would have reinstalled also.  When I started, I must have reinstalled at least 3 or 4 times, and then when I had a "permanent" installation, I messed around with it so much I couldn't install anything unless I used some program that compiled software and made red hat packages.  I even gave up for a year!  Now I've built a linux beowulf cluster for my school and found myself hosting lug meetings.  

Screwing up and doing things wrong is the only way to learn how to use a computer, linux is no exception.  Screw things up early on, so that if you get completely lost, you have the safety of reinstallation.  I strongly suggest (if you haven't already done so) to make a separate home partition so that if you need to reinstall, you can keep all your data and personal settings.

---

### Post by switchcode on 2007-08-10
Damn thats a good idea =j
I shall create a separate partition right now. Thanks dude =)

---

