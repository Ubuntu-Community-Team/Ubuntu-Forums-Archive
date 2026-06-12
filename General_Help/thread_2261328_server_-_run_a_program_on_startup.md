---
title: "server - run a program on startup"
date: 2015-01-18
forum: General Help
---

### Post by kieran6 on 2015-01-18
I know this question has been asked many times before, but after about 2 hours of searching I couldn't find a single helpful answer that would work for me.

Basically, I want to run a java "jar" in a screen session when the server boots (so when it turns on, restarts etc)

How I run the program at the moment is using the following:

```
screen -S screen1 -d -m java -Xms8G -Xmx8G -jar javafile.jar nogui
```

This works fine, but when I tried running something similar in a script inside /etc/init.d I didn't get the results I was hoping for.

What I'm looking for is for this screen session to be automatically initialized on boot, and if possible I'd also like to send something like this to the screen once it starts:

```
screen -S screen1 -X stuff "commands here $(printf \\r)"
```

Note: I have been running the scripts from the user "kieran" after logging in once the system boots, if that helps at all, and I'm hoping that I can still start this screen session before I've manually logged in.

Thanks in advance, any help is greatly appreciated

---

### Post by ian-weisser on 2015-01-18
Does the java application work without 'screen'?
 Are you using 'screen' simply to keep the application running after you logout?
Does the application need to run the entire time the server is up?

What kind of data does the java application provide?
What format is this data in?
Are you open to alternative applications?

Are you logging into the server at a physical text-only terminal/console? or via SSH? Or some other way?

---

### Post by Holger_Gehrke on 2015-01-18
> **kieran6 said:**
> How I run the program at the moment is using the following:

```
screen -S screen1 -d -m java -Xms8G -Xmx8G -jar javafile.jar nogui
```

This works fine, but when I tried running something similar in a script inside /etc/init.d I didn't get the results I was hoping for.


Just putting a script in /etc/init.d doesn't start it. You also need a link in one of the run level directories '/etc/rc[0-6].d' . 

Actually, init scripts are meant to control daemons and need to follow some conventions; take a look at '/etc/init.d/skeleton'.

I'd probably try putting it in /etc/rc.local, that gets called at the end of init and is meant for this kind of thing.

---

### Post by kieran6 on 2015-01-19
> **ian-weisser said:**
> Does the java application work without 'screen'?
 Are you using 'screen' simply to keep the application running after you logout?
Does the application need to run the entire time the server is up?

What kind of data does the java application provide?
What format is this data in?
Are you open to alternative applications?

Are you logging into the server at a physical text-only terminal/console? or via SSH? Or some other way?

Thank you both for the replies. The java application works perfectly without screen, however, I'm unable to do anything else with the server while the application is running hence why I run it in a screen so I can detach it to do other things. I don't logout so that's not something I need to worry about. The application does need to run the entire time the server is up. I'm not sure exactly what you mean by "what kind of data does it provide." if it helps at all it's simply running a game server that gets accessed by multiple clients, for that reason there are no "alternative applications" unfortunately.

> [COLOR=#000000]Just putting a script in /etc/init.d doesn't start it. You also need a link in one of the run level directories '/etc/rc[0-6].d' . [/COLOR]

[COLOR=#000000]Actually, init scripts are meant to control daemons and need to follow some conventions; take a look at '/etc/init.d/skeleton'.[/COLOR]

[COLOR=#000000]I'd probably try putting it in /etc/rc.local, that gets called at the end of init and is meant for this kind of thing.

Thank you. I have already tried putting it in rc.local, unfortunately I still got no results there either. I'm not sure if it's because it's trying to create the screen before I've logged in, and therefore failing or what the issue is :/[/COLOR]

---

### Post by nerdtron on 2015-01-19
Put it like this:
first create a script the contains your screen:
```
#/bin/bash
## set some sleep just to let the server completely boot up
sleep 30
screen -S screen1 -d -m java -Xms8G -Xmx8G -jar javafile.jar nogui
```

Save the file.
Now on the rc.local file, add the line that will run the script
```
/bin/bash /path/to/script.sh
```

As long as the script.sh is present and is able to run, startup will continue. I think it won't even wait for the 30 seconds. It will just call the file.


EDIT: does this even run correctly when you run from the terminal? If not, then we have to fix this first.
```
screen -S screen1 -d -m java -Xms8G -Xmx8G -jar javafile.jar nogui
```

---

### Post by Holger_Gehrke on 2015-01-19
> **kieran6 said:**
> if it helps at all it's simply running a game server that gets accessed by multiple clients, for that reason there are no "alternative applications" unfortunately.


So it actually is a daemon ? No interaction on the console ? Only interacts through the network or local sockets ?

Why not send it into the background from rc.local with its standard output and standard error sent to a log-file like this:
```

java -Xms8G -Xmx8G -jar javafile.jar nogui >> /var/log/javagameserver.log 2>&1 &

```

If it **is** a daemon, writing a real init-script and linking it in the appropriate run-level or setting up an upstart job is probably the right solution.

---

### Post by kieran6 on 2015-01-19
> **nerdtron said:**
> Put it like this:
first create a script the contains your screen:
```
#/bin/bash
## set some sleep just to let the server completely boot up
sleep 30
screen -S screen1 -d -m java -Xms8G -Xmx8G -jar javafile.jar nogui
```

Save the file.
Now on the rc.local file, add the line that will run the script
```
/bin/bash /path/to/script.sh
```

As long as the script.sh is present and is able to run, startup will continue. I think it won't even wait for the 30 seconds. It will just call the file.


EDIT: does this even run correctly when you run from the terminal? If not, then we have to fix this first.
```
screen -S screen1 -d -m java -Xms8G -Xmx8G -jar javafile.jar nogui
```

Thank you for your reply. I appended the script to match yours and ran it to ensure it works. It slept for 30 seconds and then launched the application perfectly.
I added the call to the script into rc.local and rebooted. The loading screen for the OS stayed up for an extra 30 seconds than usual (obviously due to the sleep command) so I know it is calling the script on boot, but then it loaded without launching the application. I know it wasn't launched successfully because a 'screen -ls' call showed no active screen sessions.

To answer your question about "does this even run correctly from the terminal" it certainly does. I launched it multiple times from that script just to be sure.

Thanks again for the help, it's much appreciated

---

### Post by Holger_Gehrke on 2015-01-19
> **kieran6 said:**
> 
I added the call to the script into rc.local and rebooted. The loading screen for the OS stayed up for an extra 30 seconds than usual (obviously due to the sleep command) so I know it is calling the script on boot, but then it loaded without launching the application. I know it wasn't launched successfully because a 'screen -ls' call showed no active screen sessions.


This is exactly the behaviour of screen if the command does not work. For example 'screen -S screen1 -d -m this-will-not-work-because-it-does-not-exist' does not display an error message or set a non-zero exit code. 

Do you have the absolute path to the jar file in the script ? Do you set any environment variables on login ($CLASSPATH in ~/bashrc or ~/.profile) which should be set before executing the jar file ?

---

### Post by kieran6 on 2015-01-19
Just an update, the java application does seem to be starting up on boot now, however I think it's being run by the root user as the screen still won't show up and I'm not able to connect to the service, I know it's running though as I get "server refused connection" errors when trying to connect and when trying to run the java application it won't start as "another application is running on that port"

I tried updating my script to look like this to fix the problem

```
#!/bin/bash
cd /home/kieran/game
su - kieran -c "screen -S screen1 -d -m java -Xms8G -Xmx8G -jar server.jar nogui"
```

This made absolutely no difference though. The server still loads but the screen is not accessible from the account "kieran"

EDIT:

> [COLOR=#000000]This is exactly the behaviour of screen if the command does not work. For example 'screen -S screen1 -d -m this-will-not-work-because-it-does-not-exist' does not display an error message or set a non-zero exit code. [/COLOR]

[COLOR=#000000]Do you have the absolute path to the jar file in the script ? Do you set any environment variables on login ($CLASSPATH in ~/bashrc or ~/.profile) which should be set before executing the jar file ?

Sorry I know I've only just figured this out now, but the jar file IS being started (see above) so the path seems to be correct (can also see the path above) as far as I'm aware no environment variables are set on login unless this is done automatically by Ubuntu Server, I usually just log in and run the script as is.

Thanks for you response![/COLOR]

---

### Post by kieran6 on 2015-01-19
Finally discovered a solution.

```
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/bash
[/FONT][/COLOR]cd /home/kieran/game
sudo -u kieran screen -S screen1 -d -m java -Xms8G -Xmx8G -jar server.jar nogui
```

I have no idea why this works when 'su - kieran blah blah' didn't, but it finally works! :D

Thanks again to everyone for the help!

---

### Post by ian-weisser on 2015-01-19
There are some best practices for running headless servers in the background:

- Don't run it using your login. If it's compromised, and the attacker gains a shell, that's really bad news. Best practice is to create a [system user]("http://ubuntuforums.org/showthread.php?t=1146686") ('fooserver') without shell access. The .jar file, associated data files, and the server's working directory should be owned by that system user, not you nor root.

- Use an [Upstart job]("http://upstart.ubuntu.com/cookbook/") in /etc/init/ (or systemd job starting in 15.04) to start the server automatically when the network becomes available. The server becomes a standard always-on service (daemon), just like lots of others running in the background, and eliminates all the mucking about with screen. To manually start/stop/restart the server, you use the 'service' command, just like for all the other services.


Example: A minecraft server.

```
sudo mv minecraft-server /srv/minecraft-server                 # Move the server dir out of your home directory, since you won't own it anymore.
sudo adduser --system --home /srv/minecraft-server  minecraftuser    # Create the system user
sudo chown -R minecraftuser /srv/minecraft-server               # Change minecraft files' ownership to the new user.

```

And create the Upstart job: /etc/init/minecraft
```
# description "start and stop the minecraft-server"
start on network-device-up
stop on shutdown

setuid minecraftuser
chdir /srv/minecraft-server
exec /bin/sh -c '/usr/bin/java -Xms1024M -Xmx1024M -jar server.jar nogui 2>&1 | logger -t minecraft'

respawn
respawn limit 20 5

```

---

### Post by Holger_Gehrke on 2015-01-19
> **kieran6 said:**
> Finally discovered a solution.

```
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/bash
[/FONT][/COLOR]cd /home/kieran/game
sudo -u kieran screen -S screen1 -d -m java -Xms8G -Xmx8G -jar server.jar nogui
```

I have no idea why this works when 'su - kieran blah blah' didn't, but it finally works! :D

Thanks again to everyone for the help!

It works because 'su - kieran' implies a cd to the home directory as it behaves as if you logged in as 'kieran', as you can see by executing 'cd /home/kieran/game; su - kieran -c 'pwd'. Your server.jar probably uses relative paths to find it's configuration files -- especially the users and their passwords -- and ends up in it's default configuration if it can't find them.

---

### Post by kieran6 on 2015-01-29
Just wanted to thank everyone again for the help. I now have it running as a daemon using init.d, and I made a script so I can access multiple functions such as "start|stop|restart|backup|command" etc from the "service" command. I even have crontab automatically executing the "backup" function every so often to provide a backup of the game's save files. Slightly strange issue with the crontab part though. While manually executing the backup function using service it sends input to the server fine using "stuff" and backs up the server, yet when crontab executes the same script, it does the backup but doesn't send the input to the server correctly. I'm sure I'll figure that out quickly though.

---

### Post by ian-weisser on 2015-01-29
Glad to see you found a solution that works for you, that you'll be able to maintain, and that is safe.

---

### Post by kieran6 on 2015-01-30
> **ian-weisser said:**
> Glad to see you found a solution that works for you, that you'll be able to maintain, and that is safe.

Indeed. Thanks to you. :)

Getting cron to do a screen -X stuff wasn't as simple as I had expected, still can't convince it to do so after hours of trying.

---

