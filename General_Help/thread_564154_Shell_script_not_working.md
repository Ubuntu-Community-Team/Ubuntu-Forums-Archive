---
title: "Shell script not working?"
date: 2007-09-30
forum: General Help
---

### Post by william_hunter on 2007-09-30
Hey folks. I have had to reinstall due to a serious HDD failure, and I decided to go with Feisty server for various reasons. Before I did this, I made backups of the things I wanted to save most of all: my forum, website for my students, and a NWN gameserver I host. Here is my problem:

I run the game server application using a shell script that checks to make sure the game server reboots in the event of a crash (happens sometimes, but not too often, thankfully). This script was working nicely before I re-installed, and now it won't work. Can anyone here think of a reason for this? Here is the script:

> 
#!/bin/bash
while [ true ]
do
export LD_PRELOAD=./nwnx2.so
./nwserver -module "Tharagon08212007" -dmpassword xxxxx -maxclients 40 -minlevel 1 -maxlevel 40  -difficulty 4 -elc 0 -ilr 0 -port 5121 -gametype 3
sleep 5
done
unset LD_PRELOAD 


thanks!

---

### Post by HermanAB on 2007-09-30
Well, execute these two lines one by one and see what it tells you:
export LD_PRELOAD=./nwnx2.so
./nwserver -module "Tharagon08212007" -dmpassword xxxxx -maxclients 40 -minlevel 1 -maxlevel 40 -difficulty 4 -elc 0 -ilr 0 -port 5121 -gametype 3

It should be fairly obvious - most probably a missing file or a bad path.

Cheers,

Herman

---

### Post by william_hunter on 2007-10-01
Sorry, I should have been more clear. It fires the server as it should, but it does not restart it in the event of a crash as it was before I changed to the new OS. I did move the entire contents of the server's directory to a new HDD in the process, but everything else seems to be working fine. It just does not seem to be working in regards to the restart of the server process when the program crashes.

---

### Post by william_hunter on 2007-10-15
Could this issue be related to moving the files to a new directory? I really dont understand whats going on, so I am grasping at straws here.

---

