---
title: "Where's the source?"
date: 2004-10-27
forum: General Help
---

### Post by gwon on 2004-10-27
I'm currently trying to install driverloader in order to get my belkin wireless card working. During the installation I'm asked to provide the directory of the linux source (it suggests /usr/src/linux). However I can't seem to find the location of the source.

Any help?

Craig

---

### Post by babui on 2004-10-27
First you must install the package with the source code:
  
        sudo apt-get install linux-source-2.6.8.1
 
 it leaves a tar.bz2 file in /usr/src that can be decompressed by
 
        tar xjf linux-source-2.6.8.1.tar.bz2
 
 and the directory with the source is
  
        /usr/src/linux-source-2.6.8.1
 
 Hope it helps.
 
 JM

---

### Post by gwon on 2004-10-27
I got:

Package linux-source-2.6.8.1 is not available but is reffered to by another package..

---

### Post by gwon on 2004-10-27
[QUOTE=gwon]I got:

Package linux-source-2.6.8.1 is not available but is reffered to by another package..[/QUOTE]
 Can someone direct me? If indeed the package is missing (could it be that it's a different filename), is there somewhere I could download and install the source package?

---

### Post by Rancoras on 2004-10-27
It's right there in synaptic.  I searched for the word "source" and scrolled to the "L"s and there it was.

---

### Post by gwon on 2004-10-27
[QUOTE=Rancoras]It's right there in synaptic.  I searched for the word "source" and scrolled to the "L"s and there it was.[/QUOTE]
 THanks for your help.

You should see my makeshift attempt at getting online in linux, involving a wireless router, a laptop, 2 ethernet cables and some blue tack ;)

---

