---
title: "Screen not able to be resumed after running on startup (server 14.04)"
date: 2014-06-19
forum: General Help
---

### Post by ryan91 on 2014-06-19
EDIT: Fixed the problem, had to run the program from rc.local as ryan.
new rc.local
```
#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

su -c 'cd /home/ryan/minecraft && ./srvr' ryan &
exit 0
```


I am having trouble with screen. I am using it to start a minecraft server, and to do this I am attempting to run it on startup using a shell script that is started by rc.local.

rc.local
```

#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


sh '/home/ryan/minecraft/srvr'


exit 0

```

/home/ryan/minecraft/srvr
```

#!/bin/sh
/usr/bin/screen -dmS "msrv"
/usr/bin/screen -S msrv -p 0 -X stuff "cd /home/ryan/minecraft^M"
/usr/bin/screen -S msrv -p 0 -X stuff "java -Xmx2048M -Xms1024M -jar minecraft_server.jar nogui^M"

```

Now, when I reboot, I am expecting a screen to be running, detached, and to have a minecraft server running in it. However, after logging in to ryan and typing 'screen -r' the console outputs that 'There is no screen to be resumed'. Now this would seem to indicate that the script was not executed, yet when I run my minecraft client and go into my multiplayer tab, I can connect to my minecraft server. So I have no idea why this is happening. 

If anyone could give me some advice, it would be greatly appreciated.

---

