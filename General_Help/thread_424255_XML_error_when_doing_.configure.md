---
title: "XML error when doing ./configure"
date: 2007-04-26
forum: General Help
---

### Post by CAFH on 2007-04-26
Hi @all,

When i try to configure source i get the following error:
> checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool


it says that it need perl module... Where to find?
Any solutions?

Thx for helping,
CAFH

---

### Post by Theimon on 2007-04-27
Open up Synaptic and search for Perl XML,  it should come up with the right package(s).

---

### Post by ebash on 2007-04-27
The following command should fix the problem:

```
sudo apt-get install libxml-parser-perl
```

If you are compiling software that's already available in the repositories, here's more help on how to proceed:

[http://ubuntuforums.org/showpost.php?p=2547535&postcount=22]("http://ubuntuforums.org/showpost.php?p=2547535&postcount=22")

---

### Post by CAFH on 2007-04-28
Thx ebash, that worked.

---

