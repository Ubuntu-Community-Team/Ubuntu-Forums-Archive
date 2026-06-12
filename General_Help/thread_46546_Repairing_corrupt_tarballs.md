---
title: "Repairing corrupt tarballs"
date: 2005-07-05
forum: General Help
---

### Post by Sethleben on 2005-07-05
I recently reformatted my Linux box and made a backup of important data as a .tar.gz file onto a CD. I then installed Hoary Hedgehog, and, lo and behold, when I tried to restore the data from the archive on the CD, the archive had become corrupt.

I checked on another CD drive and also on a Windows system to see if maybe there had been a read error from the CD, but to no avail.

Anyway, the point of my post is this:
does anyone know of any open-source tools for repairing damaged tarballs? 

I found a Windows-based tool called Advanced TAR repair, but it costs $50.
However, it did list for me the files that it would be able to recover, so in the end I may have to end up buying it if the data is not recoverable in any other way.

Any help most appreciated.

Cheers.

---

### Post by Sethleben on 2005-07-24
After some trawling around I came across this website [HTML]http://www.urbanophile.com/arenn/hacking/gzrt/[/HTML], which has some useful information on this subject. In order to compile the source code provided on the website it was necessary to update the version of zlib installed on Ubuntu. I don't know exactly which packages were needed, but I just installed all of the updates through Synaptic. I also manually copied zlib.h into the include folder before updating zlib, as I was having a few errors and thought this would help. I'm not sure whether installing the additional packages would have done this anyway, but I thought I would mention it for thoroughness.

I then followed the instructions detailed on the website above in order to compile and install the packages, and then proceeded to recover my corrupted .gz archive using gzrecover.

Next I tried to recover some files from the repaired archive:

```
sudo /usr/local/bin/tar --recover --ignore-zeros -xvf Backup.tar.recovered
``` 

Many (although not all) files were then extracted to the current directory, but then after about 5 minutes the following message appeared:

```
/usr/local/bin/tar: memory exhausted
``` 

I'm not sure what memory this is referring to, and why this should be filled up. The archive I'm dealing with is only ~230Mb in size, which isn't even enough to fill up the RAM (256Mb).

Anybody got any ideas?

Furthermore, am I posting this in the right forum? None of the others seemed to be appropriate.

Any help much appreciated!

Sethleben

---

