---
title: "Get the Port in Use by PID for Shell Script"
date: 2012-12-24
forum: General Help
---

### Post by own3mall on 2012-12-24
Is there a way to get the port in use by a process?  I've got the PIDs, and I just want the port number that each process is using returned.  So far, I've got:  

```

#!/bin/bash

# Get PIDs of everything running ET
PIDs=`sudo ps -ef | grep etded | awk '{print $2}'`

# Place PIDs into an array
arr=$(echo $PIDs | tr "\n" "\n")

# Foreach ID, check the port, kill the process if it's not 27960
for x in $arr
do
    echo "> [$x]"
done


```

So far, people are identifying the processes based on the port, but this will not work for me.  I have already identified the process and need to know which port they are using.

---

### Post by The Cog on 2012-12-24
I would probably use lsof -i to get the open ports, and pipe through grep to pick out the right pid,

---

### Post by rnerwein on 2012-12-24
> **own3mall said:**
> Is there a way to get the port in use by a process?  I've got the PIDs, and I just want the port number that each process is using returned.  So far, I've got:  

```

#!/bin/bash

# Get PIDs of everything running ET
PIDs=`sudo ps -ef | grep etded | awk '{print $2}'`

# Place PIDs into an array
arr=$(echo $PIDs | tr "\n" "\n")

# Foreach ID, check the port, kill the process if it's not 27960
for x in $arr
do
    echo "> [$x]"
done


```So far, people are identifying the processes based on the port, but this will not work for me.  I have already identified the process and need to know which port they are using.
hi
netstat -punt | grep etded
to get all: sudo netstat -puntl | grep blablablu
cheers

---

### Post by own3mall on 2012-12-24
> **rnerwein said:**
> hi
netstat -punt | grep etded
to get all: sudo netstat -puntl | grep blablablu
cheers

Thanks!  I spent two hours on this super nasty script:

```

#!/bin/bash

#Define valid IPs and Ports:
arrayValid=("226.240.226.188:27960" "226.240.226.189:27960")

#Get the date and time:
CurDate=`date +"%c"`

#Functions
containsElement () { for e in "${@:2}"; do [[ "$e" = "$1" ]] && return 0; done; return 1; }

# Get PIDs and IPs of everything running ET
PIDs=(`sudo netstat -puntl | grep etded | awk 'match($6,"/"){print substr($6,0,RSTART-1)}'`)
IPs=(`sudo netstat -puntl | grep etded | awk '{print $4}'`)

# Debug
# echo `sudo netstat -puntl | grep etded | awk '{print $4}'`
# echo `sudo netstat -puntl | grep etded | awk 'match($6,"/"){print substr($6,0,RSTART-1)}'`

#Create counter variable:
count=0

# Check each Process ID to see if it's using an IP and Port within the allowed array
# If it's not, kill it!
for x in ${IPs[@]}
do
   
   # Is the IP and Port in the valid IPs array?
   containsElement "$x" "${arrayValid[@]}"
   InArray=`echo $?`

   # Get the port
   StartPos=`expr index "$x" ":"`
   Port=${x:StartPos}
   
   #echo $StartPos
   #echo $Port
   
   # Debug values
   #echo $x
   #echo ${PIDs[$count]}
   #echo $InArray

   # InArray returns 1 if the IP is not in the array
   if [ "$InArray" == 1 ] && [ $Port -ge 27960 ] && [ $Port -le 28000 ] ; 
   then
       echo "Enemy Territory Process ID:${PIDs[$count]} was killed at $CurDate" >> /root/etded_log
       sudo kill -9 ${PIDs[$count]}
   else
       #It's in the valid IP address range, but we want to kill it if it's not running properly...
       #Additional ports are used when the PID freezes, as a new PID is launched
       
       #Debug
       # echo $(cat /proc/${PIDs[$count]}/status | grep "(sleeping)")
       # echo $(cat /proc/${PIDs[$count]}/status | grep "(running)")

       if [ "$(cat /proc/${PIDs[$count]}/status | grep "(sleeping)")" == "" ] &&
          [ "$(cat /proc/${PIDs[$count]}/status | grep "(running)")" == "" ]
       then
          echo "Enemy Territory Process ID:${PIDs[$count]} was killed at $CurDate" >> /root/etded_log
          sudo kill -9 ${PIDs[$count]}
       fi
   fi
   count=$(($count+1))
done

```

Wish there were a better way to do it...

---

