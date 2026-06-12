---
title: "MySql does not work after restart for some time"
date: 2015-03-30
forum: General Help
---

### Post by Vishal_Ved on 2015-03-30
I am using Mysql version 5.6.19 on Ubuntu 14.04.1
  I have a peculiar problem on my server. When I restart the server  mysql takes around 150-200% CPU when I use the "top" command in Linux  some time(around 60 to 90 minutes) with no users on the website. I am  not able to connect to my website during this time.
  After 60 -90 minutes approximately the the CPU usage of mysql come  down in the range of 20-40% automatically and then I can connect to my  website.
  I used to run Mysql version 5.5 before. I have upgraded it to version 5.6 today and I still have the same problem.
  But after upgrading to Mysql 5.6 yesterday, Mysql is showing cpu  usage of 150-200% and website is not running for the last 48 hours.

  My website is hosted on Digital Ocean.
  Please let me know how to fix this problem.

---

### Post by bardo2 on 2015-03-31
I don't know, i am not using mysql. But from the top of my memory, i recall, that all RDBMS start off by playing back the transaction log - if necessary -. Has there been a hard shutdown/power failure recently? can you consolidate manually and make sure to shutdown in a clean way? you might want to have a look at the size of the logs as well.

---

### Post by SeijiSensei on 2015-03-31
Try dumping the database with the mysqldump command, then remove and re-install MySQL and reload the database from the backup.

---

