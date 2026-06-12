---
title: "Startup script runs but doesn't work (serial remote control) 12.04"
date: 2014-03-30
forum: General Help
---

### Post by lindsayward on 2014-03-30
Hi there.
I have a problem in 12.04 that I've been working on most of the day. I've searched a heap, tried lots of things, and am finally ready to post a plea for help!

In short: I have a startup script that runs, but it does not produce the same result as when I run it myself.
The script:
```

#setup serial port
stty -F /dev/ttyUSB0 9600exec 3<> /dev/ttyUSB0
# irexec daemon for remote control commands
irexec -d
echo "finished mystartup..." > /tmp/finlog.txt
```

I have tried:
[LIST=1]
[*]putting the script in crontab (crontab -e and the script line was prefaced with @reboot) - this runs (finlog.txt exists), but irexec is not running and the serial port is not setup
[*]putting this script in /etc/rc.local - this runs the same as crontab
[*]putting the script in "Startup Applications" using the Unity tool - this does NOT run at all (finlog.txt does not exist)
[*]using an upstart job in /etc/init/ - this runs and does run irexec, but the ttyUSB0 port says "device or resource busy". I tried putting userid = lindsay (my username) in the script...
[*]So, I tried putting irexec -d in the Startup Applications and the other setup jobs in the Python script for each and every button press (redundant, but wouldn't require the startup script) and now the Python script runs, but the serial commands don't work&#8230; if I type cat /dev/ttyUSB0, then they DO work&#8230; ?
[/LIST]

Here are my attempts for the methods. I've used absolute paths in all of them...

crontab
```
@reboot /home/lindsay/scripts/mystartup.sh > /home/lindsay/scripts/startupoutput.txt
```

rc.local
```
exec 2> /tmp/rc.local.log  # send stderr from rc.local to a log file
exec 1>&2                      # send stdout to the same log file
set -x                         # tell sh to display commands before execution

sleep 12
/home/lindsay/scripts/mystartup.sh
#output date, to be sure this ran
date > /tmp/datetemp.txt
```

upstart (/etc/init/lindsaystartup.conf):
```
# /etc/init/lindsaystartup.conf 
description "Lindsay's startup script"
author      "Lindsay Ward"
 
# used to be: start on startup
# until we found some mounts weren't ready yet while booting:
#start on started mountall
# If network interface is wireless
#start on (local-filesystems and net-device-up IFACE=wlan0)
# If network interface is Ethernet uncomment below line and comment above line
start on (local-filesystems and net-device-up IFACE=eth0)
 
stop on shutdown
 
# Automatically Respawn:
#respawn
#respawn limit 99 5
 
script
    # Not sure why $HOME is needed, but we found that it is:
    export HOME="/home/lindsay/"
    setuid lindsay
 
    exec /home/lindsay/scripts/mystartup.sh >> /tmp/startupout.txt 2>&1
end script
 
post-start script
end script
```

Background:
I have figured out how to get my Harmony remote to use irexec to start a Python script that toggles the picture mute feature of my TV by using the serial port (USB). I have to setup/open the serial port first. It does work if I do it manually, but not with any of these startup script options.

The Python script, if you're interested is:
```
import os, subprocess

#setup serial port
## To be done by startup script... so should be ready/open
## WHEN I figure out how!
subprocess.call("stty -F /dev/ttyUSB0 9600", shell=True)
subprocess.call("exec 3<> /dev/ttyUSB0", shell=True)

os.chdir("/home/lindsay/scripts")
inFile = open("picmutestatus.txt", 'r')
status = inFile.readline().strip()
inFile.close()
outFile = open("picmutestatus.txt", 'w')
if status == "off":
    # send serial command for mute on
    subprocess.call("echo 'kd 0 1' > /dev/ttyUSB0", shell=True)
    outFile.write("on")
else:
    # send serial command for mute off
    subprocess.call("echo 'kd 0 0' > /dev/ttyUSB0", shell=True)
    outFile.write("off")       
#subprocess.call("exec 3>&-", shell=True)
outFile.close()
```

---

### Post by TheFu on 2014-03-30
Scripting 101:
* always specify complete, full paths to all programs
* always know any environment variables that must be set for each program to work properly - HOME is just 1.
* always know the required groups to access specific devices.  Some are only available to console logins. This is a security feature, but can be overridden simply by added the userid to the group manually.  Login on a console, run **id** to see. Now ssh in from a different PC and run **id**. See the differences?

---

### Post by lindsayward on 2014-03-30
Thanks very much for the reply. I'm sure it's helpful, but I'm not sure how - sorry for my ignorance.
* I have specified full paths, as shown in the samples.
* I don't know what environment variables need to be set… how would I? (legitimate question - perhaps that's the issue?)
* I tried typing id from an ssh terminal and from directly on the machine, and I got the same results.

I actually have made a working solution using only Python and the serial module (irexec -d started OK from Startup Applications), based on [http://forum.xbmc.org/showthread.php?tid=115599](http://forum.xbmc.org/showthread.php?tid=115599) 
Although this has solved my problem for now, I am still very keen to find out the solution to why the script wasn't working. I always find it frustrating when you find someone's question online and it's just what you want to ask, but they solve their problem a different way and the question never gets answered!
So please reply if you have more ideas, thanks.
Here's the working Python code if anyone's interested:
```
import serial, os, time

#setup serial port
ser = serial.Serial("/dev/ttyUSB0", 9600, timeout=1)
#time.sleep(1)
#ser.write("kf 0 0\r")


os.chdir("/home/lindsay/scripts")
inFile = open("picmutestatus.txt", 'r')
status = inFile.readline().strip()
inFile.close()
outFile = open("picmutestatus.txt", 'w')
if status == "off":
    # send serial command for mute on
    ser.write("kd 0 1\r")
    outFile.write("on")
else:
    # send serial command for mute off
    ser.write("kd 0 0\r")
    outFile.write("off")
#outFile.write(ser.portstr)
#print ser.portstr
time.sleep(0.4)
outFile.close()
ser.close()
```

---

### Post by efflandt on 2014-03-30
Since you may not know the environment or $PATH, full paths means "full" paths for everything including files and binaries (programs or commands).

For example in your very first code block at the top of this post you might assume that /bin is in your $PATH, but it would be best to use /bin/stty. What might be tripping you up is that I have no clue where irexec is, so you should include the full path to that. Also use full paths for everything you do from cron including within scripts launched by cron.

---

