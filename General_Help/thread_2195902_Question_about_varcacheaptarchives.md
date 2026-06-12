---
title: "Question about /var/cache/apt/archives/"
date: 2013-12-27
forum: General Help
---

### Post by Tristan_Williams on 2013-12-27
This is just a question, but it kinda goes along with a "solution" of sorts that I've been working on.

Is the contents of "/var/cache/apt/archives/" a complete list of all software installed on the system, or just a partial list?
Also, can the .deb files there be used to install software, or are they just used for list/archive purposes?

---------------------------------------------------------------------------------

And in case you were wondering what my "solution" is for I shall explain below:

I have a main computer which run a custom Ubuntu that I have built from the minimal command line install method (yes, even more minimal that Ubuntu Server)

I also have a computer I use for testing, which I often have to uninstall and reinstall Ubuntu.

I hate having to spend half a day getting things back to normal after reinstalling Ubuntu Minimal.

My I am looking for a way to just keep every configuration that matters on a Flash Drive. This would include:

All PPAs
All packages
/etc/bash.bashrc
/etc/apt/sources.list
/home/USER/bashrc
Custom Kernel / Custom Kernel source package
Configurations for important software/packages


Anyways thanks in advance for help with /var/cache/apt/archives/ :)

---

### Post by mikewhatever on 2013-12-27
/var/cache/apt/archives/ contains all the downloaded .deb files, which can be used on another machine, but it's not a complete list of anything, just a bunch of installation files. You can get a list of installed packages with **dpkg -l**, and while what you want is doable the way you want it, there are better ways.
[Tar System Backup and Restor]("https://help.ubuntu.com/community/BackupYourSystem/TAR")
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by steeldriver on 2013-12-27
If you use

```
dpkg --get-selections
```

instead of dpkg -l then it outputs the package list in a way that is directly importable into the new system (using dpkg --set-selections). 

AFAIK the deb files /var/cache/apt/archives are not a complete record (the cache is cleared by clean / autoclean operations) and backing them up is not the way to go (aside from which their versions may not be consistent with the target system).

---

