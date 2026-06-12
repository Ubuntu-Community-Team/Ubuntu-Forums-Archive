---
title: "Wine Problems"
date: 2007-01-09
forum: General Help
---

### Post by Rotodyne on 2007-01-09
Hi, I am having some trouble with Wine.

When I try "winecfg" I get this error: 

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

I am still able to get into the interface, when I click on drivers I receive:

You do not have a Drive C. This is not so great.
Remember to click Add in the Drives tab to create one.

When I click on add it shows

C:            ../drive_c

What do I have to change ../drive_c to?

Also, when I click autodetect I get, No Virtual Drive C mapped, Try running wineprefixcreate

So when I run "wineprefixcreate" I get:

mkdir: cannot create directory `/home/evan/.wine/dosdevices/c:/windows': No such file or directory

WHen I try to install starcraft I get a "Path not found error"

I am very new to Ubuntu, is this an easy fix?

](*,) 

Thanks for reading, I shall be back tomarrow

---

### Post by Sqwishy on 2007-01-09
For you're winecfg problem? I think i had the same problem, my drive_c is in ~/.wine/drive_c/

---

### Post by sehe on 2008-06-21
perhaps not superfluous: "wineprefixcreate" is the word

---

