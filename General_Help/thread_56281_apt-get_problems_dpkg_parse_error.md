---
title: "apt-get problems dpkg parse error??"
date: 2005-08-12
forum: General Help
---

### Post by Digitallysick on 2005-08-12
Building dependency tree... Done
The following packages will be upgraded:
  dbus-1 dbus-1-utils dbus-glib-1 dbus-qt-1 evolution
  kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4 kgamma
  kghostview kmrml kolourpaint kpdf ksnapshot ksvg libc6 libc6-dbg libc6-dev
  libc6-i686 libc6-pic libc6-prof libgadu3 libnetpbm10 locales netpbm xpdf
  xpdf-common xpdf-reader xpdf-utils
30 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/53.4MB of archives.
After unpacking 238kB disk space will be freed.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6006 package `python2.4-dbus':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by heimo on 2005-08-12
[QUOTE=Digitallysick]dpkg: parse error, in file `/var/lib/dpkg/status' near line 6006 package `python2.4-dbus':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)[/QUOTE]

That's your clue. I would try to (possibly incorrect filenames):

 ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status_mybackup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

``` 
and try again. I'm not sure about that status-old - might be status_old or something else. This is just a hunch, but worth trying.

---

### Post by SneakyWho_am_i on 2008-05-18
I know this is an ANCIENT thread (or else you've just traveled back in time!!)
but....
Did anyone ever find a PEACEFUL solution to this?
I've just had the exact same problem with /status (different package and line number)
gedit couldn't open it because I couldn't specify a valid charset.

I opened the file in mousepad, deleted two symbols from the Martian alphabet, saved it (and a copy, but whow's a copy of a broken file going to help!?) and now I'm fixing packages.

Fixing. Packages. I'm not actually missing any of the dependencies at all - it's just "forgotten" most of what I have installed :(
I tried removing the file altogether and it ate my face.

NOTE: I think my faulty RAM bit me and caused this. I hope I don't break everything by accidentally reconfiguring something I shouldn't :(
NOTE2: Oh well. If I do, I will at least still have the data on the disk, so it won't be a total meltdown like it would be in that **other** operating system if a critical file melted......

---

### Post by alveola on 2008-05-23
I just had the same problem and this solution worked perfectly! Just what I needed. When I compared the 'status' and 'status-old' file, just a few characters were changed. How? When? Why?. Anyway, it was the perfect moment to restore the '-old' version.

I guess this is just the reason why a '-old' file is created!

---

