---
title: "apt-get flash for 12.04LTS onwards?"
date: 2014-06-18
forum: General Help
---

### Post by cheeyi on 2014-06-18
Hey all,

I recently got a summer student job at my college as an undergrad systems worker, and I'm helping the math department manage their Ubuntu machines. What we are doing currently for new machines is to use a preseed disc that automatically installs all software, and one of the apt-get installations started to fail recently, namely:

```
sudo apt-get install flashplugin-nonfree
```

> [COLOR=#111111][FONT=Arial]Reading package lists&#8230; Done
Building dependency tree
Reading state information&#8230; Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source[/FONT][/COLOR]
[COLOR=#111111][FONT=Arial]E: Package &#8216;flashplugin-nonfree&#8217; has no installation candidate
[/FONT][/COLOR]
I've tried using adobe-flashplugin, and a few other packages mentioned on several different forum threads but to no avail. The primary purpose is to get flash working on Mozilla Firefox by using just terminal commands, hopefully using apt-get. 

Any help would be much appreciated!

---

### Post by deadflowr on 2014-06-18
First make sure the repos are up and running right
```
sudo apt-get update
```
then if nothing is wrong try installing
```
sudo apt-get install flashplugin-installer
```

---

### Post by monkeybrain20122 on 2014-06-18
If you isntall ubuntu-restricted-extras it would pull in flash and other things like codecs which you will need eventually. So you shouldn't  install flash separately.

And please use a gui (Software Centre or better, synaptic) where you can seach for packages with keywords. Using the terminal is fine as long as you know the names of the packages, and sometimes you may just remember them wrong or the package names may have changed if you copy those "sudo apt-get install blah" lines from several years old forum posts or online tutorials.

---

