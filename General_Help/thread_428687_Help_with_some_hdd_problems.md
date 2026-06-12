---
title: "Help with some hdd problems"
date: 2007-04-30
forum: General Help
---

### Post by Lycaon on 2007-04-30
Dear members,

I had an ubuntu 6.06.1 LTS server up and running with two maxtor 160GB sata discs. Those discs were configured in software raid0. It worked great, but last weekend i could get some spare discs of a friend.
In the end i have to following discs:
  - Maxtor 160GB S-ATA (SATA1 PORT)
  - Maxtor 160GB S-ATA (SATA2 PORT)
  - Samsung 160GB P-ATA (IDE MASTER) - IDE1
  - Samsung 160GB P-ATA (IDE SLAVE)    - IDE1
The samsungs are the same type and the maxtors too.

So i thought it would be a good time to reinstall the complete server to get rid of the raid 0 config.
The installer of ubuntu 6.06.1 LTS finds all four drives, and i can manually edit the partion table.
So on the IDE Master i create a root and swap partition and the rest will be mounted as /DISC1.
All the other discs are formated and mounted as /DISC1 till /DISC4. 
The install works fine etc, but when booting the following error occurs:
  **mdadm: /dev/md0 assembled from 1 drive - not enough to start an array.**
Now when i login to the server and ask for the free disc space with "df -h" i get all partitions except my SATA PORT2 drive (sdb1). It wont mount, and im guessing its because mdadm wants to make it an raid array.

My mobo has an raid controller on board, but it is turned off.

I dont know anymore how i can get BOTH sata drives available?!

Please help me on this one!

NOTE:
What ive tried already:

> edit /etc/defaults/mdadm

change "START_DAEMON" and "AUTOSTART" to false.

and 

> As well as any /etc/default options, you can remove any startup services (note - just the links) using :

update-rc.d -f <name> remove

See : man update-rc.d

e.g.

update-rc-d -f mdadm remove

Will remove any "S" (start) and "K" (kill/stop) links - so these services do not start up anymore. If you want to start anything afterwards, you can still start via "/etc/init.d/<name> start", or put the links back using "update-rc.d".

---

### Post by Lycaon on 2007-05-01
OK newsflash, the problem is solved but not the way i wanted.
All the tests above and the setup i wanted was with ubuntu 6.06.01 LTS version.
That version runs mdadm at startup even if i tell it to do not, anyways it tries to make an array with discs, but only if i have all 4 drives connected. Doesnt matter what, if i install the os on 1 sata and leave 1 sata and 1 ide with it in the install. It works, but if i plug the second ide in , it goes bitching again.

I didnt find out how to solve the "automatic array-ing" problem, so ubuntu 7.04 server edition was the solution.
And yes just one install, and everything worked fine and got mounted correctly.

---

