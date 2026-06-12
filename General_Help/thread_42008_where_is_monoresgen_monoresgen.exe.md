---
title: "where is monoresgen monoresgen.exe"
date: 2005-06-15
forum: General Help
---

### Post by incompetence on 2005-06-15
today i tried to install boo [http://boo.codehaus.org/](http://boo.codehaus.org/) on my ubuntu hoary system.
Altough ```
apt-file search monoresgen.exe
```
says ```
mono-mcs: usr/share/dotnet/bin/monoresgen.exe
```.
I have mono-mcs installed but i am not able to find monoresgen or monoresgen.exe.
I opened mono-mcs_1.1.7-0ubuntu4~5.04ubp1_all.deb in file-roller an copied data.tar.gz out.
```
tar -tvzf data.tar.gz | grep monoresgen
``` -> ```
293 2005-05-14 22:27:47 ./usr/share/man/man1/monoresgen.1.gz
```
What did i wrong an who ist right apt-file or tar -tvzf?
Even the slocate database shows me only the file for the manpage.
The main problem is that nant is searching for monoresgen.exe.

---

