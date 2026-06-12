---
title: "alien vs SuSE RPMs"
date: 2004-11-20
forum: General Help
---

### Post by MarcDM on 2004-11-20
Hey all.

Tell me, does this alien only function with Red-Hat RPMs? Before Warty, I was using SuSE 9.1 and I have a bunch of RPMs that I'd like to install.

These RPMs are mostly mono stuff (1.0.4/5) that I need to install since I use some of the bug-fixes made available in 1.0.4

I noticed that there was an rpm command available on Ubuntu, does it only work with Redhat RPMs?

Thanks

---

### Post by MarcDM on 2004-11-20
I seem to be answering all my own questions. Hmmm. 

Anywho, It seems to work. 

I used the mono RPM files intended for Suse 9.1 

I seperated the files into folders :
01-dep - dependencies
02-mcs - Mono core + mcs
03-mono - classes from the mono stack
04-ms - classes from the MS.NET stack
05-gtk - GTK# and associated classes
06-data - data providers not included in the MS stack
07-doc - monodoc
08-md - monodevelop

These folders were created using the same hierarchy that is shown on the go-mono.com download page. 

After using alien to convert all the rpm files to deb, I copied the resulting debs into the respective folders. (according to download site)

From there, I changed to each folder in order of number and executed :
dpkg -i ./*.deb

You could [theoretically] also change to the directory above all the others and execute :
dpkg -i -R .

I haven't tested it, but it should work the same.

After that, just fire-up monodevelop and you good-to-go.

**Testing**
I haven't done much testing using this setup, however, MD does work. And I've tested compiling a few small c# projects. No problems so far.  Matter of fact, MD seems more well behaved now than on SuSE.

I'm going to assume it's due to a more stable installation of gnome.


**Errors**:

There were two errors reported by :
cairo-devel_0.2.0-2_i386.deb
gtk-sharp-gapi_1.0.4-2_i386.deb

both were trying to overwrite files already written by another install. In both cases it was a *.pc file (pkgconfig data file). I assume this will cause a problem later, but that's yet to be seen.

---

### Post by MarcDM on 2004-11-20
I only completed this install 20 minutes ago. Haven't tested it much but, It seems to work. 

I used the mono RPM files intended for Suse 9.1 

I downloaded the files into folders :
01-dep - dependencies
02-mcs - Mono core + mcs
03-mono - classes from the mono stack
04-ms - classes from the MS.NET stack
05-gtk - GTK# and associated classes
06-data - data providers not included in the MS stack
07-doc - monodoc
08-md - monodevelop

These folders were created using the same hierarchy that is shown on the go-mono.com download page. 

After using alien to convert all the rpm files to deb, I copied the resulting debs into the respective folders. (according to download site)

From there, I changed to each folder in order of number and executed :
dpkg -i ./*.deb

You could [theoretically] also change to the directory above all the others and execute :
dpkg -i -R .

I haven't tested it, but it should work the same.

After that, just fire-up monodevelop and you good-to-go.

**Testing**
I haven't done much testing using this setup, however, MD does work. And I've tested compiling a few small c# projects. No problems so far.  Matter of fact, MD seems more well behaved now than on SuSE.

I'm going to assume it's due to a more stable installation of gnome.


**Errors**:

There were two errors reported by :
cairo-devel_0.2.0-2_i386.deb
gtk-sharp-gapi_1.0.4-2_i386.deb

both were trying to overwrite files already written by another install. In both cases it was a *.pc file (pkgconfig data file). I assume this will cause a problem later, but that's yet to be seen.

---

