---
title: "apt/dpkg questions"
date: 2006-12-29
forum: General Help
---

### Post by foogod on 2006-12-29
Hi all..

I've been adminsitrating Linux machines for quite a few years now, but up til now have used exclusively RPM-based distributions.  I've recently gotten into Ubuntu and am very impressed by the distribution so far (it's actually become my new favorite very quickly), but I'm still getting the hang of a few of the small differences, such as using deb packages and such..

I've heard lots of people tell me for many years how vastly superior apt/dpkg/etc are to RPM for package management, but I'm having a hard time figuring out how to do some types of operations I routinely do on my RPM-based systems.

I figured out how to get a list of what files in the filesystem are associated with a particular package, but how can I get the system to compare the contents/ownership/permissions/etc of the files currently installed on the system against what's actually shipped in the .deb package so I can tell if anything's changed since they were installed (the equivalent of 'rpm --verify')?  Also, is there any way to find out which files are "configuration" files (and thus changes might be ok) vs. static files that shouldn't ever be changing (this information is provided automatically with most RPM packages and displayed by 'rpm --verify')?

Also, is there any way to reconstruct the dpkg database for a system (eg from all the relevant .deb files) if it gets corrupted or deleted?  A while back I created a script to do this for RPM systems using some of the advanced features of rpm, but dpkg doesn't seem to have some of the required options (such as an equivalent to 'rpm --install --justdb') to do the same thing for deb packages.  This worries me a little bit as it seems to me if this isn't possible that the only alternative if such a thing did happen would be to wipe the system and reinstall/reconfigure everything from scratch, which is really not a great option..

Anyway, I'm hoping I'm just missing something somewhere.. any help figuring out how to do this sort of thing would be much appreciated!

---

### Post by zippy028 on 2006-12-29
This may not be the most straghtforward answer to your question but I think the [Debian]("http://www.debian.org/doc/manuals/apt-howto/") apt how-to should be of some help.


John

---

### Post by foogod on 2007-01-01
Thanks for the reply..

I've actually read through the apt howto, but I can't find anything in there that actually addresses my questions.  It tells how to find out what files are in a package, but nothing about checking/validating installed files.  I also don't see anything in there about database management..

---

