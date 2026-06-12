---
title: "MythTV (and IVTV?) Issues"
date: 2006-08-01
forum: General Help
---

### Post by batkins on 2006-08-01
I'm trying to set up MythTV with my Hauppauge PVR-150, but I'm having a couple of problems:

1.  If I connect the output jack of my satellite set-top box to the input of my tuner card, I'd expect to be able to tune to channel 3 on my machine and watch TV from the satellite.  This doesn't work - every channel I tune to is static.  I've tried this from within MythTV and also by manually tuning the IVTV drivers to 3 and then mplaying /dev/video0 .

2.  I'd like to be able to play my PlayStation2 through my tuner card (one of the reasons I bought the tuner card was to eliminate the space my TV takes up).  If I plug my playstation into the composite inputs and select them as an input, this works.  However, there's one fairly large problem - a five-second lag between pressing a button and seeing a reaction.  Obviously, this is no way to play a game.  Does this have something to do with the time it takes my card to encode MPEG's, and if so, how can I turn that off?

3.  The mythfilldatabase command fails spectacularly for me.  It downloads the files without any issue, but then the terminal is flooded with messages like this:

DB Error (Inserting into dd_schedule):
Query was:
INSERT INTO dd_schedule (programid,stationid,scheduletime,duration,repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtime) VALUES('SH7400760000','46172','2006-08-02T00:00:00','01:00:00',0,0,0,0,0,NULL,0,0,'2006-08-02T01:00:00');
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,parttotal,endtim' at line 1


Any help would be appreciated.

Software: MythTV 0.18.1, IVTV 0.4.6, Linux 2.6.15-686
Hardware: Hauppauge PVR-150
Input: DirecTV satellite

Thanks,
Bill

---

