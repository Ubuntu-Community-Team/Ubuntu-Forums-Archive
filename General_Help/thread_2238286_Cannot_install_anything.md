---
title: "Cannot install anything"
date: 2014-08-07
forum: General Help
---

### Post by pine508 on 2014-08-07
I'm trying to just install secure-delete to wipe a number of folders for returning a computer, and it isn't working.  (If it is possible to use shred to securely delete folders, I won't need to install secure-delete, but it seems it isn't?)

when I try this:

```
sudo apt-get install secure-delete
```

I get this error message in the terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  secure-delete
0 upgraded, 1 newly installed, 0 to remove and 401 not upgraded.
Need to get 0B/70.2kB of archives.
After this operation, 201kB of additional disk space will be used.
Selecting previously deselected package secure-delete.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `python-twisted-lore': Is a directory
W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (2)

I did run apt-get and tried again and got the same message again.  I haven't been able to install anything on this Ubuntu forever, I think, but it hasn't been necessary so far.  This is using Ubuntu 10.04 LTS (Lucid Lynx), installed as a dual install via WUBI ... the other partition is Windows 7 that won't boot at all (or else I would use Eraser to erase the files from that side).

Any suggestions?

Thanks!

---

### Post by claracc on 2014-08-07
Ubuntu 10.04 is out of support since it is a very old release. The repositories to update and install software packages have been moved out of the server.

About the error you obtain, it seems that you have a duplicate line [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Packages in your /etc/apt/sources.list file.

I think it is not of any use to try to fix the problem in you 10.04 old release but to install a supported ubuntu as 12.04 or 14.04. There is not now any support for wubi neither, so I would do a dual boot install.

---

### Post by pine508 on 2014-08-07
OK, thanks, but basically I need the quickest possible way (like the next couple of hours!) to securely delete a bunch of folders.  shred comes with Ubuntu, but it appears to work only for individual files.  Since I can't install anything, is there some way to get shred or some other program that comes with Ubuntu 10.04 to work to do this?  Thank you.

---

### Post by whitesmith on 2014-08-07
By googling "download shred ubuntu 10.04" I came up witgh this: [http://www.multimediaboom.com/how-to-cleanup-unwanted-files-in-ubuntu-10-1010-0410-04/](http://www.multimediaboom.com/how-to-cleanup-unwanted-files-in-ubuntu-10-1010-0410-04/) Google is your friend.

---

### Post by mörgæs on 2014-08-07
Why not shred the entire 10.04 partition, leaving only Windows? After that you can install 14.04.1 in the free space and the information will be gone.

---

### Post by Mark Phelps on 2014-08-07
> installed as a dual install via WUBI ... means it does NOT have its own partition, but instead, has a file (root.disk) located inside a Windows filesystem partition.

If you "securely erase" the root.disk file and then Uninstall Ubuntu from inside Windows, the files will be entirely gone.

---

### Post by mörgæs on 2014-08-07
Missed the Wubi part, thanks for correcting.

---

