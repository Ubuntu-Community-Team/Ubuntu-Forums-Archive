---
title: "DVArchive 3.2 fails to launch with &quot;internal error&quot;"
date: 2006-11-20
forum: General Help
---

### Post by srf21c on 2006-11-20
Having problems trying to run the latest version of DVArchive on my Edgy 6.10 system with Sun Java(TM) Runtime Environment (JRE) 5.0  1.5.0-08-0ubuntu1                    

After clicking yes to the license agreement, and selecting the default folder for DVarchive to store its files in, I get the following error.  This happens as both root and normal users.

---

### Post by jeremycobert on 2006-12-11
i get the same error, i also know that you need java 1.4 in order to run the dvarchive for linux.

---

### Post by srf21c on 2006-12-12
Hmm.  The dvarchive site clearly states that v3.2 "is compatible with JRE 1.5, 1.6 and later"   You think it's worth trying to roll back the JRE on my system to version 1.4?  Have you tried that as a troubleshooting step yet?

---

### Post by jeremycobert on 2006-12-21
> **srf21c said:**
> Hmm.  The dvarchive site clearly states that v3.2 "is compatible with JRE 1.5, 1.6 and later"   You think it's worth trying to roll back the JRE on my system to version 1.4?  Have you tried that as a troubleshooting step yet?

i was under the impression that 3.2 was only available for windows while 3.1 is available for linux and 3.1 requires java 1.4.2.

[http://www.dvarchive.org./DVArchive_Downloads.shtml](http://www.dvarchive.org./DVArchive_Downloads.shtml)

but im no expert. i have not got it to run on my ubuntu machine yet. i believe it requires root access, but ubuntu prevents root access.

---

### Post by srf21c on 2006-12-21
> **jeremycobert said:**
> i was under the impression that 3.2 was only available for windows while 3.1 is available for linux and 3.1 requires java 1.4.2.

[http://www.dvarchive.org./DVArchive_Downloads.shtml](http://www.dvarchive.org./DVArchive_Downloads.shtml)

but im no expert. i have not got it to run on my ubuntu machine yet. i believe it requires root access, but ubuntu prevents root access.

Good eye, after re-examining the DVArchive download page, I noticed that Linux/BSD/Solaris is not specifically mentioned in the v3.2 description.  However Mac OSX, which is BSD based, is mentioned.

This is counterintuitive, IMO.   I thought the whole point of writing applications in Java was so they could run on _any_ platform that had a suitable Java Runtime Environment installed.

Also, it's entirely possible to run DVArchive as root, just type in

```
sudo java -jar /path/DVArchive.jar
```

I think the next step is to try installing an older JRE and then using it to try and run DVArchive v3.1

---

### Post by srf21c on 2007-02-26
Well, I finally heard back from DVArchive author Gerry Duprey  re: my [related post HERE:]("http://www.planetreplay.com/phpBB2/viewtopic.php?t=13773")

 Unfortunately, he wasn't able to offer any help.   :confused:

---

### Post by cgreulich on 2007-06-20
I just installed DVArchive 3.2 on Ubuntu Feisty Fawn.  All I did was go to Add/Remove under Applications, searched for Java, found and installed the Sun Java 5.0 Runtime (sun-java5-bin), right clicked on the DVArchive .jar file and chose open with 'sun java 5.0 Runtime' and it runs with out problems.

Hope this helps.

---

### Post by BradMajors on 2007-06-27
> **cgreulich said:**
> I just installed DVArchive 3.2 on Ubuntu Feisty Fawn.  All I did was go to Add/Remove under Applications, searched for Java, found and installed the Sun Java 5.0 Runtime (sun-java5-bin), right clicked on the DVArchive .jar file and chose open with 'sun java 5.0 Runtime' and it runs with out problems.

Hope this helps.

I have done exactly what you have done (same versions of ubuntu, dvarchive, and java) , but I still get the same error message as listed at the beginning of the thread.

The following is my logfile:

****************************************************************************
06/27 02:43:40.0247 [0.479] Notice: DVArchive V3.2 starting
06/27 02:43:40.0248 [0.480] DEBUG: OS Linux 2.6.20-16-generic (i386), Java 1.5.0_11, Sun Microsystems Inc. (49.0)
06/27 02:43:40.0261 [0.493] DEBUG: Queued Threaded Task
06/27 02:43:40.0262 [0.494] DEBUG: Spawned new Thread 0, now 1 threads running
06/27 02:43:40.0272 [0.504] DEBUG: THREAD_0:: ReplayDevice Refresher -- engaged
06/27 02:43:40.0580 [0.812] DEBUG: SCHD_QUEUE:: Empty Schd Task Queue on restore
06/27 02:43:40.0581 [0.813] DEBUG: SCHD_QUEUE:: Schd Event Queue Marked CLEAN
06/27 02:43:40.0584 [0.816] DEBUG: Queued Threaded Task
06/27 02:43:40.0584 [0.816] DEBUG: Spawned new Thread 1, now 2 threads running
06/27 02:43:40.0584 [0.816] DEBUG: SCHD_JOB:: Added Job ID DOWNLOAD_LATER_JOB_ID
06/27 02:43:40.0587 [0.819] DEBUG: THREAD_1:: Job Scheduler -- engaged
06/27 02:43:40.0587 [0.819] DEBUG: SCHD_JOB:: Job Scheduler Starting
06/27 02:43:40.0587 [0.819] DEBUG: SCHD_JOB:: Sleeping for 60000 milliseconds
06/27 02:43:40.0623 [0.855] DEBUG: TVLISTING_SOURCE[0]:: New Listing Source being created
06/27 02:43:40.0623 [0.855] DEBUG: Queued Threaded Task
06/27 02:43:40.0623 [0.855] DEBUG: Spawned new Thread 2, now 3 threads running
06/27 02:43:40.0627 [0.859] DEBUG: THREAD_2:: Restore TV Guide Listings -- engaged
06/27 02:43:40.0627 [0.859] DEBUG: TVLISTING_SOURCE[0]:: No providers - returning no channels
06/27 02:43:40.0627 [0.859] DEBUG: TVGUIDE:: About to link shows for 0 channels
06/27 02:43:40.0627 [0.859] DEBUG: TVLISTING_SOURCE[0]:: No providers - returning no channels
06/27 02:43:40.0643 [0.875] DEBUG: TVGUIDE:: TV Show Linkage complete
06/27 02:43:40.0652 [0.884] DEBUG: BINDABLE:: There are network interfaces on this machine
06/27 02:43:40.0652 [0.884] DEBUG: BINDABLE:: Found Network Interface eth1
06/27 02:43:40.0652 [0.884] DEBUG: BINDABLE:: Detected Available Interface fe80:0:0:0:219:dbff:fe58:2e0c%3 on eth1
06/27 02:43:40.0656 [0.888] DEBUG: Queued Threaded Task
06/27 02:43:40.0656 [0.888] DEBUG: Spawned new Thread 3, now 4 threads running
06/27 02:43:40.0657 [0.889] DEBUG: BINDABLE:: Detected Available Interface 192.168.11.6 on eth1
06/27 02:43:40.0657 [0.889] DEBUG: BINDABLE:: Found Network Interface eth0
06/27 02:43:40.0657 [0.889] DEBUG: BINDABLE:: Detected Available Interface 169.254.7.57 on eth0
06/27 02:43:40.0657 [0.889] DEBUG: BINDABLE:: Found Network Interface lo
06/27 02:43:40.0657 [0.889] DEBUG: BINDABLE:: Detected Available Interface 0:0:0:0:0:0:0:1%1 on lo
06/27 02:43:40.0658 [0.890] DEBUG: BINDABLE:: Detected Available Interface 127.0.0.1 on lo
06/27 02:43:40.0658 [0.890] DEBUG: BINDABLE:: There are 5 network interfaces on this system
06/27 02:43:40.0663 [0.895] DEBUG: THREAD_2:: Restore TV Guide Listings -- Completed/Released
06/27 02:43:40.0663 [0.895] DEBUG: THREAD_2:: Periodic TV Listings Updater -- engaged
06/27 02:43:40.0663 [0.895] DEBUG: THREAD_3:: Idled
06/27 02:43:42.0423 [2.655] Notice: Agreed to DVArchive EULA
06/27 02:43:42.0467 [2.699] *Critical* Attempt to update U/I from non-U/I thread [
java.lang.Exception: Stack trace
	at java.lang.Thread.dumpStack(Thread.java:1158)
	at dvarchive.ReplayUI.Util.UIUtils.&#257;(UIUtils.java:27)
	at dvarchive.ReplayUI.Util.A.&#257;(FileUIUtils.java:31)
	at dvarchive.ReplayUI.Util.A.&#257;(FileUIUtils.java:24)
	at dvarchive.ReplayUI.Util.UIUtils.&#258;(UIUtils.java:125)
	at dvarchive.dvArchive.&#271;(dvArchive.java:378)
	at dvarchive.dvArchive.main(dvArchive.java:984)
06/27 02:43:44.0241 [4.474] DEBUG: ADD_PATH:: Path List Import now has 1 paths to scan
06/27 02:43:44.0242 [4.474] STORAGE:: Mounted storage path /home/brad/Import for Import
06/27 02:43:44.0242 [4.474] DEBUG: PATH_INFO[Import:/home/brad/Import]::      Checking to see if PATH is up to date
06/27 02:43:44.0243 [4.475] DEBUG: PATH_INFO[Import:/home/brad/Import]:: Refresh found potential changes on path /home/brad/Import -- checking files
06/27 02:43:44.0243 [4.475] DEBUG: PATH_INFO[Import:/home/brad/Import]::   Got 0 files in path, last modified at 1182448947000
06/27 02:43:44.0243 [4.475] DEBUG: PATH_INFO[Import:/home/brad/Import]:: Allocating new path file cache and populating it
06/27 02:43:44.0243 [4.475] DEBUG: Added import directory /home/brad/Import to Import Path Archive
06/27 02:43:44.0244 [4.476] DEBUG: ADD_PATH:: Path List PATHS now has 1 paths to scan
06/27 02:43:44.0244 [4.476] STORAGE:: Mounted storage path /home/brad/Local_Guide for PATHS
06/27 02:43:44.0244 [4.477] DEBUG: PATH_INFO[PATHS:/home/brad/Local_Guide]::      Checking to see if PATH is up to date
06/27 02:43:44.0245 [4.477] DEBUG: PATH_INFO[PATHS:/home/brad/Local_Guide]:: Refresh found potential changes on path /home/brad/Local_Guide -- checking files
06/27 02:43:44.0245 [4.477] DEBUG: PATH_INFO[PATHS:/home/brad/Local_Guide]::   Got 0 files in path, last modified at 1182448947000
06/27 02:43:44.0245 [4.477] DEBUG: PATH_INFO[PATHS:/home/brad/Local_Guide]:: Allocating new path file cache and populating it
06/27 02:43:44.0245 [4.477] DEBUG: Added guide directory /home/brad/Local_Guide to Guide Path Archive PATHS
06/27 02:43:44.0246 [4.478] DEBUG: PATH_INFO[PATHS:/home/brad/Local_Guide]:: Saving path off as [/home/brad/Local_Guide]
06/27 02:43:44.0247 [4.479] DEBUG: PATH_INFO[Import:/home/brad/Import]:: Saving path off as [/home/brad/Import]
06/27 02:43:44.0253 [4.485] Notice: No existing Local Guide found -- Creating new, empty Local guide
06/27 02:43:44.0260 [4.492] DEBUG: Queued Threaded Task
06/27 02:43:44.0282 [4.514] DEBUG: THREAD_3:: Local Guide Path Refresher -- engaged
06/27 02:43:44.0283 [4.515] DEBUG: PATH_MGR:: About to mount all paths
06/27 02:43:44.0283 [4.515] DEBUG: PATH_MGR:: 2 paths to mount
06/27 02:43:44.0283 [4.515] DEBUG: PATH_MGR:: About to mount all paths (Count=1) in path list #0, Import
06/27 02:43:44.0283 [4.515] DEBUG: PATH_MGR:: About to mount all paths (Count=1) in path list #1, PATHS
06/27 02:43:44.0283 [4.516] DEBUG: PATH_MGR:: All Path lists mounted -- now refreshing path cache lists
06/27 02:43:44.0284 [4.516] DEBUG: PATH_MGR:: About to refresh all paths
06/27 02:43:44.0284 [4.516] DEBUG: PATH_MGR:: Found 2 path lists to refresh
06/27 02:43:44.0284 [4.516] DEBUG: PATH_MGR:: Refreshing Path List #0, Import
06/27 02:43:44.0284 [4.516] DEBUG: PATH_MGR:: Refreshing Path List #1, PATHS
06/27 02:43:44.0284 [4.517] DEBUG: PATH_LIST::[PATHS] Amount to refresh cached files in this path list
06/27 02:43:44.0285 [4.517] DEBUG: PATH_LIST::[PATHS] 1 paths to refresh
06/27 02:43:44.0285 [4.517] DEBUG: PATH_LIST::[PATHS] About to refresh path #0, /home/brad/Local_Guide
06/27 02:43:44.0285 [4.517] DEBUG: PATH_INFO[PATHS:/home/brad/Local_Guide]::      Checking to see if PATH is up to date
06/27 02:43:44.0285 [4.517] DEBUG: PATH_INFO[PATHS:/home/brad/Local_Guide]::     PATH is UP TO DATE
06/27 02:43:44.0286 [4.518] DEBUG: PATH_LIST::[PATHS]      Path Refreshed
06/27 02:43:44.0286 [4.518] DEBUG: PATH_LIST::[PATHS] All Path Lists refreshed
06/27 02:43:44.0286 [4.518] DEBUG: PATH_MGR::     Path List Refreshed
06/27 02:43:44.0287 [4.519] DEBUG: Queued Threaded Task
06/27 02:43:44.0287 [4.519] DEBUG: Spawned new Thread 4, now 5 threads running
06/27 02:43:44.0289 [4.521] DEBUG: THREAD_4:: UPnP Message Dispatcher -- engaged
06/27 02:43:44.0289 [4.521] DEBUG: Queued Threaded Task
06/27 02:43:44.0290 [4.522] DEBUG: Spawned new Thread 5, now 6 threads running
06/27 02:43:44.0290 [4.522] DEBUG: THREAD_5:: Device Recognition Handler -- engaged
06/27 02:43:44.0297 [4.530] ERROR: BINDABLE:: Unable to parse passed dotted quad IPV4 address [] -- Wrong number of quads!
java.lang.Exception: Stack trace
	at java.lang.Thread.dumpStack(Thread.java:1158)
	at dvarchive.B.A.&#257;(BindableServerAddress.java:67)
	at dvarchive.B.H.&#257;(ReplayServer.java:260)
	at dvarchive.dvArchive.&#271;(dvArchive.java:409)
	at dvarchive.dvArchive.main(dvArchive.java:984)
DVArchive failed to start user interface -- null
java.lang.NullPointerException
	at java.util.StringTokenizer.<init>(StringTokenizer.java:182)
	at java.util.StringTokenizer.<init>(StringTokenizer.java:204)
	at dvarchive.B.A.&#257;(BindableServerAddress.java:53)
	at dvarchive.B.H.&#257;(ReplayServer.java:233)
	at dvarchive.B.H.&#257;(ReplayServer.java:263)
	at dvarchive.dvArchive.&#271;(dvArchive.java:409)
	at dvarchive.dvArchive.main(dvArchive.java:984)

---

### Post by AzureCerulean on 2007-11-09
came across this in another forum:

"gjarboni
Just looking around
Just looking around


Joined: 07 Dec 2007
Posts: 2

	
PostPosted: Fri Dec 07, 2007 4:11 am    Post subject: Ubuntu solution to running ReplayTV 	Reply with quote
Hello,

I had this problem running Gutsy and there was an easy solution. DVArchive (or something inside Java) was trying to do a DNS lookup on my hostname not the FQDM. So I edited /etc/hosts to add a record pointing my hostname to 127.0.0.1 and now DVArchive works. Confused? Here's an example:

/etc/hosts before:
-----------------------

127.0.0.1 localhost
127.0.1.1 hostname.domainname.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hosts after:
----------------------

127.0.0.1 localhost
127.0.1.1 hostname.domainname.com hostname

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


The second line is the one that's changed. So just add your hostname to the end of that line and you should be set.

Jason M."

Thanks to Jason M.  for this solution.

My machines name is et833ua  so i added the line

127.0.0.1  et833ua  

saved and closed and DVArchive loaded up perfectly.

---

### Post by steveh1 on 2007-11-30
> **AzureCerulean said:**
> not sure why...sorry i wish i could help more.. I have 2 machines with dvarchive on both. Both are running gutsy.  dvarchive worked on one but not the other i got the same errors..

DVArchive failed to start user interface -- null
java.lang.NullPointerException
at java.util.StringTokenizer.<init>(StringTokenizer.j ava:182)
at java.util.StringTokenizer.<init>(StringTokenizer.j ava:204)
at dvarchive.B.A.&#257;(BindableServerAddress.java:53)
at dvarchive.B.H.&#257;(ReplayServer.java:233)
at dvarchive.B.H.&#257;(ReplayServer.java:263)
at dvarchive.dvArchive.&#271;(dvArchive.java:40

since DVArchive failed to start user interface I though I could attempt to login and run dvarchive from the working machine via ssh over my local network to see if was something on the unworking machine that kept it from rendering; if it loaded then there wasn't anything doing so.  

It loaded and ran.  I closed it and then attempted to start dvarchive locally again to review the error, and it loaded perfectly.

not sure if this helps anyone, as i said i have no explaination, perhaps this will help someone to explain why.

I do not have a second system to try this with (other than the DVArchive on a Vista box) and I am also getting:

sudo java -jar Desktop/DVArchive/DVArchive.jar 
DVArchive failed to start user interface -- null
java.lang.NullPointerException
        at java.util.StringTokenizer.<init>(StringTokenizer.java:182)
        at java.util.StringTokenizer.<init>(StringTokenizer.java:204)
        at dvarchive.B.A.&#257;(BindableServerAddress.java:53)
        at dvarchive.B.H.&#257;(ReplayServer.java:233)
        at dvarchive.B.H.&#257;(ReplayServer.java:263)
        at dvarchive.dvArchive.&#271;(dvArchive.java:409)
        at dvarchive.dvArchive.main(dvArchive.java:984)

I have loaded Java 6, and a version of JRE newer than 1.4...

Any thoughts??

TIA,
  Steve

---

### Post by doncook7 on 2008-02-27
Thanks AzureCerulean!  

That worked like a charm!  I've been trying for 2 days to get this working.

DVArchive 3.2
JRE 5

don

---

