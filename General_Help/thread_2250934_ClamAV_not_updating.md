---
title: "ClamAV not updating"
date: 2014-10-31
forum: General Help
---

### Post by Acharn on 2014-10-31
I'm trying to scan my Windows machine using a livecd. All the howto pages on doing this seem to be outdated. Avast and AVG do not seem to have Linux versions any more. clamtk does not seem to update its database, but an outdated database is better than nothing.

I tinkered around trying to get clamtk to update its database and then ran a scan on my windows directory. The partition is 330 GB, so it took a couple of hours. When it was finished I had a window saying it had scanned more than 200,000 files and had found a little over 2,000 threats. At this point I don't know what to do. It appears that I need to select each threat, evaluate it, and try to figure out whether to quarantine it, delete it, or do nothing. Evaluating over 2,000 items one at a time is going to take a long time. Is there a faster solution?

---

### Post by Acharn on 2014-10-31
Not sure if this should be in the Security forum, but this is where I usually come.

I want to use an Ubuntu livecd to clean a virus out of my Windows box, so I installed ClamTK. It seems to be the only anti-virus which still has Linux support. Anyway, I first installed from the Ubuntu Software Center. When I tried to update the virus database it said that it had downloaded and installed the db, but when I went back to the main window it still showed "virus database out of date." I tried several times, including running "sudo freshclam" from a terminal. No joy. Next I went to their homepage and found the latest version and installed it. Same thing. Click "update" and it runs for a while then comes back to "update available." Sometimes it claims to have been successful, but when I go back to the home window it's still showing the old db date. Sometimes when I run freshclam in reports success, and then when I start ClamTK up it shows the old date. Here's what I' gotten a number of times:

> ubuntu@ubuntu:~$ sudo freshclam
ClamAV update process started at Sat Nov  1 10:27:30 2014
WARNING: Can't query current.cvd.clamav.net
WARNING: Invalid DNS reply. Falling back to HTTP mode.
Reading CVD header (main.cvd): OK
main.cvd is up to date (version: 55, sigs: 2424225, f-level: 60, builder: neo)
Reading CVD header (daily.cvd): OK (IMS)
daily.cvd is up to date (version: 19528, sigs: 1219606, f-level: 63, builder: neo)
Reading CVD header (bytecode.cvd): OK
bytecode.cvd is up to date (version: 242, sigs: 46, f-level: 63, builder: dgoddard)
[LibClamAV] **************************************************
[LibClamAV] ***  The virus database is older than 7 days!  ***
[LibClamAV] ***   Please update it as soon as possible.    ***
[LibClamAV] **************************************************
ubuntu@ubuntu:~$ 


Any suggestions?

---

### Post by cariboo on 2014-11-01
Please don't create multiple threads on the same subject, I have merged tour two threads.

---

### Post by Acharn on 2014-11-01
Oh, thank you. I didn't remember posting the first thread. Guess I didn't get enough sleep last night.

---

