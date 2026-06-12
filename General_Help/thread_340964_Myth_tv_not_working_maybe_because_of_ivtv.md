---
title: "Myth tv not working maybe because of ivtv"
date: 2007-01-17
forum: General Help
---

### Post by fatalfurry on 2007-01-17
This morning I turned on my fully functioning mythtv box and now I cannot watch tv on it. I tried to test the card its self from a command from the ivtv wiki but that site looks to be down. But it was just using the card redirecting it to a file. I could not play that file with any player. Right now i think its the ivtv driver. With their site being down idk what to do. Can any of you help?

---

### Post by majoridiot on 2007-01-18
if you think it's ivtv, then try rebuilding/reinstalling it.  a great guide is here:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

it says edgy, but works for dapper as well.

---

### Post by fatalfurry on 2007-01-18
ok so i went through reinstalling the ivtv driver and the cat /dev/video0 > /tmp/test_capture.mpg command works and i can now view the test file. I still get when i click on watch tv in myth it goes into a black screen and then back to the main menu. I have looked through the setup and my settings are the same as they were before. What could it be?

---

### Post by superm1 on 2007-01-18
> **fatalfurry said:**
> ok so i went through reinstalling the ivtv driver and the cat /dev/video0 > /tmp/test_capture.mpg command works and i can now view the test file. I still get when i click on watch tv in myth it goes into a black screen and then back to the main menu. I have looked through the setup and my settings are the same as they were before. What could it be?
A common problem would be if your recordings partition didn't mount correctly.  Check /var/log/mythtv/mythbackend.log for more information what is happening when you choose "Watch TV".  If there is something about permissions, check to make sure the partition for recordings mounted and has the correct permissions.

---

### Post by fatalfurry on 2007-01-18
the drive is mounted fine and the permissions are rwxr_xr_x. I believe this is correct. When I look at my log file it says

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-01-18 11:23:36.356 Using runtime prefix = /usr
2007-01-18 11:23:36.365 DPMS is disabled.
2007-01-18 11:23:36.472 New DB connection, total: 1
2007-01-18 11:23:36.478 Connected to database 'mythconverg' at host: localhost
2007-01-18 11:23:36.480 Total desktop dim: 1024x768, with 1 screen[s].
2007-01-18 11:23:36.493 Using screen 0, 1024x768 at 0,0
2007-01-18 11:23:36.573 max_width: 1280 max_height: 1024
2007-01-18 11:23:36.574 Total desktop dim: 1024x768, with 1 screen[s].
2007-01-18 11:23:36.575 Using screen 0, 1024x768 at 0,0
2007-01-18 11:23:36.576 Switching to square mode (MythCenter)
libGL warning: 3D driver claims to not support visual 0x4b
2007-01-18 11:23:36.699 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-01-18 11:23:38.182 Joystick disabled.
2007-01-18 11:23:38.229 New DB connection, total: 2
2007-01-18 11:23:38.230 Connected to database 'mythconverg' at host: localhost
2007-01-18 11:23:38.272 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-01-18 11:23:38.273 Using protocol version 31
2007-01-18 11:23:38.294 TV: Attempting to change from None to WatchingLiveTV
2007-01-18 11:23:38.294 Using protocol version 31
2007-01-18 11:23:38.540 GetEntryAt(-1) failed.
2007-01-18 11:23:38.541 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2007-01-18 11:23:38.542 TV Error: LiveTV not successfully started
2007-01-18 11:23:38.542 TV Error: LiveTV not successfully started
2007-01-18 11:23:39.574 TV: Deleting TV Chain in destructor

im not sure what all of this means but i hope it helps.

---

### Post by superm1 on 2007-01-18
> **fatalfurry said:**
> the drive is mounted fine and the permissions are rwxr_xr_x. I believe this is correct. When I look at my log file it says

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-01-18 11:23:36.356 Using runtime prefix = /usr
2007-01-18 11:23:36.365 DPMS is disabled.
2007-01-18 11:23:36.472 New DB connection, total: 1
2007-01-18 11:23:36.478 Connected to database 'mythconverg' at host: localhost
2007-01-18 11:23:36.480 Total desktop dim: 1024x768, with 1 screen[s].
2007-01-18 11:23:36.493 Using screen 0, 1024x768 at 0,0
2007-01-18 11:23:36.573 max_width: 1280 max_height: 1024
2007-01-18 11:23:36.574 Total desktop dim: 1024x768, with 1 screen[s].
2007-01-18 11:23:36.575 Using screen 0, 1024x768 at 0,0
2007-01-18 11:23:36.576 Switching to square mode (MythCenter)
libGL warning: 3D driver claims to not support visual 0x4b
2007-01-18 11:23:36.699 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-01-18 11:23:38.182 Joystick disabled.
2007-01-18 11:23:38.229 New DB connection, total: 2
2007-01-18 11:23:38.230 Connected to database 'mythconverg' at host: localhost
2007-01-18 11:23:38.272 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-01-18 11:23:38.273 Using protocol version 31
2007-01-18 11:23:38.294 TV: Attempting to change from None to WatchingLiveTV
2007-01-18 11:23:38.294 Using protocol version 31
2007-01-18 11:23:38.540 GetEntryAt(-1) failed.
2007-01-18 11:23:38.541 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2007-01-18 11:23:38.542 TV Error: LiveTV not successfully started
2007-01-18 11:23:38.542 TV Error: LiveTV not successfully started
2007-01-18 11:23:39.574 TV: Deleting TV Chain in destructor

im not sure what all of this means but i hope it helps.
That looks like a frontend log to me.  Whats the backend saying when this happens? (/var/log/mythtv/mythbackend.log)

---

### Post by fatalfurry on 2007-01-19
2007-01-18 07:37:09.514 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recorded' is marked as crashed and should be repaired

---

### Post by fatalfurry on 2007-01-21
I believe that was my backend log dose anyone see something wrong?

---

### Post by majoridiot on 2007-01-21
yeah.. it's all bad.  but take note:

> **fatalfurry said:**
> QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recorded' is marked as crashed and should be repaired

you might search around and see if there's an easy fix for this... but you might have to drop
the database and start fresh.  try looking/asking at the mythtv forums:

[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/)

be sure to describe the problem and post that last log for quickest help.

---

### Post by superm1 on 2007-01-22
> **majoridiot said:**
> yeah.. it's all bad.  but take note:



you might search around and see if there's an easy fix for this... but you might have to drop
the database and start fresh.  try looking/asking at the mythtv forums:

[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/)

be sure to describe the problem and post that last log for quickest help.
Yuck.  Quite a ditto to majoridiot here.  Also check our your hardware, because a mysql database randomly going bad could always be an early indication of something bigger going wrong/about to go wrong.  Particularly check out ram and hard drive.

---

