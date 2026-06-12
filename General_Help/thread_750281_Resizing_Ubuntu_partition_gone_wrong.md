---
title: "Resizing Ubuntu partition gone wrong"
date: 2008-04-09
forum: General Help
---

### Post by TheLions on 2008-04-09
After resizing (increasing amount of ext3)  drive with Paragon Hard manager (Gparted doesn't have option to resize extended partitions) i was unable to boot in Ubuntu. In console it written some error that partition cannot be mounted cause partition changed size.
It suggested to run "fcsv" atfer i run it reported some error like "BlockXY should be on location XYZKJI. Relocate?" after holding "yes" for about 15 min at startup ony grub terminal starts and drive cannot be mounted from LiveCD?

How to fix it????:confused::confused::confused:

---

### Post by bodhi.zazen on 2008-04-09
Gparted will resize extended partitions, you need to resize the logical ones first if you are downsizing (ie two steps, apply changes with each step).

At any rate you can try testdisk : 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is in the repos (you can "install" it when running the Ubuntu live CD) and available on several live CD 's

---

