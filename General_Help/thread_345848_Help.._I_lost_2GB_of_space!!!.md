---
title: "Help.. I lost 2GB of space!!!"
date: 2007-01-24
forum: General Help
---

### Post by azazel00 on 2007-01-24
Hello, 

I have my linux configured with a 10GB partition. Out of those, I had almost 8GB in use. 

A couple of minutes ago I installed and used 'recordmydesktop' to make a video of my beryl environment. I didnt know the video would grow so fast. Anyway, I stopped the video recording and It processed until it got to 77% then stoped (I assume it was because it had no more space).

Long story short, I'm now missing over 2GBs of drive space. I tried searching for the default file name, but that doesnt work.. search comes empty.

How can I find out where the drivespace is? Anyway way to query the filesystem for files over a certain amount? I tried the "Find Files.." util, but no luck.

Regards,
az

---

### Post by gaebriel on 2007-01-24
If it's one big file it should be easy to find - you can type the following in a terminal window: 

find / -size +500M -ls 

That will find files larger than 500M and list their full path and details. 

If it's a bunch of small files and you know when they were modified, you can use: 

find / -mtime -1 

That will find files modified within the last day. Change the -1 to -2 for two days, -3 for 3 days ....

Check out [http://www.onlamp.com/pub/a/bsd/2002/02/21/FreeBSD_Basics.html?page=2]("http://www.onlamp.com/pub/a/bsd/2002/02/21/FreeBSD_Basics.html?page=2")
and the man page "man find" and you'll get all the details you need for finding files on a unix system. 

Enjoy!

---

### Post by iovar on 2007-01-25
The temporary files are stored in the /tmp directory in a subdirectory named 
rMD-session-xxxx where xxxx is the pid of recordMyDesktop.

You can remove any leftovers with 
~$ rm -rf /tmp/rMD-session-*

---

### Post by azazel00 on 2007-01-26
Thanks, I managed to solve the problem.

Regards,
az

---

