---
title: "Unchanging Trip points"
date: 2008-04-23
forum: General Help
---

### Post by deez on 2008-04-23
I'm running Ubuntu 7.10 on a Compaq Nc4010, Pentium M 1.7.  

I've searched and found walkthroughs for changing the trip points whence my fan kicks on.  

I've tried [this]("http://ubuntuforums.org/showthread.php?t=442877&highlight=trip+points") and [this]("http://ubuntuforums.org/showthread.php?t=41927") but still no dice.  


I've gone through them and cannot get the trip points to change.  Here's what they are and always have been:
> 
root@Delphi:~# cat /proc/acpi/thermal_zone/TZ1/trip_points
critical (S5):           103 C
passive:                 100 C: tc1=1 tc2=2 tsp=100 devices=CPU0 
active[0]:               80 C: devices=C1F6 
active[1]:               65 C: devices=C1F7 
active[2]:               48 C: devices=C1F8 
active[3]:               40 C: devices=C1F9

Trying this code >  echo -n "100:0:80:70:60:50:" > /proc/acpi/thermal_zone/TZ1/trip_points
 gets me this:

> bash: echo: write error: Invalid argument

I could really do for some help on this one.  My fan is on always, save for the first 2-3 minutes after booting. 

I've also tried to run this script, but it doesn't help either:

> function reset_trip_points
{
  if [ -f /proc/acpi/thermal_zone/TZ1/trip_points -a -f /proc/acpi/thermal_zone/TZ1/polling_frequency ]
  then

    ifs=$IFS
    IFS=" "
    for i in `cat /proc/acpi/thermal_zone/TZ1/trip_points`
    do
      j="${i%% C*}"
      j="${j##* }"
      i=${i%%[ :]*}
      i=${i//[][]/}
      case "$i" in
        critical|hot|passive|active0|active1|active2|active3)
          eval "[ \"x\$$i\" = x0 ] && $i=\$j"
          ;;
      esac
    done
    IFS=$ifs

    echo $critical:$hot:$passive:$active0:$active1:$active2:$active3 > /proc/acpi/thermal_zone/TZ1/trip_points 

    # Activate the kernel's temperature control system
    echo 30 > /proc/acpi/thermal_zone/TZ1/polling_frequency 

    # It's safe to turn the fan off now.
    echo -n 3 > /proc/acpi/fan/C1F9/state
  fi
}

# Set the new value for the temperature you would like to change, or leave it
# at zero to get the default.
critical=100
hot=93
passive=92
active0=80
active1=70
active2=60
active3=50

# Make the Kernel handle CPU temperature management.
# Do this before the filesystem checks so that the fan will turn off and stop
# draining the battery.
reset_trip_points

Any help is greatly appreciated

Thanks in advance.

---

### Post by ryanhaigh on 2008-04-24
Unfortunately as mentioned in the thread you linked to

> 
This feature was removed in the 2.6.22 linux kernel.
[https://lwn.net/Articles/244595/](https://lwn.net/Articles/244595/)
to check your kernel version..
uname -r
in Terminal


---

