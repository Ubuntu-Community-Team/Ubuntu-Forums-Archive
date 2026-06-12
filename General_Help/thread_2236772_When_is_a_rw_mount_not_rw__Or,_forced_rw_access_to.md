---
title: "When is a rw mount not rw?  Or, forced rw access to Journaled HFS+ stopped??"
date: 2014-07-28
forum: General Help
---

### Post by xmbwd on 2014-07-28
I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=1723857") and [here]("http://ubuntuforums.org/showthread.php?t=1751009") to force rw access to the OSX partition on my iMac from my Ubuntu partition.  And it worked for a day.  Then it stopped working.  But it stopped working in a strange way:  it ***says*** that the user (mbwd) has rw access to the files on the HFS+ drive (see ;s -la from the OSX partition below), *but I can't actually rw*.  

Any idea what that means?  Or how I can fix it?

```
ls -la
total 16
drwxr-xr-x 1 mbwd dialout    12 Jun 28 16:48 .
drwxr-xr-x 1 mbwd dialout    24 Jul 27 13:22 ..
drwxr-xr-x 1 mbwd dialout     6 Nov 18  2013 2010
drwxr-xr-x 1 mbwd dialout    18 Mar 25  2012 2011
drwxr-xr-x 1 mbwd dialout    20 Jan 12  2013 2012
-rw-r--r-- 1 mbwd dialout 15364 Jun 28 16:48 .DS_Store
drwxr-xr-x 1 mbwd dialout     4 Nov 18  2013 Holiday Cards 
drwxr-xr-x 1 mbwd dialout    34 Jun 16 14:57 iPhoto Library
drwxr-xr-x 1 mbwd dialout     5 Nov 14  2013 Lightroom
-rw-r--r-- 1 mbwd dialout     0 Dec  5  2011 .localized
drwxr-xr-x 1 mbwd dialout    34 Apr 23  2012 Photos for Print
drwxr-xr-x 1 mbwd dialout     3 Mar 23 14:42 Picasa Desktop
```

Oh, and here is the /etc/fstab entry:
```

/dev/sda2 /media/mbwd/iMac hfsplus force,rw,exec,auto,users,uid=501,gid=20 0 0
```

As noted in the links, I changed the Ubuntu UID to 501 and the GID to 20 (both of which match the iMac), and I also changed the permissions.

---

