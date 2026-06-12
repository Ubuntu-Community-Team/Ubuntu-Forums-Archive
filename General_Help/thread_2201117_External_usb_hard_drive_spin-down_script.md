---
title: "External usb hard drive spin-down script"
date: 2014-01-22
forum: General Help
---

### Post by timbalisto on 2014-01-22
I recently accuired an external usb hard drive, it works great, but I would like the disc to spin-down after a set time of inactivity. It is a Seagate Backup Plus 3 TB USB 3.0 Desktop External Hard Drive (STCA3000101). I used[ this article's]("https://help.ubuntu.com/community/ExternalDriveStandby") script and added this lsb info to the top (under #!/bin/bash) ```
### BEGIN INIT INFO
# Provides:          defaultdaemon
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INF
``` Then I saved it to /etc/init.d/, chmod -x'd the script, and then ran ```
sudo update-rc.d scsi-idle.sh defaults
```
I then executed the script in nautilus, it's been over an hour and the drive is still spinning. I'm running 13.04. I'm not using it for backups, just extra storage.

I just want the drive to spin-down when not in use. Can anyone help me?

---

### Post by timbalisto on 2014-01-23
I can't be the only one with this kind of problem.

---

### Post by pbrane on 2014-01-23
When you say "I then executed the script in nautilus", exactly how did you do that. This script requires that you provide the idle time as a parameter. Is that what you did?

---

### Post by timbalisto on 2014-01-23
I'm new to bash scripting, I thought the idle time parameter was in the  script itself. Do I then have to write a script to execute the  scsi-idle.sh script thusly? 
```
sudo ./scsi-idle 1500 &
```
I'll have to remove the first script with ```
sudo update-rc.d -f scsi-idle.sh remove
``` Then write a new script that executes the first script with the above parameters. Would I need to use "sudo" in the script, would it ask for my password?

```
#!/bin/bash
### BEGIN INIT INFO
# Provides:          defaultdaemon
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INF

##Calls scsi-idle script with time parameters
/etc/init.d/scsi-idle.sh 1500 &

##for "standby" mode, which still causes the disc to spin down but allows it to automatically spin back up when accessed.
sg_start --pc=3 /dev/sdh
``` 
Do I have this right? Should I use both commands, one or the other? Thanks for the help.

---

### Post by Dave_L on 2014-01-23
When you run a script with sudo, it runs as root. There's no need to use sudo inside the script, and that wouldn't work anyway.

The time parameter has to be passed to the script, as you've done above (scsi-idle 1500).  That's the $1 inside the script (interval=$1).  Inside a shell script, $0 is the command, $1 is the first parameter, $2 is the second parameter, etc.

---

I'm interested in this, because I also have a Seagate external drive that won't sleep. It worked in Ubuntu 10.04, but not in 12.04. It's a different model drive, and I had it working in 10.04 by using the sdparm command to change the drive settings.

I don't understand that article very well, so I can't be of much help here.

---

### Post by timbalisto on 2014-01-23
I've got it figured out, I think.
I used a script from [this website]("http://everydaylht.com/howtos/multimedia/spin-down-idle-usb-drives/"). I used the script from one of the comments as opposed to the one presented in the article because of a syntax error. I just had to substitute in the uuid of my external drive near the top of the script where the multiple X's are. I dropped it into cron.hourly and set permissions with chmod u+x. I haven't seen if cron executes it correctly or not, but the script worked perfectly when I executed from the terminal.
```
#!/bin/bash
DISKNAME=`ls -l /dev/disk/by-uuid/ | grep "XXXXXXXXXXXX" | mawk '{ print $(NF) }' | sed s_\.\.\/\.\.\/__`
isstandby=`hdparm -C /dev/$DISKNAME | grep -c standby`
if [ $isstandby == 0 ]
then
    a=0
    #check 100 times with 0.1s gaps and go on adding
    for i in `seq 0 100`
    do
        b=`cat /proc/diskstats | grep $DISKNAME | mawk '{ print $(NF-2) }'`
        a=`expr $a + $b`
        sleep 0.1s
    done
    echo $a
    if [ $a == 0 ]
    then
        echo "No Activity"
        #sdparm -C stop /dev/$DISKNAME
        hdparm -y /dev/$DISKNAME
    else
        echo "Disk Active"
    fi
fi
exit 0


``` I'll update this post in an hour to tell whether cron executes it properly.

I hope this is able to help others. Thanks for the help.

Edit: Over an hour later and the drive is still running. The script  itself works, but cron isn't executing it. I'll have to do some more research on that front.

---

### Post by timbalisto on 2014-01-24
I figured it out. Cron won't execute scripts with a file extension, it doesn't like punctuation. So I just removed the ".sh" from the file name, and now everything works. I'm going to mark this thread as solved.

---

