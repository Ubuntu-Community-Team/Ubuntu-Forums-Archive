---
title: "CRASH: Lotus Notes - installed, worked; rebooted, crash"
date: 2007-07-17
forum: General Help
---

### Post by j0rd4n on 2007-07-17
I followed the HOWTO for the Lotus Notes setup, and after combining a few methods mentioned, it worked. I was thrilled. I ran through the configuration and it all worked great. Now, when I run the application, I get the following (ran via terminal with debugging stuff turned on for nsd.sh):

notes: LD_LIBRARY_PATH = /home/jrecknag/notes:/home/jrecknag/notes/jvm/bin/classic:/home/jrecknag/notes/jvm/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/j9vm:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/jrecknag/notes:/home/jrecknag/notes/jvm/bin/classic:/home/jrecknag/notes/jvm/bin:/usr/../usr/lib/xulrunner

07/17/2007 11:49:39 AM  Lotus Notes client started
Stack base = 0xbfc597fc, Stack size = 6348 bytes 
Fatal Error signal = 0x0000000b PID/TID = 11659/-1269053760 
7/17/2007 11:49:40  Running NSD
GetACP returns 1252
7/17/2007 11:49:51  Termination is in progress
7/17/2007 11:49:51  Terminating tasks
setPreload():libraryDirPath:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/
nsdexec: notespid = 11659
7/17/2007 11:50:01  Freeing resources
7/17/2007 11:50:01  Termination completed

************************************

I have the notes error log (600+k), but I can't get anything out of that. I can't find any other relevant posts on this topic, so I was wondering if anyone could help me interpret this error?

---

