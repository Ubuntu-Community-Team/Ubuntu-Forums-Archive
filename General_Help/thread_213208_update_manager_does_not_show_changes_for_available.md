---
title: "update manager does not show changes for available updates"
date: 2006-07-11
forum: General Help
---

### Post by nanotube on 2006-07-11
Hey all
another sneaky problem here. seems like the update manager has recently taken to not showing anything in the "changes" box for any packages that show up in the updates list. 

when i click on a package in the list, it briefly shows the "downloading list of changes..." message in the Changes text box, then that goes away and box remains blank.

anyone else have the same problem? anyone know where the changelogs are actually downloaded from, so that i can go there "manually" and look? i did go to us.archive.ubuntu.com (as listed in my sources.list), and when i look at [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)
it lists the updates, but there is only the "description", but no changes. 

so then i go to [http://us.archive.ubuntu.com/ubuntu/pool/main/](http://us.archive.ubuntu.com/ubuntu/pool/main/), and find the package in that directory tree, and i can get the latest .diff.gz file, unzip it, and get the diff, then somewhere in the middle of the file there will be a changelog, and i can get the actual changelog for the latest version.

but... that can't possibly be the way update-manager does that, it's way too convoluted! how is it going to parse through the diff file to get the changes (it's possible of course, but the file didn't look too structured to me, and that seems like a lot of work.)

so, to summarize, i have two questions:
1. why isn't update manager automatically pulling changelogs?
2. where is update manager /supposed/ to pull the changelog from?

please, may i see some feedback on this? any ideas what's going on?

---

### Post by nanotube on 2006-07-11
bumpety bump bump. :) anyone?

---

### Post by domf on 2006-07-11
Yep - same problem - not sure how long it has been happening but I noticed it for the 1st time today.


Dom

---

### Post by mike984 on 2006-07-14
Mine doesn't show change description either.  Clicking on some updates will show it's downloading the change description and then my system will automatically log out requiring me to log back in again.  This has been happening for quite a while.

---

### Post by bruce89 on 2006-07-14
Update Manager gets it's changelogs from the Ubuntu Archive.  Sometimes the changelogs don't exist yet.  I filed a [bug]("https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/39462") quite a while ago now about how changelogs should be fetched from Launchpad.

---

### Post by ketsugi on 2006-07-14
I've found this to be happening since Dapper went release.

---

