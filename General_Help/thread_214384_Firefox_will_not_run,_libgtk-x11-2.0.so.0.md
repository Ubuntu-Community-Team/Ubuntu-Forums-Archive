---
title: "Firefox will not run, libgtk-x11-2.0.so.0"
date: 2006-07-12
forum: General Help
---

### Post by Thanol on 2006-07-12
So for the past 2 day's I've been trying to get Firefox to work.  So far I've installed the i686 version, but whenever I try to run Firefox I get this message in the terminal:
> /opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
Then the little floating firefox, cursor thing, goes away.

I've been searching online for help, but all I get are threads by people with AMD64's or something.  My computer's a Pentium 3-m.  Also I tried sudo apt-get install ia32-libs ia32-libs-gtk , but niether of the packages were found. ](*,)

---

### Post by rebelfallen on 2006-07-12
apt-get install gtk 
?
That lib is a standard of gtk... no idea why it wouldn't be found. :-k

---

### Post by Najand on 2006-07-12
> **Thanol said:**
> So for the past 2 day's I've been trying to get Firefox to work.  So far I've installed the i686 version, but whenever I try to run Firefox I get this message in the terminal:

Then the little floating firefox, cursor thing, goes away.

I've been searching online for help, but all I get are threads by people with AMD64's or something.  My computer's a Pentium 3-m.  Also I tried sudo apt-get install ia32-libs ia32-libs-gtk , but niether of the packages were found. ](*,)

I checked it up and it is available. Maybe you  have to edit your sources.list file. Anyway if you could not install it using apt-get or aptitude, use the following link to download the package and  install it using dpkg. 
[http://packages.ubuntu.com/dapper/libs/libgtk2.0-0]("http://packages.ubuntu.com/dapper/libs/libgtk2.0-0")

---

### Post by jtroxel on 2007-01-05
I have a similar issue with eclipse 3.2.  I am using eclipse from the eclipse-SDK-3.2.1-linux-gtk.tar on Kubuntu 6.06 AMD64.
[INDENT]./eclipse
./eclipse: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
[/INDENT]
It looks to me like the libraries are there:
[INDENT]locate libgtk-x11-2
/usr/lib/libgtk-x11-2.0.so.0.800.20
/usr/lib/libgtk-x11-2.0.so.0 (which is a link to ...800.20)
[/INDENT]
Finally, I tried
[INDENT]ldd eclipse
        linux-gate.so.1 =>  (0xffffe000)
        libgtk-x11-2.0.so.0 => not found
        libgdk_pixbuf-2.0.so.0 => not found
        libgobject-2.0.so.0 => not found
        libgdk-x11-2.0.so.0 => not found
        libc.so.6 => /lib32/libc.so.6 (0x5557c000)
        /lib/ld-linux.so.2 (0x55555000)
[/INDENT]
I thought maybe eclipse was expecting the lib to be local, so I made a link as well.  Still, same error.

Any ideas would be much appreciated,  This is the one thing that keeps me from converting to Ubuntu for all my development ;) .  Thanks!

---

