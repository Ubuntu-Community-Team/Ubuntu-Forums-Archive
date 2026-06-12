---
title: "Python Script only works when run from terminal, not from cron"
date: 2023-01-05
forum: General Help
---

### Post by AwaitingUserInput on 2023-01-05
**Edit **I want to clarify that the path is not the problem. Other commands within the python script execute just fine. It's specifically the [COLOR=#a52a2a][FONT=courier new]nmcli radio wifi ...[/FONT][/COLOR] commands that don't do anything.

Kubuntu 22.04

I wrote a python script to reset my wifi connection. It does this by sending to the shell: [COLOR=#a52a2a][FONT=courier new]nmcli radio wifi off[/FONT][/COLOR], waiting 6 seconds and then sending [COLOR=#b22222][FONT=courier new]nmcli radio wifi on[/FONT][/COLOR].


The actual line in the Python script:
```
subprocess.run('nmcli radio wifi off'.split(' '))
```


If I run the script manually from a terminal it works fine and it dosen't require sudo or anything like that. But if the script runs as a cron job, then it seems that those commands don't get executed; the wifi doesn't get turned off. Any ideas why? Is there some weird permission thing happening that's different from me as a logged-in user and the cron jobs that belong to my user account?

---

### Post by #&amp;thj^% on 2023-01-05
This is something that I'll forget to do,>>> added the statement path  to command the top of crontab.
Based off some notes I've kept, The default PATH for cron jobs is just /usr/bin:/bin, so if you want to run 
anything outside of those directories you need to either use an explicit path 
to the binary, or set the PATH variable in the crontab file.

---

### Post by HermanAB on 2023-01-05
With cron, it is best to use the full pathname for every command called.

---

### Post by #&amp;thj^% on 2023-01-05
> **HermanAB said:**
> With cron, it is best to use the full pathname for every command called.

+1
This may help if your script still fails to execute: [https://gist.github.com/alberthdev/85aa09a6640ce64bb10655a3d9f75f4c](https://gist.github.com/alberthdev/85aa09a6640ce64bb10655a3d9f75f4c)

---

### Post by TheFu on 2023-01-05
> **AwaitingUserInput said:**
> 
If I run the script manually from a terminal it works fine and it dosen't require sudo or anything like that. But if the script runs as a cron job, then it seems that those commands don't get executed; the wifi doesn't get turned off. Any ideas why? Is there some weird permission thing happening that's different from me as a logged-in user and the cron jobs that belong to my user account?

Just to extend what others already said.  processes run under cron have a minimal environment.  This is very different from a full session environment, like a user who logs in gets.  BTW, this bites everyone.  Cron doesn't run the initialization files like login does, so your ~/.profile and ~/.bashrc settings aren't picked up for any crontab program.

To see the differences, put 1 command into your crontab  and run the same command from a shell.  Just have the crontab output be redirected to /tmp/file.cron and the shell output redirected to /tmp/file.shell.

Now use any diff tool you like, 'meld' is the best I know, and compare /tmp/file.cron to /tmp/file.shell.  See all the differences? That's likely why the cron job fails.  Of course, YMMV.

+1 for using the full path to any program called.  Never trust the PATH in any script.  That's a good way to have unexpected results.

---

### Post by #&amp;thj^% on 2023-01-05
> **TheFu said:**
> Never trust the PATH in any script.  That's a good way to have unexpected results.

Exactly,  I used "PATH" as a point to, so I'll correct that in my first reply, I can see that would be confusing. (Thanks for calling that out)

---

### Post by AwaitingUserInput on 2023-01-05
Thanks, but the issue is not the path in the crontab. I already have an absolute path to the Python script in crontab. And there are other bash/shell commands within the Python script that run just fine. It's only turning off the wifi connection that doesn't work.

These shell commands work OK even when cron is the one running the script: 

[LIST]
[*]iperf3 to measure network speed
[*]ps aux to check if rsync is running
[*]sending text to /dev/pts/0 to warn me that the network is about to get reset
[/LIST]

All of these work OK, it's just the nmcli commands that get skipped when running the script via cron. If I manually run it from a terminal, everything works.


Here is a piece of the Python script though you don't really need it to understand the problem that I'm having.
```
def reset_network(speed):
    message = (datetime.datetime.now().strftime('%a %H:%M: ') + f'Network is {speed} MB/s. Restarting in 15 seconds.').encode()
    
    pts = os.open('/dev/pts/0', os.O_RDWR)
    os.write(pts, message)
    time.sleep(15)
    subprocess.run('nmcli radio wifi off'.split(' '))
    time.sleep(6)
    subprocess.run('nmcli radio wifi on'.split(' '))
    os.close(pts)

```

---

### Post by TheFu on 2023-01-05
subprocess.run('nmcli radio wifi off'.split(' '))

That isn't using the full path to the program.  nmcli needs to be /usr/bin/nmcli --- or something like that

The web-based manpage does say something about needing access to GConf, which holds keys needed to do things.  Under cron, those keys aren't available.  Check your local manpage about this to be certain.  Don't trust web manpages, since they aren't likely to be for the same version of the program you have installed.

Rather than using a workaround, why not just setup netplan to bring up the wifi interface system-wide and solve any issues with that directly?

---

### Post by #&amp;thj^% on 2023-01-05
See if this helps:[https://askubuntu.com/questions/1294631/program-that-disable-wifi-automaticly](https://askubuntu.com/questions/1294631/program-that-disable-wifi-automaticly)
It's pretty detailed with options.
mines just a basic:
```

import os
import time
from datetime import datetime
import sys

while(1):
    now = datetime.now()
    if now.hour == 0:
        print("Starting Wifi...\n")
        os.system("nmcli radio wifi on")
    if now.hour == 6:
        print("Turning Wifi off...\n")
        os.system("nmcli radio wifi off")
        sys.exit()
    time.sleep(60)
```

---

