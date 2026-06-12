---
title: "Messed up password file/can't sudo/No root recovery login"
date: 2007-02-03
forum: General Help
---

### Post by lfloyd on 2007-02-03
Hello

Messed up password file/can't sudo: what if you can't boot into root in recovery mode. I am having similar problems changed samba.config, nsswitch.config, etc to attempt to network with windows business server. Also I have no root access in recovery mode. Furthermore I when I do a list from my lamp server installed on another partition, I can't see all the files. The default for shell should be monochrome the simplest setting so you can see the screen. I can't edit files I can't see. when I use live cd I can't access my hard drive because gnome live won't mount the hard drive. I simply can't get into my ubuntu. Any help would be appreciated. Thanks Help! I've been dealing with this all week. I need a solution that assumes you have no user or root access file whatsoever. The password file has been corrupted no users exist now.




Loretta

---

### Post by melancholeric on 2007-02-03
What happens when you try to boot to recovery mode?

Can you boot from a liveCD?

---

### Post by lfloyd on 2007-02-03
thanks for the quick reply.  Recovery mode for root was not available.  Live CD did not allow access to my hard drive where my ubuntu is located.  Finally I pulled out the original install iso CD, then selected Start or install ubuntu.   From there I was able to see the "disks" selection under System Menu- Administration-Disks.  Live CD did not give me this option.  Under disks I selected my hard drive then selected partitions and then selected the partition of the sysy\tem I wanted to recover.  Then under "Access Path" I selected a direcory to mount my failed system.  Then I selected  browse, from this point I have access to all my files of the failed system.   zI can them open the firectory from within the the CD fileserver system, to the directory where I placed or mounted the files from the failed system.  In order to see all the files in the hone directory of my failed system, under view I selected show HIDDEN FILES.  From there I had recover my old firefox bookmarks so that I could pinpoint exactly where I went wrong.  They were located in the home directory of the failed system in the mozilla folder and firefox subfolder of mozilla.   I am not going thru the changes I made from How to: Active Directory Authentication in ubuntu forums.   Thanks again.  Recovery mode does not work well because ubuntu does not start with the lowest default monitor parameters, so in shell directory lists don't fit on the page you can't search becuase what yo find doesn't fit on the page.  It was a disaster even attempting to find the files that I had changed in shell, and on top of that I had no root privileges to fix anything not even the screen because I couldn't log in as root.



Sincerely, (frustrated with ubuntu's resolution parameters that only work on brand new monitors)


Loretta

---

