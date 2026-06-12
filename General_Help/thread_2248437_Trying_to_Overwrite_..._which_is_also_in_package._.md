---
title: "Trying to Overwrite ... which is also in package.  Error.  UHD.  GNU-Radio"
date: 2014-10-14
forum: General Help
---

### Post by imzack2 on 2014-10-14
I cannot find anything online anywhere and do not really want to uninstall everything since, 1. I don't want to lose my files, and 2. It was a pain to install in the first place...

My issue can be see in the screenshot below.  I have tried force installing, purging the messed up packages and re-installing... I feel like I have tried alot but with no luck!

I was wondering if someone could please lend me their assistance and walk me through this, I am very frustrated...


[ATTACH=CONFIG]257220[/ATTACH]

Keep getting this "trying to overwrite '/usr/include/uhd/device_deprecated.ipp", which is also in package libuhd-dev 3.5.5-1

Any suggestions?

---

### Post by TheFu on 2014-10-14
I don't have an answer - just more things to try.
a) use aptitude - it is smarter than apt-get
b) do an **aptitude update** && **aptitude dist-upgrade** - before trying anything else. This will get the system completely patched. This is really something that should be done weekly, but on a system not on the internet, monthly should be ok.
c) reinstall the problem package. There is an option for that with both aptitude or apt-get.

The package doesn't seem to be signed - are you really certain you want to install that on the box?

Less data is used for text than images ... just sayin' - plus I can't copy/paste text from an image to help. ;)

---

### Post by imzack2 on 2014-10-14
Sorry, see below for code version.

Also, I am positive I want to use uhd, it is apart of the GNU-Radio Companion for SDR (Software Defined Radio), which i think it pretty awesome!  Check it out here:

[http://gnuradio.org/redmine/](http://gnuradio.org/redmine/)

[http://code.ettus.com/redmine/ettus/projects/uhd/wiki/GNURadio_Linux](http://code.ettus.com/redmine/ettus/projects/uhd/wiki/GNURadio_Linux)

```
WARNING: The following packages cannot be authenticated!
  uhd
Install these packages without verification? [y/N] y
(Reading database ... 571061 files and directories currently installed.)
Preparing to unpack .../uhd_003.007.002-90-unstable_amd64.deb ...
Installing UHD.
Unpacking uhd (003.007.002-90-unstable) ...
dpkg: error processing archive /var/cache/apt/archives/uhd_003.007.002-90-unstable_amd64.deb (--unpack):
 trying to overwrite '/usr/include/uhd/device_deprecated.ipp', which is also in package libuhd-dev 3.5.5-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/uhd_003.007.002-90-unstable_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user:~$ 


```

---

### Post by imzack2 on 2014-10-14
Note: I am trying to run the following script.

```
sudo apt-get install uhd
```

---

### Post by ian-weisser on 2014-10-14
> **imzack2 said:**
> I was wondering if someone could please lend me their assistance and walk me through this, I am very frustrated...

Uninstall the 'libuhd-dev' package.
It's the problem.
It conflicts with 'uhd' - they cannot coexist on your system.

---

### Post by imzack2 on 2014-10-14
omg!!!!

Ian you are my hero!

Thank you soo much!

How did you know that was my issue?!?

---

### Post by imzack2 on 2014-10-14
oh, I see it in my error now...  I would of never thought to remove that though, why can't both packages share the same file?

---

### Post by ian-weisser on 2014-10-14
Because it raises so many questions with unpredictable answers. What if the files are different? Which one should win? When you uninstall a package, does that change the file? 

So the package management world takes the sensible way out: A file can only be provided by one package. Anything else is an error that a human must deconflict.

---

### Post by imzack2 on 2014-10-14
Gotcha, that makes sense, but sounds like it would limit the number of programs you can use...  Unless each program is fully incapsulated and doesn't need to use other common files...  

Interesting, thank you for the run down!

---

### Post by ian-weisser on 2014-10-15
> **imzack2 said:**
> sounds like it would limit the number of programs you can use.

It only limits the number of *badly packaged* programs.
It's essentially the same conflict if you installed manually.

---

