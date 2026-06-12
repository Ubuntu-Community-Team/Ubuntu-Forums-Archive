---
title: "UPSTART: script spawns itself??"
date: 2013-09-11
forum: General Help
---

### Post by leopardsanderson on 2013-09-11
Dear all,
I am testing an upstart job for automatic connection of machines based on avahi and other stuff, similar to UPnP but focused on professional audio.

The problem I'm facing it's hawkward: a script launched by the upstart job appears in the process list twice, one instance lives forever (as it must) and another spurious one is born periodically and dies in a few seconds. The strange thing is: the parent of the spurious script is the first instance, but in my script there is no command that should give birth to another instance of the script!

Details:

the .conf in /etc/init launches these commands in the "script" stanza:
```
script
        if [ -f /home/ccrma/on-startup/WeMUST/wemust-start.sh ]; then
                rm /home/ccrma/on-startup/WeMUST/wemust.log
                rm /home/ccrma/on-startup/WeMUST/afterConnect.log
                sudo -H -E -u ccrma /home/ccrma/on-startup/WeMUST/wemust-start.sh > /home/ccrma/on-startup/$
                sudo -H -E -u ccrma /home/ccrma/on-startup/WeMUST/afterConnect.sh > /home/ccrma/on-startup/$
        elif [ -f  /home/ccrma/on-startup/load_default_patch ]; then
                sudo -H -E -u ccrma /home/ccrma/on-startup/load_default_patch
        fi
end script
```

(I know it is deprecated to have long scripts in the "script" stanza, I see if I can improve this later).
The abnormal behavior is with the wemust-start.sh script.

The wemust-start.sh script is quite long, and includes call to jackd, avahi, jacktrip and more, but there is NO reference whatsoever to itself, so I can't see how the script could initiate a new wemust-start.sh instance.

I know that the parent process to the periodically appearing instance is the first instance of wemust-start.sh from the following command:
ps -p `ps aux | grep [w]emust-start | awk 'NR == 2'{ print $2 }'` -o ppid=

So I read the second line (whenever it is not empty) of ps to get its pid and then send the pid to ps -o ppid to know what is the parent pid. The parent pid is the first wemust-start instance. The first instance has of course parent pid = 1.

Maybe the problem is with the conf file? I tried to mingle with the "expect" and "respawn" stanzas to no avail...
Any suggestions?

The entire .conf file:

```
description     "WeMUST daemon"

# starts at runlevel 2 after avahi
start on (runlevel [2]
        and started avahi-daemon)
stop on runlevel [016]

#expect fork
#respawn limit 2 1

pre-start script
        echo "[`date +"%m/%d/%Y %H:%M:%S"`] UPSTART: Starting wemust.conf startup job" >> /home/ccrma/on-startup/WeMUST/.globaldump
end script

script
        if [ -f /home/ccrma/on-startup/WeMUST/wemust-start.sh ]; then
                rm /home/ccrma/on-startup/WeMUST/wemust.log
                rm /home/ccrma/on-startup/WeMUST/afterConnect.log
                sudo -H -E -u ccrma /home/ccrma/on-startup/WeMUST/wemust-start.sh > /home/ccrma/on-startup/WeMUST/wemust.log &
                sudo -H -E -u ccrma /home/ccrma/on-startup/WeMUST/afterConnect.sh > /home/ccrma/on-startup/WeMUST/afterConnect.log &
        elif [ -f  /home/ccrma/on-startup/load_default_patch ]; then
                sudo -H -E -u ccrma /home/ccrma/on-startup/load_default_patch
        fi
end script

post-stop script
        killall wemust-start.sh
        killall afterConnect.sh
        echo "[`date +"%m/%d/%Y %H:%M:%S"`] UPSTART: Launched wemust.conf startup job" >> /home/ccrma/on-startup/WeMUST/.globaldump
end script

```

PLATFORM:
It's a BeagleBoard xM running Ubuntu 10.10 with a patched kernel.
Linux omap 3.2.2-x4 #1 SMP PREEMPT armv7l GNU/Linux
upstart is version 2010-02-04 0.6.5

---

