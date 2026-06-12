---
title: "MythTV: mythfilldatabase, no channels problem"
date: 2006-10-02
forum: General Help
---

### Post by firefly2442 on 2006-10-02
Hello.  I've just gotten through installing MythTV 0.20 from source on Ubuntu Dapper 6.06.  When I run mythtv-setup, I can choose my pcHDTV 3000 card running NTSC (non-HD).  I can also get my lineup from my zap2it account.  However, there doesn't seem to be any channel data.  When I run mythfilldatabase I get this:

```
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [                              <=>    ] 246,507       25.60K/s

15:45:52 (20.35 KB/s) - `-' saved [246507]

2006-10-02 15:45:52.381 DataDirect: Your subscription expires on 12/01/2006 11:48:13 PM
2006-10-02 15:46:01.614 Grab complete.  Actual data from Fri Oct 13 00:00:00 2006 to Sat Oct 14 23:59:59 2006 (UTC)
2006-10-02 15:46:01.615 Main temp tables populated.
2006-10-02 15:46:01.624 Did not find any new program data.
2006-10-02 15:46:01.628 New DB connection, total: 4
2006-10-02 15:46:01.628 Connected to database 'mythconverg' at host: localhost
2006-10-02 15:46:01.630 New DB connection, total: 5
2006-10-02 15:46:01.630 Connected to database 'mythconverg' at host: localhost
2006-10-02 15:46:01.631 Failed to fetch some program info
2006-10-02 15:46:01.632 Adjusting program database end times.
2006-10-02 15:46:01.632     0 replacements made
2006-10-02 15:46:01.632 Marking generic episodes.
2006-10-02 15:46:01.633     Found 0
2006-10-02 15:46:01.633 Marking repeats.
2006-10-02 15:46:01.634     Found 0
2006-10-02 15:46:01.661 Unmarking new episode rebroadcast repeats.
2006-10-02 15:46:01.661     Found 0
2006-10-02 15:46:01.661 Marking episode first showings.
2006-10-02 15:46:01.662     Found 0
2006-10-02 15:46:01.662 Marking episode last showings.
2006-10-02 15:46:01.662     Found 0
2006-10-02 15:46:01.663 Grabbing next suggested grabbing time
2006-10-02 15:46:02.038 DataDirect: BlockedTime is: 2006-10-02T15:38:37
2006-10-02 15:46:02.038 DataDirect: NextSuggestedTime is: 2006-10-03T21:09:52
2006-10-02 15:46:02.040
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2006-10-02 15:46:02.043 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-10-02 15:46:02.045 Using protocol version 30
2006-10-02 15:46:02.048 mythfilldatabase run complete.
```

It seems to be downloading something from their servers but then nothing is actually updated or inserted in the MySQL database.

Any ideas?  Thanks! :)

---

### Post by tagra123 on 2006-10-03
> **firefly2442 said:**
> Hello.  I've just gotten through installing MythTV 0.20 from source on Ubuntu Dapper 6.06.  When I run mythtv-setup, I can choose my pcHDTV 3000 card running NTSC (non-HD).  I can also get my lineup from my zap2it account.  However, there doesn't seem to be any channel data.  When I run mythfilldatabase I get this:

```
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [                              <=>    ] 246,507       25.60K/s

15:45:52 (20.35 KB/s) - `-' saved [246507]

2006-10-02 15:45:52.381 DataDirect: Your subscription expires on 12/01/2006 11:48:13 PM
2006-10-02 15:46:01.614 Grab complete.  Actual data from Fri Oct 13 00:00:00 2006 to Sat Oct 14 23:59:59 2006 (UTC)
2006-10-02 15:46:01.615 Main temp tables populated.
2006-10-02 15:46:01.624 Did not find any new program data.
2006-10-02 15:46:01.628 New DB connection, total: 4
2006-10-02 15:46:01.628 Connected to database 'mythconverg' at host: localhost
2006-10-02 15:46:01.630 New DB connection, total: 5
2006-10-02 15:46:01.630 Connected to database 'mythconverg' at host: localhost
2006-10-02 15:46:01.631 Failed to fetch some program info
2006-10-02 15:46:01.632 Adjusting program database end times.
2006-10-02 15:46:01.632     0 replacements made
2006-10-02 15:46:01.632 Marking generic episodes.
2006-10-02 15:46:01.633     Found 0
2006-10-02 15:46:01.633 Marking repeats.
2006-10-02 15:46:01.634     Found 0
2006-10-02 15:46:01.661 Unmarking new episode rebroadcast repeats.
2006-10-02 15:46:01.661     Found 0
2006-10-02 15:46:01.661 Marking episode first showings.
2006-10-02 15:46:01.662     Found 0
2006-10-02 15:46:01.662 Marking episode last showings.
2006-10-02 15:46:01.662     Found 0
2006-10-02 15:46:01.663 Grabbing next suggested grabbing time
2006-10-02 15:46:02.038 DataDirect: BlockedTime is: 2006-10-02T15:38:37
2006-10-02 15:46:02.038 DataDirect: NextSuggestedTime is: 2006-10-03T21:09:52
2006-10-02 15:46:02.040
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2006-10-02 15:46:02.043 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-10-02 15:46:02.045 Using protocol version 30
2006-10-02 15:46:02.048 mythfilldatabase run complete.
```

It seems to be downloading something from their servers but then nothing is actually updated or inserted in the MySQL database.

Any ideas?  Thanks! :)

Did you already set up the channels at datadirect. mythfilldatabase looks like it is working fine, but is basically downloading "blank information". Also try it a couple of times and see if it loads the data.

---

### Post by Titus A Duxass on 2006-10-03
What command are you using to fill the database - mythfilldatabase or mythfilldatabase - manual.

---

### Post by firefly2442 on 2006-10-03
I'm just going to the terminal command prompt and typing in "mythfilldatabase".  Are there more command arguments that I need to be specifying?

Yep, I already setup my channels on zap2it.  I added basic cable and then removed some that I won't be watching.  Should I try recreating the MySQL database maybe?  It seems to already be populated with tables, however, there's nothing in the channels table....

Thanks. :)

---

### Post by tagra123 on 2006-10-03
Try setting the channel lineup in mythtv-setup

Click on video sources

choose your video source

a message should display "Fetching Lineups" 

Next make sure XMLTV listing grabber is set to North America (DataDirect) which I think you already have done correctly.

Your user and password for zaptit are obviously correct.

CLICK ON retrieve lineup

Do you see your listings (Cily zipcode, cable provider, or something similar) in Data Direct Lineup. If not select your lineup.

Finish

Next

Click on Channel editor --  Select All Sources -- Do you see your channels?

Escape out of this menu.

Click on capture card settings,  Does the default input match the device you are getting you channels form -- ie composite for av cable box connection, or tuner.

Close the setup.

Now run mythfilldatabase.

Then start mythfrontend when its finished and see if your channels are displaying.

I just googled and this link may also be helpful.

[http://www.mythtvtalk.com/forum/archive/o_t/t_375/mythtv_ver_0.16_mythfilldatabase_not_filling_database.html](http://www.mythtvtalk.com/forum/archive/o_t/t_375/mythtv_ver_0.16_mythfilldatabase_not_filling_database.html)

---

### Post by firefly2442 on 2006-10-04
Hello.  Here's what I tried.  I deleted the mythtv database and recreated it and ran through mythtv-setup again.  I added my capture card and then went in and did all the settings again.  I can retrieve my lineup and see my zipcode and state and so on.  It's certainly getting this correct.  I tried running the get channels from data but it doesn't grab anything.  And then when I go into the channel editor, nothing shows up.  Could it maybe be whatever program is getting the TV data isn't formatting it properly for the database?  Maybe I need a newer version?  Thanks for the help. :)

---

### Post by tagra123 on 2006-10-04
Its been a long time since I originally set up my system, It still sounds like you haven't set the channel lineup (channels ) in mythtv.

You could try installing phpmyadmin and actually looking at the database using it to see if the database has channel infor in  it. 

Also have you tried 

sudo mythfilldatabase

---

### Post by firefly2442 on 2006-10-05
I looked in the database and the channels table is empty.  I tried sudo mythfilldatabase but got the same results.  Hmm, I'll keep searching online.  Maybe someone on IRC has some ideas...

Thanks. :)

---

### Post by tagra123 on 2006-10-05
> **firefly2442 said:**
> I looked in the database and the channels table is empty.  I tried sudo mythfilldatabase but got the same results.  Hmm, I'll keep searching online.  Maybe someone on IRC has some ideas...

Thanks. :)

See this link. Sounds like they had the exact same problem and got it to work.

[http://ubuntuforums.org/showpost.php?p=612546&postcount=16](http://ubuntuforums.org/showpost.php?p=612546&postcount=16)

The system is great once you get it working. 

By the way one you get once portion working, its a good idea to make a backup using partimage before proceeding to the next step  in case something gets nuked along the way,

---

### Post by firefly2442 on 2006-10-07
I got it working!  After asking on the IRC forums, a very helpful person on there suggested I try running this:

 mythfilldatabase --do-channel-updates

So... for anyone else with this same issue, try that command.  Thanks for the help Tagra123!

---

### Post by tagra123 on 2006-10-10
No problem. My problem was getting a homemade irblaster to change channels on an unsupported cablebox. I ended up setting up a receiver and using the remote, using windows to record the remote codes and then adding them to the setup file for myth.

---

