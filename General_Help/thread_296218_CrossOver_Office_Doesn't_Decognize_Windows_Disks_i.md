---
title: "CrossOver Office Doesn't Decognize Windows Disks in Edgy"
date: 2006-11-09
forum: General Help
---

### Post by Athanasius on 2006-11-09
I have been having this problem since I installed Edgy.  Just to note, though, that I have found a workaround for this problem and I am posting this in the event that anybody else has a problem like this (it is not really a howto so I put it here).  The solution I found is at the bottom but if anyone has a better way to fix it please post.

```
We have tested your Linux CD drive configuration for compatibility with Windows CD-ROMS.  This is necessary because some Windows CD-ROMS are not compatible with every Linux configuration.
```

However it was very compatible with Dapper so I don't know what is going on.  When I click the "FIX" button I get:

```
Crossover needs to make the following world readable: /dev/.tmp-3-0
```

I click "OK" and then terminal comes up and I get:

```
/usr/bin/sudo -H /bin/sh -c "chmod ugo+r /dev/.tmp-3-0"
```

I enter the password and then it says that it is done but Crossover still has a problem with the disk.

So what I did is open the disk and copy all the files to desktop.  Then I go to panel and under Accessories> CrossOver> Install Windows Software> Microsoft Office XP> other .exe file> browse>Desktop>setup.exe> open> next
Then all should go fine.

---

