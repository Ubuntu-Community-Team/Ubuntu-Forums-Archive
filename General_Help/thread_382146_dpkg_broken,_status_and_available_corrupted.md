---
title: "dpkg broken, status and available corrupted"
date: 2007-03-11
forum: General Help
---

### Post by pasipasi on 2007-03-11
For some reason my computer crashed earlier and I ran fsck which fixed some things. After that, aptitute has been broken. I tried to use the -old files in /var/lib/dpkg, but those don't work either.

Apparently many words that contained "lib" got replaced with 'li"'. I fixed those, but the problems stays.

> dpkg: parse error, in file `/var/lib/dpkg/available' near line 29688 package `ksirtet':
 `Depends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)


> Depends: kdelibs4c2a (>= 4:3.5.3-1), libacl1 (>= 2.2.11-1), libart-2.0-2 (>= 2.3.16), libattr1 (>= 2.4.4-1), libaudio2, libavahi-client3 (>= 0.6.13), libavahi-common3 (>= 0.6.10$


What's wrong with that line?

As the backups of the files status and available were corrupted too, what can I do?

This is the kind of error I got first: 
> Fetched 217kB in 3s (55.3kB/s)
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing python2.4-gadfly (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


I edited the file "status" and got rid of this problem, but the other problem still stays.

EDIT: [COLOR="Red"]**Meh, fixed..**[/COLOR]

I ran sudo dpkg --clear-avail, which cleared the available file. I was literally googling for hours with different kinds of error messages I got, but I just couldn't find an answer. There are still some things wrong in the status file. For example, I just fixed one line where it said 0ython instead of python. Is my hardware failing? :-O

---

### Post by dcstar on 2007-03-11
> **pasipasi said:**
> 
........
I ran sudo dpkg --clear-avail, which cleared the available file. I was literally googling for hours with different kinds of error messages I got, but I just couldn't find an answer. There are still some things wrong in the status file. For example, I just fixed one line where it said 0ython instead of python. **Is my hardware failing?** :-O

Possibly, you may want to back up anything important until things become clearer.

It may be a good idea to get something like a USB stick and backup all your important data to it - it could be good, convenient insurance against a disk failure.

---

