---
title: "How can i run a on screen script before the login prompt?"
date: 2014-04-23
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-04-23
I am looking at re-purposing some old hardware
i want it to boot to a script instead of the login screen
this is the script i want it to boot to (just made this)
```
#!/bin/sh
file="/tmp/startTime"
here=$(/sbin/ifconfig eth0 | awk -F':' '/inet addr/{split($2,_," ");print _[1]}')
while [ ! -f "$file" ];do
        clear
        echo "Waiting for Start Time"
        echo "Please visit http://$here to set"
        sleep 0.25
done
startTime=$(cat "$file")
while [ $(($startTime+1)) -gt $(date +%s) ];do
        clear
        i=$(( $startTime - $(date +%s) ))
        figlet -t -f banner $(echo $(date -u -d @$i +"%T")|sed 's/:/ : /g')
        sleep 0.12
        startTime=$(cat "$file") # in-case start time is changed
done
clear
i=0
while [ $i -lt 60 ];do
        figlet -t -f banner "00 : 00 : 00"
        sleep 0.5
        clear
        sleep 0.5
        i=$(($i+1))
done
rm $file
$(dirname $0)/$(basename $0)
```

---

### Post by pqwoerituytrueiwoq on 2014-04-23
So i figured out i need to save it to [FONT=courier new]/etc/init.d/timer[/FONT]
but i don't know the correct numbers for the [FONT=courier new]update-rc.d[/FONT] command
it needs to start after apache2 and sshd have started

---

