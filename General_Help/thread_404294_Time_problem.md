---
title: "Time problem"
date: 2007-04-08
forum: General Help
---

### Post by andyman3000 on 2007-04-08
Hi everyone,

after googleing, searching this forum and searching everything other resource I could think of for about 4 hours now, I am hoping someone might have an answer to my problem which is totally driving me nutts:

I am using Ubuntu 6.10 and I am having problems with my server time (times?). 
I first noticed the bug, when my a php framework i am testing, symfony, created some files on the server (via php cli). The time of the created files was wrong, they were all one hour ahead of the actual server time, which is correct. I am usually on GMT+1 and the system time is fine ( I synced it again as well). I could not find anything on different server times, except for a small note to set a timezone setting in each php.ini which I did - no change!

Today I created a new subversion project and checked out a bunch of files. All these files are one hour ahead as well. Has anyone experienced similar problems? Is there a way to change this? Is there something like a "second internal time"? Where would this be hidden?
Using the php date()-Function on my webserver returns the correct time, so it cannot be a php issue (as is proved by the svn problem as well).

Please help, I am so fed up with this. thanks in advance.

Cheers, Andy

---

### Post by andyman3000 on 2007-04-08
Well, how shall I put it.... I am pretty stupid!!!!

After rechecking everything on the command line instead of my preferred application to transfer files from windows to my ubuntu machne - winScp - everything looked fine. So the problem was not a problem with my Ubuntu server after all. It was a problem with Win SCP.

So, if anyone should ever experience something similar, check your WinScp connection settings. There is a setting in the "expert mode" which lets you set a server time offset. I do still not know, why winSCP displayed a wrong time for all of the files that were created by appications on the server,as the offset was set to "0", but after setting the time offset to -1 hours everything is working fine.

Ouch....

---

