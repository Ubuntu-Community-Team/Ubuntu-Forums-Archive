---
title: "script to automatically kill telnet sessions"
date: 2013-03-20
forum: General Help
---

### Post by bxdobs on 2013-03-20
I use the attached script to automatically remove all my telnet sessions from an AIX machine

2 issues that I am trying to resolve in UBUNTU

1) Ubuntu won't run this script because kill needs to be run under sudo ... is there any way around this?

2) because system processes are also running under the MyUserName, kill -1 -9, would be a BAD thing to run
    
doing a ps -ef | grep telnetd shows the PID's of the sessions I want to terminate 

telnetd   6754  1094  0 17:03 ?        00:00:00 in.telnetd: Machine.local 
telnetd   6757  1094  0 17:03 ?        00:00:00 in.telnetd: Machine.local

looking for a way to automatically kill both of these Machine.local sessions without touching anything else that is running

is there some way to direct an exit to run in each telnet session

-------------------------
UserName=MyUserName
rusure=N

for CurrentUser in `whoami`; do
  echo " "
done

if [ "$UserName" = "$CurrentUser" ]
then 
   read rusure?'Are you sure you want to exit all processes? (y/n)' 

   if [ "$rusure" = "Y" ] || [ "$rusure" = "y" ]
   then
      echo Exit in progress from $CurrentUser
      sleep 1
      nohup kill -9 -1 > /dev/null
   fi
else
   echo ---  You cannot exit the system using this script from $CurrentUser ----

fi
-----------------------------------------------------------------

---

### Post by Cheesemill on 2013-03-20
How about...
```
 pkill telnetd
```

If any of the telnet processes are run by other users, then you may need to do...
```
 sudo pkill telnetd
```
to kill all of the active telnetd sessions.

---

### Post by bxdobs on 2013-03-20
Thanx Cheesemill

Bash also apparently doesn't like the AIX read syntax either so the final script is now:

-------------------------
#!/bin/sh

UserName=MyUserName
rusure=N

for CurrentUser in `whoami`; do
   echo " "
done

if [ "$UserName" = "$CurrentUser" ]
then 
   read -p 'Are you sure you want to exit all processes? (y/n) ' rusure 

   if [ "$rusure" = "Y" ] || [ "$rusure" = "y" ]
   then
       echo Exit in progress from $CurrentUser
       sleep 1
       nohup sudo pkill telnetd < /home/MyUserName/bin/pk.txt
   fi
else
    echo --- You cannot exit the system using this script from $CurrentUser ----
fi
-----------------------------------------------------------------

---

