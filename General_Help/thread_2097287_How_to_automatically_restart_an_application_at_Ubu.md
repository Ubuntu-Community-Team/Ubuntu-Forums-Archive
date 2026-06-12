---
title: "How to automatically restart an application at Ubuntu"
date: 2012-12-22
forum: General Help
---

### Post by aman pal on 2012-12-22
Hello everyone!

I've recently installed some BF2 servers on Linux Ubuntu 10.04 and i run them by using mono application. Though sometimes, the server crush and i have to access again to te root server, close mono apllication and restart it again. Anyone knows how can i manage to automaticaaly restart this application without having to login to the root server and restart it automatically? I've searched for this and found some info on some scripts that could make it done, but they all are quite different so i cannot have a clue if they will work. Can you help on this subject?

Thank and best regards

---

### Post by Cheesehead on 2012-12-22
My preferred way is to use Upstart to respawn a crashed process (server).

Upstart is Ubuntu's version if process #1 (init). Upstart includes features to start the system upon boot, start processes in response to signals, respawn (optionally) crashed processes, start/stop/restart daemons, and much more.

This means that you can make starting your server part of the boot cycle, starting it after the network comes up. Using upstart properly will also make your server respond to the [FONT="Courier New"]service foo start/stop/restart[/FONT] commands.

Upstart runs as root, or course. It can start/respawn non-root (user-level) applications.

The way to use Upstart is to write a .conf file and place it in /etc/init

Writing a .conf file is detailed at [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

### Post by aman pal on 2012-12-23
I see! It's not the root server that is crushing, only the "mono" application! Using upstart or monit or daemon are kind of difficult ways to me, since i'm not a Pro in script programming or any other kind of programming stuff! Isn't there any easier way of doing it, or at least a smaller script to use?

Best regards

---

### Post by 3rdalbum on 2012-12-23
> **aman pal said:**
> I see! It's not the root server that is crushing, only the "mono" application! Using upstart or monit or daemon are kind of difficult ways to me, since i'm not a Pro in script programming or any other kind of programming stuff! Isn't there any easier way of doing it, or at least a smaller script to use?

Best regards

Unfortunately I haven't done any Bash scripting, but you could do something similar to this:

While True: program.executive

Obviously this is not Bash language, you would need to find how to write that in Bash. But it is a very simple loop:

Execute "program.exe". If the program stops running for any reason at all, the script continues. It re-enters the loop again and runs program.exe and pauses itself until the program stops. Then it re-enters thr loop... Etcetera, etcetera.

I'm sure if you use Google you will find a code snippet that will be much more refined, and you can just copy and paste it into a text file and run it. I can write it in Python but I don't have access to a Linux computer at the moment.

---

### Post by rnerwein on 2012-12-23
> **aman pal said:**
> I see! It's not the root server that is crushing, only the "mono" application! Using upstart or monit or daemon are kind of difficult ways to me, since i'm not a Pro in script programming or any other kind of programming stuff! Isn't there any easier way of doing it, or at least a smaller script to use?

Best regards
hi
here a little script you can start e.g. from a terminal in the background:
#!/bin/bash
# simple watchdog for a process
# start the process and if the process is gone -> restart it
while :
do
    /bin/sleep 10 &   # start your process here - sleep must be changed to your process
    Child=$!    # pid of the forked child
    while :
    do
        /usr/bin/stat /proc/$Child >/dev/null 2>&1  # is the process id still present ?
        if [ $? -ne 0 ]
            then
                echo "will restart the process"  # your process is gone
                break
        fi
        sleep 5   # checking interval - you can use another one
    done
done

if the pid is gone and you will be shure it's your process you can inster:
cat /proc/${Child}/status | grep name_of_the_process_you_started
cheers

---

### Post by aman pal on 2012-12-26
Thanks for the help but i need to ask some questions still...

1- That script should be saved on wich folder in order to always monitor the process?

2-  "/bin/sleep 10 &   # start your process here - sleep must be  changed to your process" My process is ran by accesing the folder  (servers/karkand) and then running the .exe with mono through the  command: screen mono bf2ccd.exe -ranked

What should i write on that line?

3- "Child=$!    # pid of the forked child"

Pid??  23821.pts-0.rootserver -> is this what you mean?

I'm sorry but i'm kind of a beginner in programming, so this might take a while to solve. Meanwhile thanks for all the help

Best regards

---

### Post by Cheesehead on 2012-12-27
I think you're making this much more complicated then it needs to be.

For example, here's an upstart script. Name it [FONT="Courier New"]myserver123.conf[/FONT] or anything else you like, and place it in /etc/init . Use sudo when you place it - upstart runs as root, of course.

```
# myserver123 - regular myserver123 daemon

description	"myserver123 background daemon"

start on net-device-up
stop on net-device-down

respawn

exec /usr/bin/myserver123
```

The server starts after the network comes up. You can change that.
The server stops when the network goes down. You can change that.
It will respawn if it crashes.

You will need to change the [FONT="Courier New"]exec[/FONT] line to match the name of the application or script you want to launch.

---

### Post by aman pal on 2012-12-28
Ok i will try that one Cheesehead! Thanks. I'll post the feedback when i get some results! 

Best regards

---

### Post by Cheesehead on 2012-12-28
Edited the script to fix a rather fatal typo.

---

### Post by aman pal on 2012-12-28
Ok so i've created the following file: server_restart.conf

```
# server_restart - regular server_restart daemon

description    "server_restart background daemon"

start on net-device-up
stop on net-device-down

expect fork
respawn

exec /root/servers/karkand/screen mono bf2ccd.exe -ranked
```As you see the application or the command line that i have to use to restart the application is: screen mono bf2ccd.ex -ranked. I don't know if it will work but now i have to wait for the application "mono" to crash to see if it is really working. I'll post the feedback when i get the results.

Thanks for all the help. Best regards

---

### Post by aman pal on 2012-12-29
Well it seems that it is working when restarting the application. There is one problem! Without the script and before when "mono" application crashed it would automatically restart but didnt load all the server. It would stay at 38% of 100%. So i had to shut down this application that had restarted to create a new one so it could fully load to 100%.

So now with the script besides respawning the application, mono is automatically and as before restarting the application so i get two "screens" with different pids but running the same application. One with the automaticac mono restart that doesnt fully loads, and another one restarted by the script you just gave me that isn't working because there is already the other one restarted....

My question is if i can shut down the automatic restart of the application when it crash made by the mono application so it can only be respawned or restarted by the script i just placed there, when the application crash??

Thanks and best regards

---

### Post by Cheesehead on 2012-12-29
Are you sure that a failed restart is really what is happening?

For example, your're telling scree to run mono, then telling mono to run bf2ccd.exe. When the .exe crashes, maybe it's crashing mono, but maybe not. And a crashed mono may not terminate screen.

So perhaps you are actually seeing the old, uncrashed screen running uncrashed mono instead of some kind of failed restart.

Check the PIDs upon startup to see what started and when, and then after a crash see what is still running.

Upstart includes the ability to run pre-start and post-stop commands, too. You can use those to clean up mono and screen before respawning.


On a separate note, why do you need to run screen at all? Upstart scripts run as root, and independent of any user session. If you were using screen to keep the process alive between logins, you don't need it if you use Upstart. Try it without screen and see how that affects the problem.


Also, if you're running a public-facing server (like a gameserver), you probably shouldn't be running public-facing services as root. If the service can be exploited, you just gave the attacker root access. A separate system-user with limited permissions and no shell is normally created to run those services.

---

### Post by aman pal on 2012-12-30
The processes were running in different PID's. One for the failed mono application restart, with the loading stuck at 38%, and another PID for the respawn from upstart you gave me... Before implementing the script, the PID stayed the same but the application only went at 38%. But mono will not fully load if another mono is running the same application. That's why i need upstart to close the failed mono restart (the one that gets stuck at 38%). I only use screen because like you said if i close the root access software the application will close and with it the game server goes offline. This is also due to the fact that i run 4 servers at different folders and without screen i cannot start another server without shuting down the window i just ran, for example of one of the servers...

So i'm getting kind of lost here...

Best regards

---

### Post by Cheesehead on 2012-12-31
Since mono is handling any forking, remove 'expect fork' from the script.

Since mono crashes are probably being caught by screen instead of passing uphill to init, remove 'screen' from the script. As written, upstart will respawn if 'screen' (not mono) crashes, and root does not need to run a screen session to keep the server alive.

See if those two changes help.

---

### Post by aman pal on 2013-01-02
ok ill give that a try! Thanks again

Best regards

---

### Post by aman pal on 2013-01-17
Ok let me try to explain it better cause i'm a noob in this kind of stuff and maybe i'm not explaining good the situation.

First i know that i should have installed the servers and run them with another account created besides root, but now its too late because i have some statistics related to the game servers also installed as root wich i cannot re-install again because i dont know how to do it so i cannot operate now as another user... or can i?

So this is the situation...

I have 4 servers installed, each one of them in different folders. To start the servers through the executable i have to run the command "screen mono bf2ccd.exe" in each one of the folders or else, in case i just run it without "screen" i wont be able to start more than one server or even close the ssh access software putty without closing the apllication or in this case server that is running... 

So after i run the command "screen mono ....exe" i have to start the server with a Control Center (BFCC) called "admin tool" so that the server starts loading from 0% to 100%... I haven't seen the server crushing. The only thing i see is that when the server is down i go to putty, open the screen where the server is running (through his PID id) and i see that the server stopped loading at 27%, so it is like if it has crushed... The truth is that i don't really know what happened. Just know that the application can't restart.

I know this is a bit confusing without looking directly into the problem but i will try to explain it even better if it is necessary, maybe through images...

Can you now see better what the problem is? Can i make anything about it? Sorry for the big post

Best regards

---

