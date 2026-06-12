---
title: "Why does my startup script not work?"
date: 2022-09-24
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2022-09-24
It works fine when i run it via a terminal after login
I have this script called via it's full path in my kde startup applications (Kubuntu 22.04)

```
[FONT=monospace][COLOR=#000000]$ cat /home/$USER/.config/mpd/start.sh[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]#!/bin/sh [/COLOR]
sleep 15 
HERE=$(dirname "$0") 
if [ -f $HERE/pid ];then 
        read -r pID < $HERE/pid 
        if [ -h /proc/$pID/exe ] && [ -n "$(readlink /proc/$pID/exe)" ];then 
            read -r pID < /proc/$pID/comm 
            if [ "$pID" = "mpd" ];then 
                echo "Yo, It is already running..." 
                exit 
            fi 
        fi 
fi 
/usr/bin/mpd $HERE/mpd.conf 
exit 0
[/FONT]
```

---

### Post by MAFoElffen on 2022-09-25
Please explain your logic flow... And what is in your 'pid' file? (contents)

It looks like you are trying to check if the mpd music player daemon is running, and if not start it... But this starts it whether it is or not. (because of a possible error in logic)

If that is what you are trying to do, then there's a lot easier way to do it.... actually lots of ways...

---

### Post by MAFoElffen on 2022-09-26
No answer(?). Just going to continue with my answer.

Here is the logic error (which migh have been just a typo):
```

...[FONT=monospace]
if [ "$pID" [COLOR=#ff0000]=[/COLOR] "mpd" ];then 
...

```
[/FONT]a single equals sign there, is not an evaluation for an if/then statement. Instead of evaluating "if equal" for a true or flase, it rather says "set to", which would always evaluate to true... And you used a very complex tree to get there...

Simpler, what I would have probably done was something like this:
```

#!/bin/bash
sleep 2
HERE=$(dirname "$0")
pID=$(pidof mpd)
if [ "$pID" == "" ]
then
    /usr/bin/mpd $HERE/mpd.conf 
else
    echo "mpd is running already"
fi
exit 0

```

---

### Post by pqwoerituytrueiwoq on 2022-09-26
Sorry for late reply, was busy working with my new raspberry pi pico w (really lost track of time)
MPD creates a PID file when it is running (see the [FONT=Courier New]pid_file[/FONT] option in [FONT=Courier New]mpd.confg[/FONT])

if i just open a terminal and run the script it works every time, but it i let autostart run it, it never starts

this is a shell script not a bash script, [FONT=Courier New]-eq[/FONT] is for numbers and [FONT=Courier New]=[/FONT] is for strings, [FONT=Courier New]==[/FONT] does not work
```
chad@X470-Gaming-Plus:~$ sh -c 'if [ "cat" == "cat" ];then echo hi;fi' 
sh: 1: [: cat: unexpected operator 
chad@X470-Gaming-Plus:~$ sh -c 'if [ "cat" = "cat" ];then echo hi;fi'  
hi
chad@X470-Gaming-Plus:~$ sh -c 'if [ "cat" = "dog" ];then echo hi;fi'
chad@X470-Gaming-Plus:~$
```

---

### Post by MAFoElffen on 2022-09-27
IDK - With what you provided, I traced trough the Logic. It is either  loaded or you reload it. It should work, unless there is some problem  loading that daemon.

But you say that if you start it from a  terminal it loads, so it show work. I think I would be hitting my head  against a wall. It show work.

Maybe extend the sleep time a bit? That way everything else is finished loading(???)

I  asked someone else about MPD. They said I should be running it for my  Music collection instead of Plex. Then my Son wants me and him to  migrate from Plex to Jellyfin, then migrate our music to MPD... So now I  seem to have more of a personal investment to get your problem resolved,  because it also might affect us.

How do you like MPD? Are you doing this script, because there is some problem with the MPD daemon not loading?

---

### Post by MAFoElffen on 2022-09-27
Since now, it seems that I have a personal investment with this, in think I would add to the script like this:
```

#!/bin/sh 
sleep 15 
HERE=$(dirname "$0")  # Get directory where script started
exit_code=0
if [ -f $HERE/pid ];then  # Check if the pid file from the daemon exists
    read -r pID < $HERE/pid  # set the directory & path to to a variable
    # Check to see if the link created by the daemon running is there and 
    # it is not blank
    if [ -h /proc/$pID/exe ] && [ -n "$(readlink /proc/$pID/exe)" ];then 
        read -r pID < /proc/$pID/comm  # Set the comm to a varaible
        if [ "$pID" = "mpd" ];
        then  # check to see if it is 'mpd'
            echo "Yo, It is already running..." # prompt that it is running
            exit exit_code
        fi
        # You told me when the daemon loads it writes a file with the PID, but...
        # I don't know if it deletes it when it shuts down at shutdown, so...
        # There may be a file, but with the last loaed PID. So this is where 
        # the else would be to reload it... 
        /usr/bin/mpd $HERE/mpd.conf
        exit_code=$? # Set exit code of manualy loading the daemon
        # check if it loaded or not
        if [ exit_code -eq 0 ]; then
            echo "mpd daemon loaded" # Daemon loaded
        else
            echo "mpd still not loaded"  # Daemone didn't load
        fi
        exit exit_code
    fi 
else
    echo "pid file was not there"  # PID file is missing
fi  

```

---

### Post by MAFoElffen on 2022-09-27
It won't let me edit that so corrected, more like this:

```

#!/bin/sh 

# Wait 15 seconds
sleep 15 
HERE=$(dirname "$0")  # Get directory where script started
exit_code=0

# Check if the pid file from the daemon exists
if [ -f $HERE/pid ];
then  
    # set the directory & path to to a variable
    read -r pID < $HERE/pid  
    
    # Check to see if the link created by the daemon running is there and 
    # it is not blank
    if [ -h /proc/$pID/exe ] && [ -n "$(readlink /proc/$pID/exe)" ];
    then 
        # Set the comm to a varaible
        read -r pID < /proc/$pID/comm  
        # check to see if it is 'mpd'
        if [ "$pID" = "mpd" ];
        then  
            # prompt that it is running
            echo "Yo, It is already running..." 
            # Here exit code is still 0...
            exit $exit_code
        fi
    else
        # You told me when the daemon loads it writes a file with the PID, but...
        # I don't know if it deletes it when it shuts down at shutdown, so...
        # There may be a file, but with the last loaed PID. So this is where 
        # the else would be to reload it... 
        /usr/bin/mpd $HERE/mpd.conf
        
        # Set exit code of manually reloading the daemon
        exit_code=$? 
        
        # check if it loaded or not
        if [ $exit_code -eq 0 ]; then
            # Daemon loaded
            echo "mpd daemon loaded" # Daemon loaded
        else
            # Daemon didn't load
            echo "mpd still not loaded"  
        fi
        exit $exit_code
    fi 
else
    # PID file is missing
    echo "pid file was not there" 
    exit_code=1
    exit $exit_code 
fi  


```

---

### Post by pqwoerituytrueiwoq on 2022-09-27
I do not recall why i am running it this way, in this use case i am using it cause i was not happy with the desktop software i could find, so i said screw it i will use mpd where i already have multiple viable GUIs
* i think it was some kind of permissions issue with some default file in some directory and make it was easier to deal with another way (it was last November when i did this)

the sleep 15 is already excessively long (probably 3 or 4x) i only put that in there after it was not working (currently working on getting a pico setup to replace my dead rpi 0 thermostat; lightening damage, RIP SOC)


i run mpd on my raspberry pi as well as on my x86 server (this and a pico will be replacing the pi) gonna have the entire house sound system attached to the server with a few pico units with some buttons on there for play/pause for the given room (the pico will also be wired to door sensors as well as DHT22 temp/humidity sensors) it is a giant work in progress

the pid file remains after the sever stops, that is why i check if the app running under that pid is infant mpd

i do not ask much from a music player, i just want random playback from the entire library and i made a script to manage the playlist so every file is part of it (i'm not much a power user when it comes to music playback, i just want it to work)

i'll attach my web ui for mpd incase you want to take a look at it (usually have it open in a side bar), if you use kde i also have a widget that i made for use with do-it-yourself-bar (i'll drop this in there also)
also have one i made for playback on the client device i made in html: [https://github.com/GM-Script-Writer-62850/HTML5-Music-Player](https://github.com/GM-Script-Writer-62850/HTML5-Music-Player)

---

### Post by MAFoElffen on 2022-09-29
Thank you very much... You have given me more than I expected... and I was the one who expected to help you! LOL

Here is my gits: 
[https://github.com/Mafoelffen1/](https://github.com/Mafoelffen1/)
(mostly my Bash and Python scripting)
[https://github.com/Mafoelffen1/system-info](https://github.com/Mafoelffen1/system-info)
(Bash TEST/DEV for the UbuntuForums 'system-info' script:)
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
[https://ubuntuforums.org/showthread.php?t=2465764](https://ubuntuforums.org/showthread.php?t=2465764)
(Discussion thread for that script)

I  can see the logic is sound and should work, what I added would then,  after if is loaded again, check if the reload was successful or not.

It should work. Maybe a timing issue. I think on mine, if I have a load problem, then I would do something like this.
```

#!/bin/sh -e
##
## Ensure all paths have exits...
#
# Loop for up to 15 seconds or success, else throw error

#############
## Variables
#############
HERE=$(dirname "$0")  # Get directory where script started
exit_code=0
timer=0

#############
## Functions
#############
function CheckMPD() {
    while [ $timer -lt 15 ]
    do
        # Check if 'mpd' daemon is running
        /usr/sbin/start-stop-daemon -T --name "mpd"
        exit_code=$?
    
        if [ $exit_code -eq 0 ]
        then
            exit $exit_code
        else
            /usr/bin/mpd $HERE/mpd.conf
            exit_code=$? 
        
            if [ $exit_code -eq 0 ]; then
                echo "mpd daemon loaded"  # DEBUG
                exit $exit_code
            else
                echo "mpd still not loaded"  # DEBUG
                sleep 1
                timer=$timer+1
            fi
        fi
    done
    }

#########
## Main
#########
CheckMPD
echo "mpd still not loaded" 
exit $exit_code

```

---

### Post by pqwoerituytrueiwoq on 2022-10-23
this give me 3 after autostart has ran and mpd did is not running [FONT=Courier New]/usr/sbin/start-stop-daemon -T --name "mpd"; echo $? [/FONT]
this script is able to determine that mpd is not running correctly
after running [FONT=Courier New]/usr/bin/mpd $HERE/mpd.conf[/FONT]
[FONT=Courier New]echo $?[/FONT] gives 0
however checking [FONT=Courier New]/usr/sbin/start-stop-daemon -v -T --name mpd[/FONT] allows me to get 3 from [FONT=Courier New]$?[/FONT]
so i tried this:
```
#!/bin/sh
HERE=$(dirname "$0")
if [ -f $HERE/pid ];then
        read -r pID < $HERE/pid
        if [ -h /proc/$pID/exe ] && [ -n "$(readlink /proc/$pID/exe)" ];then
                read -r pID < /proc/$pID/comm
                if [ "$pID" = "mpd" ];then
                        echo "Yo, It is already running..."
                        exit
                fi
        fi
fi
/usr/bin/mpd $HERE/mpd.conf
/usr/sbin/start-stop-daemon -v -T --name mpd
while [ $? -eq 3 ];do
        echo "Failure"
        sleep 1
        /usr/bin/mpd $HERE/mpd.conf
        /usr/sbin/start-stop-daemon -v -T --name mpd
done
exit 0
```
and it still does not work
note that $HERE is working as expected

---

### Post by pqwoerituytrueiwoq on 2022-10-23
i tried this and mpd was working then it stopped
and this is all i got in my log file, and now idk why i do not have more output in my log (edit: error line 41; use 'do' not 'then')
maybe mpd stops when the start script exist?

```
cat /tmp/mpd_start.log
Starting mpd
HERE = /home/chad/.config/mpd
mpd started: 0
```
```
#!/bin/sh
HERE=$(dirname "$0")
LOG="/tmp/mpd_start.log"
LOGGING=1
debug () {
        if [ $LOGGING -eq 1 ];then
                echo $1 >> $LOG
        fi
        if [ -n "$2" ];then
                echo $1
        fi
}
if [ $LOGGING -eq 1 ];then
        echo "Starting mpd" > $LOG
fi
debug "HERE = $HERE"
if [ -f $HERE/pid ];then
        read -r pID < $HERE/pid
        debug "pID = $pID"
        if [ -h /proc/$pID/exe ] && [ -n "$(readlink /proc/$pID/exe)" ];then
                read -r pID < /proc/$pID/comm
                debug "pID = $pID"
                if [ "$pID" = "mpd" ];then
                        debug "Yo, It is already running..." 1
                        exit
                fi
        fi
fi
/usr/bin/mpd "$HERE/mpd.conf"
debug "mpd started: $?"
sleep 30
/usr/sbin/start-stop-daemon -v -T --name mpd
while [ $? -ne 0 ];do
        debug "Failed to start; retry" 1
        /usr/bin/mpd "$HERE/mpd.conf"
        debug "mpd started: $?"
        sleep 5
        /usr/sbin/start-stop-daemon -v -T --name mpd
done
status="$(/usr/bin/mpc status)"
while [ -z "$status" ];then
        /usr/sbin/start-stop-daemon -v -T --name mpd
        debug "WTF - $?"
        sleep 1
        status="$(/usr/bin/mpc status)"
fi
debug "status = $status"
exit 0
```

---

### Post by pqwoerituytrueiwoq on 2023-01-09
So the issue seems to be as soon as my script exits mpd stops
my script starts mpd using this line
[FONT=courier new]/usr/bin/mpd "$HERE/mpd.conf"[/FONT]

i could just put a while true sleep loop in the script...

---

### Post by TheFu on 2023-01-09
You know that the mpd package comes with an init.d/ startup script already?  Just need to figure out any issue for why mpd isn't running.  

On my raspberry pi, 
```
$ ps -eaf |grep mpd
mpd        379     1  0 Jan04 ?        00:00:02 /usr/bin/mpd --no-daemon

```

/etc/init.d/mpd is the location of that script.

To make it start automatically, 
```
$ sudo systemctl enable mpd
```
and ensure it isn't disabled in /etc/default/mpd

---

### Post by MAFoElffen on 2023-01-09
Sorry. When you first posted this, I had assumed that you "were" running mpd as a daemon, and were just checking that it was loaded and 'still running'.

Thank you for another set of eyes: 'TheFu'...

---

### Post by pqwoerituytrueiwoq on 2023-01-13
I was trying to run it on a user level not the system level

---

### Post by TheFu on 2023-01-14
> **pqwoerituytrueiwoq said:**
> I was trying to run it on a user level not the system level

I'm not certain I understand what this means.  mpd runs as the user mpd, so not root.  Startup can happen automatically at boot but the pulse audio subsystem really likes for a user with an X/Session to control audio devices, which sorta defeats the purpose of using mpd, IMHO.  If you want to playback music only when there's a login session active, there are other tools ... any of the GUI audio players, for example.  If you want to use something like mpv without any GUI, the trick is to set the DISPLAY to :0 .... here's my exact line to play music/playlists using mpv over an ssh connection:
```
DISPLAY=:0 /usr/bin/mpv --no-audio-display --vo=null --volume=50 "$M3U"
```
I know this works. Jammin' to some Pearl Jam now.

If you want to run mpd as a different userid, there's a setting in the /etc/mpd.conf file:
```
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
user                            "mpd"
```
Here's the process table with mpd on my system:
```
$ psg mpd
mpd         2001       1  0 Jan09 ?        00:00:00 /usr/bin/mpd --no-daemon
```
If I'm not logged in, I don't see how it could run as the current user, since no user is currently logged in and I use M.A.L.P. as a client.  i.e., it doesn't work that way, which is why my conf file specifies teh mpd userid.  I just needed to ensure the mpd userid was part of the audio Unix group for access to audio devices.

If you want to use your own script, just use 'su - thefu command' in the script to run with a specific userid, but be launched at boot.

I'm probably missing something important for the need you have.  I've just been using mpd for about 3 yrs and find it great to control playback using remote clients from anywhere in the house.

---

