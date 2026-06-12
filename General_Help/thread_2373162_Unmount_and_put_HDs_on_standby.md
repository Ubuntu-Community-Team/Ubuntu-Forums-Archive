---
title: "Unmount and put HDs on standby?"
date: 2017-10-03
forum: General Help
---

### Post by ra7411 on 2017-10-03
I infrequently use a couple SATA HDs on my desktop. Will putting them on standby and unmounting them lower power usage and extend the HD's lives?

Thanks

---

### Post by DuckHook on 2017-10-03
The short answer is: yes.

The more complete answer is: instead of *unmounting*, consider using *autofs*, which auto unmounts HDDs after a set time and automounts them again when accessed.

Note that standby won't work on some older HDDs.

Autofs info:

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Standby info:

[http://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time](http://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time)
[http://zackreed.me/articles/60-spin-down-idle-hard-disks](http://zackreed.me/articles/60-spin-down-idle-hard-disks)
[http://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm](http://www.linux-magazine.com/Online/Features/Tune-Your-Hard-Disk-with-hdparm)

---

### Post by efflandt on 2017-10-03
This is a script I call hd-standby and put in /etc/cron.hourly because older methods to auto spin down a hard drive do not seem to work with newer drives:```
#!/bin/sh
# Spin down drive(s) when idle and not mounted
# Put script in /etc/cron.hourly
drives="/dev/sda" # drive(s) to spin down (space separated)
IFS="$(printf '\n\t')" # remove newline from hdparm output
for hd in $drives
do
  dstate=$(/sbin/hdparm -C $hd | /bin/grep -B 1 standby)
  if [ $? -ne 0 ] # if not in standby
  then # active/idle
    /bin/grep $hd /etc/mtab 2>&1 > /dev/null
    if [ $? -ne 0 ] # do standby if not mounted
    then dstate=$(/sbin/hdparm -y $hd 2>&1)
    fi 
  fi
  if [ "$dstate" != '' ] # log unless mounted (null)
    then echo $dstate | /usr/bin/logger -e
  fi
done
```Basically you set **drives** variable to a space separate list of drives you want to put into standby with quotes around that list, and it if any of those drives are active, not mounted, and not already in standby, it will put them in standby and log that in syslog. Otherwise it does nothing.

Note that it needs execute permission. It does not matter if it has execute permission for "others", because anyone else would need to be in sudo group for it to do anything manually:```
~$ ls -l /etc/cron.hourly
total 4
-rwxr-xr-x 1 root root 602 Jan 25  2017 hd-standby
```

---

### Post by ra7411 on 2017-10-04
I've been looking at temperatures to see if my HDs are actually responding to standby commands from Disks. I use the terminal w/  hdparm -H since Disks doesn't seem to keep the HD temperatures updated. 
All 3 2tb HDs are Hitachis; 2 model 330s, 1 331.

Oddly, if I just put an HD on standby (in Disks) while mounted, the temperature doesn't decrease from the active mounted level (~38C). 
If I put it on standby and unmount it, T drops to ~27C.

From what I'm seeing, you have to check on things to see if Disks commands are actually having an effect on your particular brand/model HD.

---

### Post by efflandt on 2017-10-04
Not sure which temperature is correct. When in standby:```
~$ sudo hdparm -C /dev/sda

/dev/sda:
 drive state is:  standby
```smartctl shows 30 C and psensors shows 40 C (Western Digital 1 TB) (sudo hdparm -H /dev/sda shows -18, so apparently not supported for WD drive) , although, smartctl and psensors match for my mSATA SSD in SATA adapter at 36 C. But maybe psensors does not poll a drive in standby.

---

