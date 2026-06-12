---
title: "gnump3d and access from different partition (nobody)"
date: 2007-10-01
forum: General Help
---

### Post by tmas on 2007-10-01
I`m running gnump3 perfect when I`m cathing music from /var/music, but I do want to catch the music from another partition (sda3 vfat) but I dont get this to work.
I`m starting sda3 with nobody attributes, but I`m still getting a blank browser screen when opening up [http://localhost:8888](http://localhost:8888)

Here`s my fstab for the sda3:
UUID=46F3-28D2 /media/sda3     vfat    defaults,utf8,umask=007,gid=46,uid=nobody 0       1

How can I get gnump3d access music on sda3??
I have all the rw rights on sda3.

Thomas

---

### Post by tmas on 2007-10-02
Nobody knows how this stuff works?

Please?? :)

---

### Post by tgalati4 on 2007-10-02
I assume you ran gnump3d-index to update the index file?  This normally only happens once per day (via a CRON job).  If you need immediate results, then you need to run it manually.

---

### Post by bren on 2007-10-09
tmas = this is a permissions problem - gnump3d won't serve files that aren't marked as public (eg have group user of everyone and the right chmod of 644 for files plus x for directories)

as i understand it vfat does not store user permissions?

so i think this might be difficult

but this is only my thoughts and might be quite wrong

more here

[http://lists.gnu.org/archive/cgi-bin/namazu.cgi?query=windows+share&submit=Search%21&idxname=gnump3d-users&max=10&result=normal&sort=score](http://lists.gnu.org/archive/cgi-bin/namazu.cgi?query=windows+share&submit=Search%21&idxname=gnump3d-users&max=10&result=normal&sort=score)

---

### Post by tmas on 2007-10-17
Got it fixed finaly!
I only needed to change umask from umask=007 to umask=000! It wasnt harder than that! :D

Anyway, thanx for all the help.
Thomas

---

