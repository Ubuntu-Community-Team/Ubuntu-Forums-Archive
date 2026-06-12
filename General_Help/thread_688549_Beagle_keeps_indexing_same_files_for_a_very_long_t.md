---
title: "Beagle keeps indexing same files for a very long time"
date: 2008-02-05
forum: General Help
---

### Post by Maupertus on 2008-02-05
Beagle-helper is taking up almost 100% of my CPU on Gutsy.
When I run *beagle-info --status* I get the following output:

Debug: Done reading conf from /home/matthijs/.beagle/config/Daemon.xml
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
Scheduler:
Count: 182
Status: Executing task
Delayed 0 (2/5/2008 5:12:32 PM)
Indexing files inside /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk
Status: Indexing files inside /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk


Now, this didn't seem like a problem at first, but it must have been a week or longer since it started with indexing that folder and I've left my pc running a couple of nights, and still no improvement.

Does anybody have an idea what to do. I'm running beagle version 0.3.1

---

### Post by dbera on 2008-02-05
In one terminal do
$ tail -f ~/.beagle/Log/current-IndexHelper

In another terminal do
$ kill -USR2 <pidof beagled-helper>

This will print something in the first terminal. Copy that to a comment here. Also, paste the output of
$ tail -n50 ~/.beagle/Log/current-IndexHelper

If you have stopped beagle, then just do the last step.

Note that the text will contains names of the files that were indexed. If you dont wish to make them public for some reason, I can tell you explicitly how to further narrow down the particular file causing the problem.

(All of the above from the beagle wiki - troubleshooting page).

---

### Post by Maupertus on 2008-02-07
tail -f ~/.beagle/Log/current-IndexHelper
20080207 20:34:05.6057 06121 IndexH DEBUG: Helper Size: VmRSS=42.8 MB, size=2.44, 36.0%
20080207 21:03:45.8827 06121 IndexH DEBUG: No activity for 30.1 minutes, shutting down
20080207 21:03:45.8866 06121 IndexH  INFO: Shutdown requested
20080207 21:03:45.8920 06121 IndexH DEBUG: CancelIfBlocking Beagle.Daemon.UnixConnectionHandler
20080207 21:03:45.9198 06121 IndexH DEBUG: (1) Waiting for 2 workers...
20080207 21:03:45.9201 06121 IndexH DEBUG: waiting for HandleConnection (27)
20080207 21:03:45.9202 06121 IndexH DEBUG: waiting for server '/home/matthijs/.beagle/socket-helper'
20080207 21:03:45.9248 06121 IndexH DEBUG: Server '/home/matthijs/.beagle/socket-helper' shut down
20080207 21:03:45.9268 06121 IndexH DEBUG: (2) Waiting for 1 worker...
20080207 21:03:45.9270 06121 IndexH DEBUG: waiting for HandleConnection (27)

matthijs@matthijs:~$ kill -USR2 <pidof beagled-helper>
bash: syntax error near unexpected token `newline'
matthijs@matthijs:~$ tail -n50 ~/.beagle/Log/current-IndexHelper
20080207 20:33:26.4741 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_1.VOB
20080207 20:33:26.4750 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_2.VOB
20080207 20:33:26.4757 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_3.VOB
20080207 20:33:26.4764 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_4.VOB
20080207 20:33:26.4773 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VIDEO_TS.BUP
20080207 20:33:26.4782 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VIDEO_TS.IFO
20080207 20:33:26.4790 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VIDEO_TS.VOB
20080207 20:33:26.4797 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_01_0.BUP
20080207 20:33:26.4805 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_01_0.IFO
20080207 20:33:26.4813 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_01_0.VOB
20080207 20:33:26.4824 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_01_1.VOB
20080207 20:33:26.4831 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_02_0.BUP
20080207 20:33:26.4838 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_02_0.IFO
20080207 20:33:26.4845 06121 IndexH DEBUG: -file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_02_0.VOB
20080207 20:33:26.5372 06121 IndexH  WARN: Failed to execute child process "mplayer" (No such file or directory)
20080207 20:33:26.5377 06121 IndexH  WARN: Error in filtering /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_02_1.VOB with Beagle.Filters.FilterMPlayerVideo, falling back
20080207 20:33:27.3081 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_02_1.VOB
20080207 20:33:27.3232 06121 IndexH DEBUG: No filter for file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.BUP (/media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.BUP) [application/octet-stream]
20080207 20:33:27.3234 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.BUP
20080207 20:33:27.3592 06121 IndexH DEBUG: No filter for file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.IFO (/media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.IFO) [application/octet-stream]
20080207 20:33:27.3594 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.IFO
20080207 20:33:27.3792 06121 IndexH  WARN: Failed to execute child process "mplayer" (No such file or directory)
20080207 20:33:27.3796 06121 IndexH  WARN: Error in filtering /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.VOB with Beagle.Filters.FilterMPlayerVideo, falling back
20080207 20:33:27.3902 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_0.VOB
20080207 20:33:27.4173 06121 IndexH  WARN: Failed to execute child process "mplayer" (No such file or directory)
20080207 20:33:27.4178 06121 IndexH  WARN: Error in filtering /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_1.VOB with Beagle.Filters.FilterMPlayerVideo, falling back
20080207 20:33:27.7373 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_03_1.VOB
20080207 20:33:27.7542 06121 IndexH DEBUG: No filter for file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.BUP (/media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.BUP) [application/octet-stream]
20080207 20:33:27.7544 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.BUP
20080207 20:33:27.7650 06121 IndexH DEBUG: No filter for file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.IFO (/media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.IFO) [application/octet-stream]
20080207 20:33:27.7652 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.IFO
20080207 20:33:27.7837 06121 IndexH  WARN: Failed to execute child process "mplayer" (No such file or directory)
20080207 20:33:27.7841 06121 IndexH  WARN: Error in filtering /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.VOB with Beagle.Filters.FilterMPlayerVideo, falling back
20080207 20:33:27.8013 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_0.VOB
20080207 20:33:27.8243 06121 IndexH  WARN: Failed to execute child process "mplayer" (No such file or directory)
20080207 20:33:27.8247 06121 IndexH  WARN: Error in filtering /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_1.VOB with Beagle.Filters.FilterMPlayerVideo, falling back
20080207 20:33:27.9326 06121 IndexH DEBUG: Helper Size: VmRSS=42.2 MB, size=2.41, 35.1%
20080207 20:33:41.7949 06121 IndexH DEBUG: +file:///media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_1.VOB
20080207 20:33:41.8266 06121 IndexH  WARN: Failed to execute child process "mplayer" (No such file or directory)
20080207 20:33:41.8270 06121 IndexH  WARN: Error in filtering /media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/VTS_04_2.VOB with Beagle.Filters.FilterMPlayerVideo, falling back
20080207 20:34:05.6057 06121 IndexH DEBUG: Helper Size: VmRSS=42.8 MB, size=2.44, 36.0%
20080207 21:03:45.8827 06121 IndexH DEBUG: No activity for 30.1 minutes, shutting down
20080207 21:03:45.8866 06121 IndexH  INFO: Shutdown requested
20080207 21:03:45.8920 06121 IndexH DEBUG: CancelIfBlocking Beagle.Daemon.UnixConnectionHandler
20080207 21:03:45.9198 06121 IndexH DEBUG: (1) Waiting for 2 workers...
20080207 21:03:45.9201 06121 IndexH DEBUG: waiting for HandleConnection (27)
20080207 21:03:45.9202 06121 IndexH DEBUG: waiting for server '/home/matthijs/.beagle/socket-helper'
20080207 21:03:45.9248 06121 IndexH DEBUG: Server '/home/matthijs/.beagle/socket-helper' shut down
20080207 21:03:45.9268 06121 IndexH DEBUG: (2) Waiting for 1 worker...
20080207 21:03:45.9270 06121 IndexH DEBUG: waiting for HandleConnection (27)


Okay, so Beagle seems to have a problem indexing Les Triplettes, but I don't really get, why.

---

### Post by dbera on 2008-02-07
Because it requires mplayer to index those files.

It is still not clear the reason behind the CPU 100% problem, in fact the log file shows no such problem :-/

Do you have multiple beagled-helpers running ? Kill them (usnig the system monitor). You should really use 0.3.3, 0.3.1 and 0.3.2 has a problem with indexing multimedia files (it does not look like you faced that problem, but you might in the future).

Do this test,
$ cd "/media/sdb1/Film/The Triplettes of Bellville/The T of B - disk/"

Run beagle-extract-content for each file in that directory and see if any file is taking more than, say 2 minutes.

$ beagle-extact-content VTS_04_2.VOB
Do the above for each file; this might pinpoint which file beagled-helper is spending a lot of time on.

---

### Post by dbera on 2008-02-07
> **Maupertus said:**
> 
matthijs@matthijs:~$ kill -USR2 <pidof beagled-helper>
bash: syntax error near unexpected token `newline'


Ahh... when I wrote <pidof beagled-helper> I meant it to be substituted by the PID of the beagled-helper process. Use system monitor to find the pid of the beagled-helper process or install the package containing the program 'pidof' (then type "$pidof beagled-helper" to get the pid of the process).

In the future anytime you see beagled-helper taking lot of CPU for a long time, do the tail followed by the killof command and the tail terminal will print the name of the file which was currently being indexed.

---

### Post by Maupertus on 2008-02-08
Mmm, but I don't use mplayer, but that isn't a problem?

How can I upgrade to 0.3.3? It isn't in the rep's as I don't get an upgrade via sudo apt-get upgrade.

I'll post the output of the lines you gave me this midday.

Thanks!

---

### Post by dbera on 2008-02-08
If Mplayer is not found Totem is used. If that is not found, the video properties are not indexed. When you run the extract-content test, it might give some hint on what the problem is.

Where did you get 0.3.1 from ? AFAIK, it isnt in the gutsy repo either.

---

