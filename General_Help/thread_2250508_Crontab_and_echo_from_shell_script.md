---
title: "Crontab and echo from shell script"
date: 2014-10-29
forum: General Help
---

### Post by rob104 on 2014-10-29
Hi there. I've got some basic shell script that works fine when called like ./script.sh (i'm logged in like root), but when i try to call it via crontab like this - 0 1 * * * /home/dev/script.sh & i am not seeing any output from script, what am i missing? Script looks like this (checks if wlan is connected on my raspberry):

```
#!/bin/bash                                  
                                               
TESTIP=google.com                           
                                               
ping -c4 ${TESTIP} > /dev/null               
                                               
if [ $? != 0 ]                               
then                                         
    sudo echo "WIFI down, restarting"
    ifdown --force wlan0                     
    ifup wlan0                               
else                                        
    sudo echo "WIFI up"          
fi       
   sudo echo "EXIT"
```

---

### Post by steeldriver on 2014-10-29
Where do you expect to see this output? cron jobs are not run in a terminal - you will need to redirect the echo commands' output to a file and then look at that

BTW why are you using sudo?

---

