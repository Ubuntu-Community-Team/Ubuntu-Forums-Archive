---
title: "How to reinstall all my current packages"
date: 2007-12-26
forum: General Help
---

### Post by artinla on 2007-12-26
I used aptoncd to save all the packages in my apt-cache after a clean load.  Unfortunately, I think a few had been purged before I saved them. 

Is there any good way to get a list of all the stuff that I have installed so that I can make a script or something to reinstall the same packages on another machine?  I have seen some apps (yum I think) that work somewhat, but they reinstall kernel stuff and libraries etc.  I don't want to open that can of worms, I just want to reinstall all the new packages that have been installed after gutsy was put on. 

I tried the install script generator in synaptic, but it only works if you have all the packages "Marked".
I can't mark them if they are already installed.  Am I missing something there?

How are others accomplishing this?  I am open to any and all advice.

Thanks,

Art

---

### Post by artinla on 2007-12-26
bump

---

### Post by dagnabit dang doohickey on 2007-12-27
This command will save a list of all installed packages in a file called packagelist:
```
dpkg --get-selections | sed 's/[[:space:]]*install$//' > packagelist
```
The list can then be used with apt-get or aptitude to install the same package set on another computer:
```
xargs -a packagelist sudo apt-get install
```

---

### Post by mdurham on 2007-12-27
# Create a text list of an existing installation of all apt-get installed packages
# in order to re-install on a newly installed distro

# make the list
[old distro] sudo dpkg --get-selections >packages

# Now put them back on the new distro
[new distro] sudo dpkg --set-selections <packages

[new distro] sudo apt-get dselect-upgrade

# that's it!

---

### Post by dagnabit dang doohickey on 2007-12-27
The method I offered is what I use because I usually modify the generated package list or otherwise just write one from scratch. But, the method mdurham offered is more appropriate for your stated situation.

---

### Post by artinla on 2007-12-27
Thanks, I appreciate all the suggestions.

Art

---

### Post by artinla on 2007-12-27
New Question...

Say that I have a package list from a fresh install of Gutsy, and a list of packages after I modify it like I want it.  How can I make a file containing only the DIFFERENCES?  A list of only the new stuff.

Thanks in advance

Art

---

### Post by dagnabit dang doohickey on 2007-12-27
Fresh Install: dpkg --get-selections > freshlist

Modified Install: dpkg --get-selections > modlist

The following command will create a list of all packages *installed* on the "modified install" that are *not installed* on the "fresh install."
```
grep -Fvx -f freshlist modlist > installedlist
```

The following command will create a list of all packages *removed/purged* from the "modified install" that are *installed* as part of the "fresh install."
```
grep -Fvx -f modlist freshlist | sed 's/install$/purge/' > removedlist
```

The above two commands will result in files which have the same format as the input files and are usable as such. (installedlist for installing the additional packages on a fresh system, removedlist for purging the unwanted packages from a fresh system.)

But, if all you want to do is eyeball the differences, you can simply diff the two files:
```
diff freshlist modlist
```

---

### Post by artinla on 2007-12-28
dagnabit, you are truly the man.  That does exactly what I wanted.

Thanks!

Art

---

### Post by Marcelo Ramone on 2008-01-06
Some days ago, i removed all packages form my apt-cache.

I need download all my current packages (with dependencies) but do not "reinstall" , only download to my apt-cache and make an add-on CD with AptonCD

It is possible? :s

Thanks in advance.-

---

