---
title: "Stop Service When Laptop Battery Low"
date: 2023-06-14
forum: General Help
---

### Post by richardbaum on 2023-06-14
Can anyone please help me out with putting together a simple script to stop a service when laptop battery is low?
This laptop is running 24/7, need to stop it to prevent corruption is power is cut and laptop shuts down.
Any other ideas to shutdown this service when battery is low also appreciated. (have APC UPS)

Command to stop service:
```
sudo systemctl stop fulcrum.service
```

---

### Post by MAFoElffen on 2023-06-14
I adapted an older script that started out life as this, which no longer works for Ubuntu, but was a good start: [https://unix.stackexchange.com/questions/84437/how-do-i-make-my-laptop-sleep-when-it-reaches-some-low-battery-threshold](https://unix.stackexchange.com/questions/84437/how-do-i-make-my-laptop-sleep-when-it-reaches-some-low-battery-threshold)

Updated fro systemd and current Ubuntu...
```

#!/bin/bash

###########################################################################
#
# Usage: system-low-battery
#
# Checks if the battery level is low. If &#8220;low_threshold&#8221; is exceeded
# a system notification is displayed, if &#8220;critical_threshold&#8221; is exceeded
# a popup window is displayed as well. If the critical threshold is met, it 
# shuts down systemd service after &#8220;timeout&#8221; seconds. If &#8220;Cancel&#8221; is pressed the script
# does nothing.
#
# This script is supposed to be called from a cron job.
#
###########################################################################

# This is required because the script is invoked by cron. Dbus information
# is stored in a file by the following script when a user logs in. Connect
# it to your autostart mechanism of choice.
#
# #!/bin/bash
# touch $HOME/.dbus/Xdbus
# chmod 600 $HOME/.dbus/Xdbus
# env | grep DBUS_SESSION_BUS_ADDRESS > $HOME/.dbus/Xdbus
# echo 'export DBUS_SESSION_BUS_ADDRESS' >> $HOME/.dbus/Xdbus
# exit 0
#

###########################
## VARIABLES
###########################
low_threshold=10
critical_threshold=4
timeout=59
shutdown_cmd='sudo systemctl stop fulcrum.service'

level=$(upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /percentage/ ) { print $2  } }' | \
    sed 's/%//g')
state=$(upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /state/ ) { print $2  } }' )


###########################
## FUNCTIONS
###########################
function do_shutdown() {
  sleep $timeout && kill $zenity_pid 2>/dev/null

  if [ x"$state" != x'discharging' ]; then
    exit 0
  else
    $shutdown_cmd
  fi
}

function check_states () {
  if [ -r ~/.dbus/Xdbus ]
  then
    source ~/.dbus/Xdbus
  fi

  # Is it unplugged from AC and discharging
  if [ x"$state" != x'discharging' ]
  then
    exit 0
  fi

  if [ "$level" -gt $critical_threshold ] && [ "$level" -lt $low_threshold ]
  then
    notify-send "Battery level is low: $level%"
  fi

  if [ "$level" -lt $critical_threshold ]
  then

    notify-send -u critical -t 20000 "Battery level is low: $level%" \
      'The system is going to shut down the fulcrum.service in 1 minute.'

    DISPLAY=:0 zenity --question --ok-label 'OK' --cancel-label 'Cancel' \
      --text "Battery level is low: $level%.\n\n The system is going to shut down the fulcrum.service in 1 minute." &
    zenity_pid=$!

    do_shutdown &
    shutdown_pid=$!

    trap 'kill $shutdown_pid' 1

    if [ ! wait $zenity_pid ]
    then
      kill $shutdown_pid 2>/dev/null
    fi

  fi
}

###################
## MAIN
###################
check_states

exit 0

```

---

### Post by richardbaum on 2023-06-14
Wow nice, thank you!

I am just getting started learning about scripts, sorry for stupid questions:

1) Do I have it right that if state is not charging and battery level is 10%, shutdown command is initiated?
2) What happens at critical 4%?
3) What is function of timeout?
4) Will the sudo command run without password?
5) What is the /.dbus/Xdbus stuff all about?
6) How much of this script can I strip out if notifications are not required? 


I almost never lift the lid.
If I am home I know if there is a power outage.
If away I can SSH in to check on it.
Maybe I could look into adding email notification once I get it running.

---

### Post by richardbaum on 2023-06-14
Went to give this a go as is:

```
$ touch $HOME/.dbus/Xdbus
touch: cannot touch '/home/richard/.dbus/Xdbus': No such file or directory
```

---

### Post by MAFoElffen on 2023-06-15
If you were keeping the dialog box where you had to respond, then you would create that directory first
```

mkdir $HOME/.dbus/

```
But since you wan it stripped down, you no longer need that.

Stripped down? No response to notifications from user? I left echo'ing thigs, so you know what is going on. You can always comment those out.
```

#!/bin/bash
###########################################################################
#
# Usage: system-low-battery
#
# Checks if the battery level is low. If &#8220;low_threshold&#8221; is exceeded a message is displayed, 
# if &#8220;critical_threshold&#8221; is exceeded, a message is displayed as well. If the critical threshold 
# is met, it shuts down systemd service after &#8220;timeout&#8221; seconds. 
#
# This script is supposed to be called from a cron job.
#
###########################################################################

###########################
## VARIABLES
###########################
low_threshold=10  # Point where you want a warning that the battery is getting low.
critical_threshold=4  # Point where the shutdown happes
timeout=59
shutdown_cmd='sudo systemctl stop fulcrum.service'
level=$(upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /percentage/ ) { print $2  } }' | \
    sed 's/%//g')
state=$(upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /state/ ) { print $2  } }' )


###########################
## FUNCTIONS
###########################
function do_shutdown() {
  if [ x"$state" != x'discharging' ]; then
    exit 0
  else
    $shutdown_cmd
  fi
}

function check_states () {
  # Is it unplugged from AC and discharging
  if [ x"$state" != x'discharging' ]
  then
    exit 0
  fi
  if [ "$level" -gt $critical_threshold ] && [ "$level" -lt $low_threshold ]
  then
    echo -e "Battery level is low: $level%" # This is just a warning that the battery level is getting low.
  fi
  if [ "$level" -lt $critical_threshold ]
  then
    # This says the battery level is low enough to shutdown th service
    echo -e "Battery level is low: $level% \
      The system is going to shut down the fulcrum.service in 1 minute."
    sleep $timeout
    do_shutdown
  fi
}

###################
## MAIN
###################
check_states
exit 0

```

---

### Post by richardbaum on 2023-06-15
I did a test run after setting this latest script up a a cron job, unfortunately it is not stopping fulcrum.service.(changed values in script to test)

Output of:
```
upower -i /org/freedesktop/UPower/devices/battery_BAT0

native-path:          BAT0
  vendor:               ASUSTeK
  model:                ASUS Battery
  power supply:         yes
  updated:              Thu 15 Jun 2023 06:58:38 PM (100 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              8.214 Wh
    energy-empty:        0 Wh
    energy-full:         28.271 Wh
    energy-full-design:  33.3 Wh
    energy-rate:         7.092 W
    voltage:             11.1 V
    charge-cycles:       66
    time to empty:       1.2 hours
    percentage:          29%
    capacity:            84.8979%
    technology:          lithium-ion
    icon-name:          'battery-low-symbolic'
  History (rate):
    1686880718    7.092    discharging
```

Should variables for level and state be the same?

```
level=$(upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /percentage/ ) { print $2  } }' | \
    sed 's/%//g')
state=$(upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /state/ ) { print $2  } }' )
```

Also seem to be getting an error in log:

```
Jun 15 18:50:01 baum CRON[12217]: (root) CMD (/home/richard/bin/fulcrum.sh)
Jun 15 18:50:01 baum CRON[12216]: (CRON) info (No MTA installed, discarding output)
```


Thanks again for your help, much appreciated!

---

### Post by MAFoElffen on 2023-06-16
The output of these two queiries, do get different output:
```

mafoelffen@Mikes-ThinkPad-T520:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /percentage/ ) { print $2  } }' | \
    sed 's/%//g'
95
mafoelffen@Mikes-ThinkPad-T520:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
    gawk '{ if ( $1 ~ /state/ ) { print $2  } }'
pending-charge

```
For your cron errors, there is outputh there, where cron is trying to email you. To ignore, do
```

sudo crontab -e
# then...
* * * * * yourCommand 2>&1 /dev/null

```

---

### Post by richardbaum on 2023-06-16
Adding 2>&1 /dev/null works but only until low_threshold is reached. (no big deal)

The problem ended up being this, hence the value of asking stupid questions!
```

upower -i /org/freedesktop/UPower/devices/battery_BAT0 | \
gawk '{ if ( $1 ~ /percentage/ ) { print $2  } }' | \
sed 's/%//g'      
Command 'gawk' not found, but can be installed with:
sudo apt install gawk
```

Installed gawk and tested - it works!
```

Jun 16 10:46:00 baum Fulcrum[6924]:  -- Caught signal 15, exiting ...
Jun 16 10:46:00 baum Fulcrum[6924]: [2023-06-16 10:46:00.083] Shutdown requested via signal
Jun 16 10:46:00 baum Fulcrum[6924]: [2023-06-16 10:46:00.083] Stopping Controller ...
Jun 16 10:46:00 baum systemd[1]: Stopping Fulcrum...
```

Thank you very much for your time and patience!

---

