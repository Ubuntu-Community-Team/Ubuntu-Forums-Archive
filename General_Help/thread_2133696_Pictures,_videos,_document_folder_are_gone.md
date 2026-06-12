---
title: "Pictures, videos, document folder are gone"
date: 2013-04-08
forum: General Help
---

### Post by ac98521 on 2013-04-08
I Dont know what happened but I cant find them. Help please. It seems they were all removed as I have a larger storage now. How can I bring them back! THIS IS **** HELP!

---

### Post by kclark on 2013-04-08
Did you install/remove any software before this happened?  Do you have all of your partitions located on one drive or did you use LVM?  Can you open a terminal and do

```

$ cd $HOME
$ ls -al

```

Do you see them with these commands?

---

### Post by ac98521 on 2013-04-08
no. Last time I checked, I had only 21gb free space. Now I have 45. :(

---

### Post by oldfred on 2013-04-09
Stop using system. And use your liveCD/DVD/Flash.

Post this from live install. If you have separarte /home partition, click on it in liveCD to mount it.

       sudo parted /dev/sda unit s print
            # check sizes of 
Partition sizes
df -Th | sort
Inodes:
 df -i
cd / or cd /home (if mounted from liveCD may be /media/yourname if separate partition)
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

And see if testdisk shows a missing partition.
      
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

