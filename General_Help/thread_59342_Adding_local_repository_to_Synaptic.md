---
title: "Adding local repository to Synaptic"
date: 2005-08-23
forum: General Help
---

### Post by kscelt on 2005-08-23
I'm having problems setting up a local hard drive directory as a repository in Synaptic. I created a directory for local packages (home/kscelt/myrepos).  I then added to sources.list "deb file:home/kscelt/myrepo".  It gives the error "Invalid URI, local URIS must not start with //".

Need help!

---

### Post by macgyver2 on 2005-08-23
[http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862)

---

### Post by clehel on 2005-08-23
Hi,
The line in my sources.list looks like this:

deb file:///data/Downloads-Archives/packages/ ./

Don't forget the ./ at the end (tells to apt-get and Synaptic to look right here for packages and also for the file Packages.gz) After saving the file, hit the reload button in Synaptic. But it will complain that it does not find Packages.gz in your local repo, because for a repo that is also neeeded. 

So each time after you download/delete packages in this repo directory, you first need to cd to your repo dir (/data/Downloads-Archives/packages/ in my case), and then run this command from the console:

sudo dpkg-scanpackages  .  /dev/null  |  gzip  -9c  >  Packages.gz

This will update your Packages.gz file. If you hit Synaptic 'reload' button now, the packages will appear in Synaptic, and you can install them.

---

### Post by kscelt on 2005-08-23
Thanks much - it Worked!

---

### Post by A-star on 2005-09-05
Thanks a lot, this really helped me.

---

### Post by varkatope on 2005-09-24
Hi

the command "dpkg-scanpackages" isn't found on my system:
Ubuntu Breezy Badger 5.10 Colony 4 with all updates till today

What Package do i have to install to make this command work again?

Thanks!

Edit: Problem solved, i just had to install dpkg-dev via synaptic :)

---

