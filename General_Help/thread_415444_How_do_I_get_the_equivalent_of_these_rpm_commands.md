---
title: "How do I get the equivalent of these rpm commands ?"
date: 2007-04-20
forum: General Help
---

### Post by elmerfud on 2007-04-20
When I was running Fedora and I needed to know the version of a package, I used rpm -q <package name>.   How do I do the same sort of thing in Ubuntu ?

Thanks

---

### Post by spin2cool on 2007-04-20
first do an 'apt-get update'  to make sure your packages lists are up to date.

Then, you can use 'apt-cache search <name>' to list the packages.

ie:  'apt-cache search php'

more details here:
[http://newbiedoc.sourceforge.net/tutorials/apt-get-intro/info.html.en](http://newbiedoc.sourceforge.net/tutorials/apt-get-intro/info.html.en)

---

### Post by spin2cool on 2007-04-20
oh yeah - and to be clear, to get full information for a package once you knwo the name:

apt-cache show <packagename>

---

### Post by stylishpants on 2007-04-20
Just to clarify, this is not quite the same as rpm -q.

"apt-cache show <package>" will show you the version and description of the package that is currently available in the repos, whether or not it is installed.

"dpkg -l <package>" will show you the version of the package that is currently installed on your system, just like "rpm -q".  If  the package is not installed, it will tell you.


Also, "dpkg -l" without arguments will list all installed packages in a handy grep-able list, much like "rpm -qa".

---

### Post by elmerfud on 2007-04-20
Thanks !

---

