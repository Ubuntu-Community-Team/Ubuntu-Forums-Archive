---
title: "bugzilla 2.20 from universe, how to upgrade to 2.22?"
date: 2006-09-07
forum: General Help
---

### Post by bbiales on 2006-09-07
Hi, I'm fairly new to Linux, and find Ubuntu in general a breeze to get and install packages.  Installed LAMP and bugzilla with no problems at all.  But the bugzilla package is for bugzilla 2.20, while the current stable release is 2.22.  I've seen others post that the package creates a "non-standard" install of bugzilla, putting it in a few different directories.  Those posts make it sound like upgrading with the tarball diff from bugzilla won't work. 

Has anyone got experience with this?  I find that because I used the package to install bugzilla, and I've never done a stock install of bugzilla myself, I am at a real loss at figuring out the upgrade, because I don't know where the package put things, nor do I really know where the bugzilla folks think they are!

I did see that there is a 2.22 package for Edgy.  I also know that installing packages from "unstable" releases on a "stable" release can get ugly.  But perhaps someone might know enough to say that this particular package would be "safe" for use on the "Dapper Drake" release?  

If someone would tell me how to get access to the Edgy packages (new line in /etc/apt/sources.list, perhaps?) I'd be willing to create a test machine, install bugzilla 2.20 from Dapper, then change the sources.list file and attempt to upgrade with the Edgy package and "see what happens".  
Thanks in advance for any assistance.

---

### Post by mlind on 2006-09-07
Here's bugzilla-2.22 packages for Dapper. Source package is included, but you'll just need to install the .deb packages. This should upgrade your current bugzilla version to 2.22.

[http://www.freefilehoster.com/uploads/1157640475bugzilla-2.22_dapper.tar.gz](http://www.freefilehoster.com/uploads/1157640475bugzilla-2.22_dapper.tar.gz)

---

### Post by bbiales on 2006-09-07
Wow, now that is service!
I'm curious to know what the procedure is to actually put this package into the "Universe" set of packages, and if that is being done already.  I would think some extensive testing would be required before puting it there.  

I will run the package and try it out.  If I run into any problems, I'll post them in this thread.
Thanks again.

---

### Post by mlind on 2006-09-07
> **bbiales said:**
> Wow, now that is service!
I'm curious to know what the procedure is to actually put this package into the "Universe" set of packages, and if that is being done already.  I would think some extensive testing would be required before puting it there.  

I will run the package and try it out.  If I run into any problems, I'll post them in this thread.
Thanks again.

If you're interested contributing to universe section, see
[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

I guess universe packages will only get "official" updates through backports.
To request a package to be backported for Dapper, it needs to be on Edgy first. Then you can file a [bug/request]("https://launchpad.net/products/dapper-backports/+bugs") to launchpad.net.

---

### Post by bbiales on 2006-09-07
Oh-oh.  I've run into a (hopefully minor) problem.  This package first installed two other new packages, one being dbconfig-common.  Well, it asked some questions about my MySQL, such as the user password to access it, but now has displayed 

"an error seems to have occurred while installing the database.  If it's any help this was the error encountered:

dbconfig-common can not determine the maintainer script running it"

Any ideas how to best get around this issue?  Thanks!

---

### Post by mlind on 2006-09-07
> **bbiales said:**
> Oh-oh.  I've run into a (hopefully minor) problem.  This package first installed two other new packages, one being dbconfig-common.  Well, it asked some questions about my MySQL, such as the user password to access it, but now has displayed 

"an error seems to have occurred while installing the database.  If it's any help this was the error encountered:

dbconfig-common can not determine the maintainer script running it"

Any ideas how to best get around this issue?  Thanks!

Did this error stop install procedure? Are you able to reconfigure it using dpkg-reconfigure bugzilla (or similar) ?

---

### Post by bbiales on 2006-09-07
I selected <ignore> and all seemed to work.  I kept my old params, and my old localconfig (since this is an upgrade from 2.20).  

It completed, but then I got this error when I tried localhost/bugzilla:
No value for param utf8 (try running checksetup.pl again) at /usr/share/perl5/Bugzilla/Config.pm line 225.

So I did what it says (ran checksetup.pl again) and now it comes up fine.  But my template changes are gone... I only changed the main page, perhaps this was changed in the new release and so my template was turned off... 
No matter, I'm happy.  Thanks for your help.

---

