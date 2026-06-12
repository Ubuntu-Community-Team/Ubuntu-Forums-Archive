---
title: "start-up scripts"
date: 2007-06-12
forum: General Help
---

### Post by Cannon9559 on 2007-06-12
Hi guys here's an easy one for you.

I'm running a private teamspeak server ([www.goteamspeak.com](www.goteamspeak.com)), and a Battlefield 1942 server on my Ubuntu machine. I was wondering where I could add a script, and what the script should read, so that these services startup during boot instead of having to do it automatically. I would still like to see the battlefield 1942 server to start up in it's own terminal because it has a monitor on it that allows me to see who is on the server, what map it's currently playing, and other stats. It also allows me to administer the server while it is running. The TS server does not need to start in a terminal as i can adminstrate it via a web page.

Once again, I would like these services to start during boot, so that I don't have to be logged in to start or use them.......if at all possible. Thnx.

---

### Post by reclusivemonkey on 2007-06-12
You can add the commands you use to start the services normally into a script;

```

#!/bin/sh
/path/to/binary -flags

```

However, if this is a machine you are not permanently logged into you would really want to use screen. This allows you to start a service, but also log out without that process stopping. You can then log in and get back into the service. I used this when I ran a counter-strike server. You should be able to find some examples on the net. Although if you are running this service from your desktop which you are always logged in to this may be overkill.

---

### Post by Cannon9559 on 2007-06-15
I'm usually just logged in, and i hardly have to restart the computer itself. But when i do have to restart the computer then I have to open up the console twice and enter in the commands to start teamspeak and battlefield. The thing is with battlefield im running a mod called Dessert Combat 0.7, and this has a tendency to crash at random intervals(it can usually run for a couple of days, no hassle). So when BF does crash i have to manually enter in the command to start it up again, as i am new to serving BF i don't know what the command is to have the server automatically restart if it crashes. So this is why i would like the command line for BF to show up when logged in, the teamspeak doesn't matter(i don't think) because it uses a PID file.(???I might be mislead as to what the PID file is actually about). The other reason I want the terminal to start up when i log in is because the battlefield server shows it's status in the window, such as how many players are on, what players are on, what map is being played, etc.

---

### Post by Mr. C. on 2007-06-15
I'm afraid you are going to have to decide which you want.  Its either:

a) BF (and/or TS) is started by the system at boot, or

b) BF (and/or TS) is started by you when you log in

This is an either/or because for services the system starts for you, output is typically directed into a log file.  For programs you start from a terminal window, you have a terminal window available where output may go.

As you've indicated, BF sends its output to a terminal window; you want to see this terminal window when you log in, so you'll have to login immediately when you boot the server and start BF.

There is a service that will automatically start BF for you (inetd), but that would not provide you with the terminal-based status, so this won't suit your needs.

Probably the best solution would be to write a quick shell script that you start upon login, which loops continuously starting BF when BF exits prematurely.  It would look basically like:

```
#!/bin/bash

echo Starting...
while : ; do
  startBF
  wait
  echo Restarting...
done
```

MrC

---

### Post by reclusivemonkey on 2007-06-15
Personally I would recommed using screen; its not completely necessary, but will be good in case you ever go to remote servers.

This is how I started my CS:Source server;

```

#!/bin/sh
echo "Starting Cs:Source Server"
sleep 1
screen -A -m -d -S css-server ./srcds_run -console -autoupdate -game cstrike +ip 192.168.1.5 +map de_aztec +maxplayers 16 +mp_dynamicpricing 0 -tickrate 33

```

---

### Post by Mr. C. on 2007-06-15
Indeed, screen is a much better solution.

MrC

---

