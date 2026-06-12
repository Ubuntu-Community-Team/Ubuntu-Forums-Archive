---
title: "[SOLVED] How to repair broken package manager files"
date: 2008-01-16
forum: General Help
---

### Post by bkline on 2008-01-16
I've gotten myself into a jam and I need some advice on how to fix it.  I ran the update manager the other day, and it failed.  I investigated and found that it was trying to read cvs.list and couldn't (Input/Output error).  So I moved the file out of the way, and then ran "apt-get remove cvs" which was probably a mistake.  Then I found a copy of cvs.list from an older installation of Debian: the file had the same number of bytes, but I couldn't compare them when what I had moved, of course, since that file is unreadable.  Then I tried to re-install cvs, but got an error message saying the package is unavailable.  So I went through the forums looking for postings describing this problem, and based on advice in those threads, I ran:
```
$ sudo apt-get check
$ sudo apt-get clean
$ sudo dpkg --purge --force-remove-reinstreq cvs
$ sudo apt-get install cvs
```
and I got this response:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cvs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cvs has no installation candidate

Please, what do I need to do to convince apt to install cvs?

---

### Post by geirha on 2008-01-16
Try running ```
sudo aptitude update
``` Does it give any errors? if not, try installing cvs again.

---

### Post by bkline on 2008-01-16
> **geirha said:**
> Try running ```
sudo aptitude update
``` Does it give any errors? if not, try installing cvs again.

Thanks, geirha.  I ran "sudo aptitude update" as you suggested, and there was no error output.  But when I tried installing cvs again I got the same error message as before.

Help!

---

### Post by _sAm_ on 2008-01-16
> Please, what do I need to do to convince apt to install cvs?
I dont know, sorry. But you could perhaps go to Synaptic > Custom Filtres(left down corner), and chose "Broken" pacakage(upper left corner), and see if the aptkg has a list for you. If so, try to reinstall them and see if that will fix it.

---

### Post by bkline on 2008-01-16
> **_sAm_ said:**
> I dont know, sorry. But you could perhaps go to Synaptic > Custom Filtres(left down corner), and chose "Broken" pacakage(upper left corner), and see if the aptkg has a list for you. If so, try to reinstall them and see if that will fix it.

Thanks, _sAm_.  That was a creative suggestion, but synaptic shows an empty list of packages when I follow the steps you gave.

I clearly don't understand how this package management system works.  I'll be happy to read any manuals or how-to guides if anyone can recommend something that will allow me to understand this error message and fix it.

Please!

---

### Post by _sAm_ on 2008-01-16
Same as last time; I dont know.

But have you tried the "sudo aptitude install -f"  As I understand it will fix errors as you have. You could also check out this site; [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/) and look under no 7 there; it decribe how to work with APT errors.

---

### Post by bkline on 2008-01-16
> **_sAm_ said:**
> Same as last time; I dont know.

But have you tried the "sudo aptitude install -f"  As I understand it will fix errors as you have.

Doesn't seem to have done anything:
$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
$ sudo apt-get install cvs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cvs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cvs has no installation candidate

> You could also check out this site; [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/) and look under no 7 there; it decribe how to work with APT errors.

Thanks for the pointer.  I've tried everything on that page (even though the "if your error looks like this ..." stuff didn't really match my errors), and I'm still getting "package cvs has no installation candidate."

Help!  I'm really eager to solve this!  I really don't want to have to re-install the system (or go back to SuSE).  I'd love to be able to click on that new "Thanks!" button!  Doesn't ***anyone*** know how to solve this problem???

---

### Post by geirha on 2008-01-16
Hi again, could you post the content of /etc/apt/sources.list? and if there are any files in /etc/apt/sources.list.d/, post the content of those too (and please enclose such output within ```
-tags for easier reading)

And, are there any files in /var/lib/apt/lists/partial/ ? If so, delete those and try [code]sudo aptitude update
sudo aptitude install cvs
```

---

### Post by bkline on 2008-01-16
> **geirha said:**
> Hi again, could you post the content of /etc/apt/sources.list? ...

Thank you, thank you, thank you!

That was the clue I needed.  Trying to follow some instructions in existing forum threads, I had somehow ended up with a skeletal sources.list.  I restored from a backup (I do nightly backups, for which I'm often grateful), and I'm back on the road.

I really would like to understand the package management system better.  Is there a good guide to this topic, which starts at the 30,000-foot overview level and zooms into the details gradually in an intelligible way?

Again, thank you very much!

Bob

---

