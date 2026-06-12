---
title: "modifying script"
date: 2018-07-20
forum: General Help
---

### Post by rburkartjo on 2018-07-20
want to add a desktop notification when this script is finished
#!/bin/bash
clamscan -i -r /home/ray > /home/ray/vsr/clamscan.log

./tks

---

### Post by Holger_Gehrke on 2018-07-20
'notify-send' and 'zenity' can both do that. Details can be found in their respective manual pages.

Holger

PS: The command 'apropos' could have told you that. It searches the manual for keywords in the first part of each page.

---

### Post by rburkartjo on 2018-07-20
figured it out -changed aforementioned script to
#!/bin/bash
clamscan -i -r /home/ray > /home/ray/vsr/clamscan.log && notify-send -t 0 "home virus scan done"

---

### Post by wildmanne39 on 2018-07-20
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by again? on 2018-07-21
There is a package in the repos that will alert when a terminal command longer than 10secs finishes, if the terminal is not in focus.
I have used for a number of years without problem. 
```
sudo apt install undistract-me
```

After install add this to your ~/.bashrc
```
#notify when long running commands finish(undistract-me)
. /usr/share/undistract-me/long-running.bash
notify_when_long_running_commands_finish_install
```

Reload bashrc
```
source ~/.bashrc
```

Then test with 
```
sleep 11
```
Will only notify when the terminal is not in focus.

I edit the script at **/usr/share/undistract-me/long-running.bash** to also play a ting sound 
(use your own or the attached sound if /usr/share/sounds/freedesktop/stereo/complete.oga doesn't exist on your system).
ie this is the last part of the script with the added sound [COLOR="#FF0000"]edit[/COLOR].
```
if [ -x "$notify" ]; then
                        $notify \
                        -i $icon \
                        -u $urgency \
                        "Long command completed" \
                        "\"$__udm_last_command\" took $time_taken_human"
			 [COLOR="#FF0000"]paplay "/usr/share/sounds/freedesktop/stereo/complete.oga"[/COLOR]
                    else
                        echo -ne "\a"
                    fi
                fi
                if [[ -n $LONG_RUNNING_COMMAND_CUSTOM_TIMEOUT ]] &&
                    [[ -n $LONG_RUNNING_COMMAND_CUSTOM ]] &&
                    [[ $time_taken -gt $LONG_RUNNING_COMMAND_CUSTOM_TIMEOUT ]] ; then
                    # put in brackets to make it quiet
                    export __preexec_exit_status
                    ( $LONG_RUNNING_COMMAND_CUSTOM \
                        "\"$__udm_last_command\" took $time_taken_human" & )
                fi
            fi
        fi
    }

    function preexec () {
        # use __udm to avoid global name conflicts
        __udm_last_command_started=$(printf "%(%s)T\n" -1)
        __udm_last_command=$(echo "$1")
        __udm_last_window=$(active_window_id)
    }

    preexec_install
}
```

---

