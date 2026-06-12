---
title: "Where does the Downloaded packages go?"
date: 2005-09-26
forum: General Help
---

### Post by darius_underhill on 2005-09-26
i was thinking of installing Hoary in my home system, but I do not have an internet connection at home.  So I was thinking I could just copy all of the files i download when I use synaptic to upgarde hoary in my work laptop.  Problem is i do not know where the files are downloaded to  my system.  Can anyone help?

Also I've read somewhere that I just make a local version of the reposotories and use that.  Is this a better alternative? if I do decide to use this method how much diskspace do I need (everything including backports)?

Thanks!

---

### Post by macgyver2 on 2005-09-26
Well, I don't know about the local repository method.  I *think* if the packages are copied over you don't need to worry about that because Synaptic will just see that the packages are already downloaded.  What I can tell you is that the packages are downloaded to /var/cache/apt/archives/

---

### Post by mlomker on 2005-09-26
> Also I've read somewhere that I just make a local version of the reposotories and use that.  Is this a better alternative? if I do decide to use this method how much diskspace do I need (everything including backports)?


If you want to mirror the entire thing that we're talking a lot of space.  We do that at work but it's a couple Terabytes for debian and redhat.

The files are downloaded to /var/cache/apt/archives.

You could look at packages like **apt-cacher** and **apt-proxy**, but maybe just burning that cache directory to a CD-RW after you run an update would suffice.

---

### Post by darius_underhill on 2005-09-26
Thanks for the info! ill try those.. :)

---

### Post by professor_chaos on 2005-09-26
You can make a local repository by adding something like the following in /etc/apt/sources.list that points to the directory with .deb's

deb file:///home/uname/directory/ ./

---

### Post by macgyver2 on 2005-09-27
[QUOTE=professor_chaos]You can make a local repository by adding something like the following in /etc/apt/sources.list that points to the directory with .deb's

deb file:///home/uname/directory/ ./[/QUOTE]
What about the Packages.gz and all those other files?

---

### Post by heimo on 2005-09-27
[quote=macgyver2]What about the Packages.gz and all those other files?[/quote]

Can be generated using dpkg-scanpackages (and dpkg-scansources for source packages).
[http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862)

---

### Post by macgyver2 on 2005-09-27
[QUOTE=heimo]Can be generated using dpkg-scanpackages (and dpkg-scansources for source packages).
[http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862)[/QUOTE]
Ah, great howto...thanks!

---

### Post by David Marrs on 2005-09-27
[QUOTE=darius_underhill]i was thinking of installing Hoary in my home system...[/QUOTE]
Breezy's going to be out in a week or so. You should wait for that.

---

