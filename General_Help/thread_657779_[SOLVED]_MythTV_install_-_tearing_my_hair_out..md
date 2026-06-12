---
title: "[SOLVED] MythTV install - tearing my hair out."
date: 2008-01-03
forum: General Help
---

### Post by Weidbrewer on 2008-01-03
I'm trying to install a MythTV frontend/backend on a machine, and even following instruction guides is not getting the job done.  I'm sorry in advance for the Tolstoy, but no one in the meat world has been able to help me, and this should have been a simple install.

When I first run 
```
sudo apt-get install mythtv mythtv-themes
```

I get the following error included in the readout:


```
adduser: Warning: that home directory does not belong to the user you are currently creating.

Setting up mythtv-database (0.20.2-0ubuntu10.1) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: NO) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
```

After that, I *have* run sudo dpkg-reconfigure mythtv-common and sudo dpkg-reconfigure mythtv-database, so I thought that would have solved the above.

Later, I run in to trouble with with the backend setup.  Although several guides are similar, this guide has screenshots, which may help:  [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

In the setup section, you notice that there are several blue screens that I'm supposed to get to.   I got to one blue screen *once*...but it was none of the screens they have listed.  First one was language screen, which led to the mysql setup.   Since then, no matter how many times I have uninstalled and purged, I can't get to any screens like those.  Now,when I run setup  (through the GUI or command line) I get the following:

```
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2008-01-03 23:02:48.511 Using runtime prefix = /usr
2008-01-03 23:02:48.528 Gnome-Screensaver support enabled
2008-01-03 23:02:48.529 DPMS is active.
2008-01-03 23:02:48.544 New DB connection, total: 1
2008-01-03 23:02:48.550 Using WOL to wakeup database server (Try 1 of 5)
WOLsqlServerCommand not set
2008-01-03 23:02:58.561 Using WOL to wakeup database server (Try 2 of 5)
WOLsqlServerCommand not set
2008-01-03 23:03:08.566 Using WOL to wakeup database server (Try 3 of 5)
WOLsqlServerCommand not set
2008-01-03 23:03:18.843 Using WOL to wakeup database server (Try 4 of 5)
WOLsqlServerCommand not set
2008-01-03 23:03:28.847 Using WOL to wakeup database server (Try 5 of 5)
WOLsqlServerCommand not set
2008-01-03 23:03:38.850 WOL failed, unable to connect to database!
2008-01-03 23:03:38.851 Unable to connect to database!
2008-01-03 23:03:38.851 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'weidbrewer'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 23:03:38.903 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 23:03:38.958 Using WOL to wakeup database server (Try 1 of 5)
WOLsqlServerCommand not set
2008-01-03 23:03:48.961 Using WOL to wakeup database server (Try 2 of 5)
WOLsqlServerCommand not set
2008-01-03 23:03:58.965 Using WOL to wakeup database server (Try 3 of 5)
WOLsqlServerCommand not set
2008-01-03 23:04:08.967 Using WOL to wakeup database server (Try 4 of 5)
WOLsqlServerCommand not set
2008-01-03 23:04:18.975 Using WOL to wakeup database server (Try 5 of 5)
WOLsqlServerCommand not set
2008-01-03 23:04:28.978 WOL failed, unable to connect to database!
2008-01-03 23:04:28.978 Unable to connect to database!
2008-01-03 23:04:28.978 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'weidbrewer'@'localhost' (using password: YES)
```

The Wake on Lan part just continues to repeat.


I really, really hope that someone out there can help me.  ](*,)

---

### Post by RC Howe on 2008-01-04
I had exactly the same problem. The SQL database was not automatically created for me, so I had to myself. Create a database called mythconverg. Set the password in SQL, then put it into MythTV. If it does not seem to be working, try root as the username.

Alternatively, you may just try running```
gksu mythbackend &
```

---

### Post by Weidbrewer on 2008-01-04
Thanks.  I will give that a try.

Now that I knew what to look for, I did see that there were a few other threads like this.  They all had the bulk of my problem, but I didn't notice anyone else with this problem:

```
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Any ideas on that?

---

### Post by Weidbrewer on 2008-01-05
Although it wasn't by the above instructions, they showed me where to look.   I've got it up and running now.  Thanks.

---

