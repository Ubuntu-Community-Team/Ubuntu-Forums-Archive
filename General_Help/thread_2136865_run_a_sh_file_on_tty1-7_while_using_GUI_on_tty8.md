---
title: "run a sh file on tty1-7 while using GUI on tty8"
date: 2013-04-18
forum: General Help
---

### Post by ada101 on 2013-04-18
Firstly, if this post is in the wrong topic, feel free to move. I found "General Help" the most relevant.

I  currently have a minecraft server running normally on the GUI server  tty8 via a terminal emulator. I would like to be able to move the server  to tty1-7 so that I can do whatever using the normal GUI tty.

The server uses Ubuntu 12.10 with the specs being:
-Intel Core i7-2630QM Processor 6M Cache, up to 2.90 GHz
-8GB DDR3 Ram
-Cat6 Gigabit Ethernet
-750GB 5200RPM WD Blue SATA
-Intel HD3000/Nvidia 520MX
I know how to log in to a tty and start a server but I would like to do the following:
I want the computer to start up normally and default to the tty8 GUI logon screen while on the server tty I want:
-auto login to server user (username is "mcserver")
-run this shell file:
```
#!/bin/sh
Pause()
{
 OLDCONFIG=`stty -g`
 stty -icanon -echo min 1 time 0
 dd count=1 2>/dev/null
 stty $OLDCONFIG
}
 
echo "Hit a key to start the server..."
Pause
echo "Server starting....."

sh ~/mcs/craftbukkit.sh

```
Thanks for any help, it is appreciated :>

---

### Post by Slim Odds on 2013-04-18
run it from rc.local (without the pause).
Otherwise, you'll just have to open a console manually (Ctrl-Alt-F1) and do it yourself.

---

### Post by ada101 on 2013-04-18
rc.local? I have found it in /etc/. Do I just paste the script in there? How will rc.local know to log in as mcserver and how will it know which tty to load up on?
Currently, the rc.local looks like this: 
```
#!/bin/sh -e
#
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

exit 0
```

Thanks :)

---

### Post by SeijiSensei on 2013-04-19
Looks like the actual command to start the server is "sh ~/mcs/craftbukkit.sh".  Just put that above the "exit 0" line and reboot.

---

### Post by Slim Odds on 2013-04-19
> **ada101 said:**
> rc.local? I have found it in /etc/. Do I just paste the script in there? How will rc.local know to log in as mcserver and how will it know which tty to load up on?
Currently, the rc.local looks like this: 
```
#!/bin/sh -e
#
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

exit 0
```

Thanks :)
Servers normally run as root. Why do want it to run as a specific user?

---

### Post by matt_symes on 2013-04-19
Hi

I would attempt to do this a different way than suggested so far. For choice i'll elucidate.

For auto login, install mingetty

```
sudo apt-get install mingetty
```

Which ever console you want to auto login edit the ttyX.conf file.

In his example

```
sudo nano /etc/init/tty1.conf
```

Change the last line from

```
exec /sbin/getty 38400 tty1
```

to read


```
exec /sbin/mingetty --autologin USERNAME tty1
```

Change USERNAME to the correct user.

There is also the -f switch for /bin/login but i have not played with that.

You can then run a script. Place it in

```
.bash_profile
```

You may have to create it. This script get sourced for a bash login shell.

in the script you can check the current tty

```

TTY=$(tty);

if [[ "$TTY" == "/dev/tty1" ]];
then

  run script.

fi
```

The script will run on the correct tty under the correct users credentials.

If i understand your post correctly, this is kind of what you want.

Kind regards

---

### Post by matt_symes on 2013-04-19
Hi

> **Slim Odds said:**
> Servers normally run as root. Why do want it to run as a specific user?

I have never set up a minecraft server so i'm interested in this question.

My assumption is security.

Kind regards

---

### Post by ada101 on 2013-04-19
So many replies! Lets get down to it then :D
> **Slim Odds said:**
> Servers normally run as root. Why do want it to run as a specific user?
A Minecraft Server running as root? Firstly, its java, and I don't trust Java. Too many exploits. Type "run minecraft server as root" into Google and look at the captions of the results.
> **matt_symes said:**
> Hi

I would attempt to do this a different way than suggested so far. For choice i'll elucidate.

For auto login, install mingetty

```
sudo apt-get install mingetty
```

Which ever console you want to auto login edit the ttyX.conf file.

In his example

```
sudo nano /etc/init/tty1.conf
```

Change the last line from

```
exec /sbin/getty 38400 tty1
```

to read


```
exec /sbin/mingetty --autologin USERNAME tty1
```

Change USERNAME to the correct user.

There is also the -f switch for /bin/login but i have not played with that.

You can then run a script. Place it in

```
.bash_profile
```

You may have to create it. This script get sourced for a bash login shell.

in the script you can check the current tty

```

TTY=$(tty);

if [[ "$TTY" == "/dev/tty1" ]];
then

  run script.

fi
```

The script will run on the correct tty under the correct users credentials.

If i understand your post correctly, this is kind of what you want.

Kind regards
Will try this approach tommorow, sounds promising :D It is currently 3AM in my time zone, so not now ;)
> **matt_symes said:**
> Hi



I have never set up a minecraft server so i'm interested in this question.

My assumption is security.

Kind regards
As I said before, Java :) .
> **SeijiSensei said:**
> Looks like the actual command to start the server is "sh ~/mcs/craftbukkit.sh".  Just put that above the "exit 0" line and reboot.
I don't want the server to start every time I use the PC. If I stick a pause in, I can just leave the tty paused until I want the server on again.

---

### Post by efflandt on 2013-04-19
There is no need to run a minecraft server as root, since it does not use any low ports (default port 25565) and is safer that way.

When someone on the Raspberry Pi forum asked how to boot right into a text terminal (tty) program as a specific user, I was not aware of the **mingetty --autologin** parameter, but I found an **autologin** ksh script and did a little web page about how to do that in /etc/inittab in place of a regular getty, and then launch the text terminal program from ~/.profile for that user. Raspberry Pi is an ARM computer on a credit card size circuit board (for $35) that boots a Debian wheezy version called Raspbian from SD card, so it is easy to customize an SD card for specific use (Ubuntu is also Debian based). One thing that the autologin script did not set was $TERM, so I had to set TERM=linux in ~/.profile.

So you may gain some useful information from this, which does not even launch any gui, but boots right into quake3 launched from a tty: [http://efflandt.freeshell.org/rpi-web/autotermrun.html](http://efflandt.freeshell.org/rpi-web/autotermrun.html)

---

### Post by ada101 on 2013-04-20
matt_symes, I used this method in virtualbox last night, and it worked!!!! Thank you so much everyone for your input, and a big thanks to matt_symes for your method! I now have to install this stuff on my server pc. They both run the same OS, so should both be the same :). Here is a screenshot of the server running off of tty1 in virtualbox:
[IMG]http://i34.tinypic.com/347w3ep.png[/IMG]
Will post here if I have any problems installing on the server :).

> **matt_symes said:**
> Hi

I would attempt to do this a different way than suggested so far. For choice i'll elucidate.

For auto login, install mingetty

```
sudo apt-get install mingetty
```

Which ever console you want to auto login edit the ttyX.conf file.

In his example

```
sudo nano /etc/init/tty1.conf
```

Change the last line from

```
exec /sbin/getty 38400 tty1
```

to read


```
exec /sbin/mingetty --autologin USERNAME tty1
```

Change USERNAME to the correct user.

There is also the -f switch for /bin/login but i have not played with that.

You can then run a script. Place it in

```
.bash_profile
```

You may have to create it. This script get sourced for a bash login shell.

in the script you can check the current tty

```

TTY=$(tty);

if [[ "$TTY" == "/dev/tty1" ]];
then

  run script.

fi
```

The script will run on the correct tty under the correct users credentials.

If i understand your post correctly, this is kind of what you want.

Kind regards

---

### Post by ada101 on 2013-04-21
Okay, the actual server is running fine with the server in tty3. The CPU fan is running loud tho, so I went and looked up the processes in System Monitor, and, the process "getty" is running at 96-100% load:
[IMG]http://i38.tinypic.com/34pi1qo.png[/IMG]

"java" is obviously my server (Minecraft servers use a lot of ram, I only have 5 players on!), "nmon" is the CPU load in the second half of the pic and "gnome-system-monitor" is the system monitor in the top half of the screenshot.


_***Should I start a new thread or un-mark this thread as solved and post here as this looks like another issue?***_

---

### Post by matt_symes on 2013-04-21
Hi

First, as an addendum to my post, i was wracking my brains thinking i had missed something...

TTY is already set and i believe it's set before .bash_profile is started so this

```
TTY=$(tty);  
if [[ "$TTY" == "/dev/tty1" ]]; 
then    
run script. 
fi
```

can be changed to this

```
if [[ "$TTY" == "/dev/tty1" ]]; 
then    
run script. 
fi
```

> Should I start a new thread or un-mark this thread as solved and post here as this looks like another issue?

Lets see :) Some questions.

With the exact same setup in virtualbox, did you get the high loads you are getting on getty that you are seeing on your main server ?

What is the load on mingetty ?

Please post the output of (with your server under load)

```
ps aux | grep getty
```

and also

```
top -n 5 -p $(pgrep -d "," getty) 
```

It will take 5 seconds to complete. Post that back here as well.

Which tty has the main load ? The one you are running the minecraft server on ? The one that is running your window manager ? An unrelated on ?

Can you post the script you are using to run minecraft.

Kind regards

---

### Post by ada101 on 2013-04-21
> With the exact same setup in virtualbox, did you get the high loads you  are getting on getty that you are seeing on your main server ?
Surprisingly not! Here is the load on virtualbox:
[IMG]http://i34.tinypic.com/24grvjd.png[/IMG]
> What is the load on mingetty ?
there is no process called "mingetty".
there are 5 getty processors tho, 4 of them are idle and 1 is (tty3, the desktop i'm running minecraft on) running at 96-100%
> 
Please post the output of (with your server under load)
```
ps aux | grep getty
```
and also
```
top -n 5 -p $(pgrep -d "," getty)
```
It will take 5 seconds to complete. Post that back here as well.

```
adam@adam-laptop ~ $ ps aux | grep getty
root      1306  0.0  0.0  19976   972 tty4     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty4
root      1310  0.0  0.0  19976   972 tty5     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty5
root      1320  0.0  0.0  19976   972 tty2     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty2
root      1322 99.9  0.0  19976   972 ?        RNs  Apr21 893:19 /sbin/getty -8 38400 tty3
root      1325  0.0  0.0  19976   976 tty6     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty6
adam     15428  0.0  0.0  13588   928 pts/0    S+   12:08   0:00 grep --colour=auto getty

adam@adam-laptop ~ $ top -n 5 -p $(pgrep -d "," getty)

top - 12:12:53 up 14:58,  3 users,  load average: 1.36, 2.13, 2.41
Tasks:   5 total,   1 running,   4 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.9 us,  9.7 sy,  3.2 ni, 85.9 id,  0.3 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   8085792 total,  3382968 used,  4702824 free,   279364 buffers
KiB Swap:  8980476 total,        0 used,  8980476 free,   992044 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1322 root      39  19 19976  972  812 R  99.9  0.0 897:47.74 getty             
 1306 root      20   0 19976  972  812 S   0.0  0.0   0:00.00 getty             
 1310 root      20   0 19976  972  812 S   0.0  0.0   0:00.00 getty             
 1320 root      20   0 19976  972  812 S   0.0  0.0   0:00.00 getty             
 1325 root      20   0 19976  976  812 S   0.0  0.0   0:00.00 getty   
```
> Which tty has the main load ? The one you are running the minecraft  server on ? The one that is running your window manager ? An unrelated  on ?
I'm running the server on tty3 and the window manager on tty8. all the other tty's are at the login prompt other than tty1 and tty7 which are just blank. I'm running the server on tty3.
> Can you post the script you are using to run minecraft.
.bash_profile:
```
#!/bin/sh
Pause()
{
 OLDCONFIG=`stty -g`
 stty -icanon -echo min 1 time 0
 dd count=1 2>/dev/null
 stty $OLDCONFIG
}
 
echo "Hit a key to start the server..."
Pause
echo "Server starting....."

sh ~/mcs/craftbukkit.sh
```
craftbukkit.sh:
```
#!/bin/sh
 BINDIR=$(dirname "$(readlink -fn "$0")")
 cd "$BINDIR"
 java -Xmx4096M -Xms1024M -jar craftbukkit.jar
```

---

### Post by matt_symes on 2013-04-21
Hi

Some things noticed instantly.

That getty has a nice level of 19 pretty much the lowest you can get.

cpu idle is at 85.9.

Does the laptop feel slugish at all ?

Let's try something a second, but read through this entire post before entering this command.

Open a terminal and type
```

sudo renice -1 -p **1322**
```

Enter your password. It will not be echoed to the screen.

The bolded 1322 is the pid of the getty that was causing you the problems. 

This will have changed if you have stopped Minecraft or rebooted your laptop.

You can find the pid again by running top.

After running the renice command please re-run the ps and top commands and post the output back here.

There are things i need to check.

Kind regards

---

### Post by ada101 on 2013-04-22
> That getty has a nice level of 19 pretty much the lowest you can get.
Yup, I put the "getty" process on 19 myself:
[IMG]http://i37.tinypic.com/sgqslt.png[/IMG]
This was so other programs could run faster and become higher prioritized if need be.
> This will have changed if you have stopped Minecraft or rebooted your laptop.
I did reboot it once to see if this would fix the issue. I did this before posting the CPU issue tho :) no reboots since.
```
sudo renice -1 -p **1322**
```
Is obviously gonna turn the priority back to normal
Here is the output anyways:
```
adam@adam-laptop ~ $ sudo renice -1 -p 1322
[sudo] password for adam: 
1322 (process ID) old priority 19, new priority -1
```
Here are those commands again:
```
adam@adam-laptop ~ $ ps aux | grep getty
root      1306  0.0  0.0  19976   972 tty4     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty4
root      1310  0.0  0.0  19976   972 tty5     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty5
root      1320  0.0  0.0  19976   972 tty2     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty2
root      1322 99.9  0.0  19976   972 ?        R<s  Apr21 1206:08 /sbin/getty -8 38400 tty3
root      1325  0.0  0.0  19976   976 tty6     Ss+  Apr21   0:00 /sbin/getty -8 38400 tty6
adam     20764  0.0  0.0  13588   932 pts/3    S+   17:21   0:00 grep --colour=auto getty
adam@adam-laptop ~ $ 
```
```
adam@adam-laptop ~ $ top -n 5 -p $(pgrep -d "," getty)

top - 17:23:32 up 20:09,  4 users,  load average: 1.15, 1.21, 1.22
Tasks:   5 total,   1 running,   4 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.5 us,  9.3 sy,  0.0 ni, 86.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8085792 total,  3722840 used,  4362952 free,   304512 buffers
KiB Swap:  8980476 total,        0 used,  8980476 free,  1085400 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1322 root      19  -1 19976  972  812 R 100.2  0.0   1208:18 getty             
 1306 root      20   0 19976  972  812 S   0.0  0.0   0:00.00 getty             
 1310 root      20   0 19976  972  812 S   0.0  0.0   0:00.00 getty             
 1320 root      20   0 19976  972  812 S   0.0  0.0   0:00.00 getty             
 1325 root      20   0 19976  976  812 S   0.0  0.0   0:00.00 getty             
```
Here is "top" with no arguments:
```
adam@adam-laptop ~ $ top

top - 17:24:53 up 20:10,  3 users,  load average: 1.27, 1.25, 1.23
Tasks: 189 total,   2 running, 187 sleeping,   0 stopped,   0 zombie
%Cpu(s):  5.7 us,  9.8 sy,  0.0 ni, 84.0 id,  0.4 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   8085792 total,  3725744 used,  4360048 free,   304580 buffers
KiB Swap:  8980476 total,        0 used,  8980476 free,  1083268 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1322 root      19  -1 19976  972  812 R 100.2  0.0   1209:38 getty             
 2949 mcserver  20   0 8170m 1.4g  13m S   3.7 17.9  42:49.48 java              
 1429 root      20   0  141m  21m 7044 S   3.3  0.3  12:06.98 Xorg              
19810 adam      20   0 1124m 302m  45m S   3.3  3.8   2:46.68 firefox           
19868 adam      20   0  548m  18m  11m S   2.0  0.2   0:02.13 gnome-terminal    
 2406 adam      20   0 1661m 162m  27m S   1.7  2.1  10:25.85 cinnamon          
20536 adam      20   0  527m  89m  25m S   0.7  1.1   0:06.78 plugin-containe   
  641 root      20   0     0    0    0 S   0.3  0.0   3:07.00 rts5139-polling   
20680 root      20   0     0    0    0 S   0.3  0.0   0:00.03 kworker/u:0       
    1 root      20   0 24452 2448 1368 S   0.0  0.0   0:00.87 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.01 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.90 ksoftirqd/0       
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.05 migration/0       
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.07 watchdog/0        
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.47 migration/1       
   10 root      20   0     0    0    0 S   0.0  0.0   0:02.90 ksoftirqd/1       
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.10 watchdog/1        
   12 root      rt   0     0    0    0 S   0.0  0.0   0:00.04 migration/2       

```
Thanks for all the help so far :) you have been amazing

---

### Post by matt_symes on 2013-04-22
Hi

There are a couple of things i really don't understand about this.

You have one tty running getty at 100%. getty is a program that prompts for login credentials that it then passes onto /bin/login for validation. Once validated it will run bash (or other program configured).

If minecraft is running on that tty then there should be no getty process running on it and certainly no getty process running at 100%.

On that tty mingetty should have auto logged the minecraft user in and it should be running bash with mincraft as a child process.

This makes no sense.

To make sure i was no going mad, i have just set it up on my netbook and it works as expected.

Check and then double check your configuration. Something is wrong with it.

Post all the configuration files you changed.

Take a look at this.

```
matthew@matthew-S206:~$ ps ux | grep tty2
matthew   1452  0.0  0.1  26904  3788 tty2     S+   11:32   0:00 -bash
matthew   1531  3.2  0.0  30508  2668 tty2     S+   11:32   0:35 /usr/bin/htop
matthew   3110  0.0  0.0  13624   912 pts/0    S+   11:50   0:00 grep --color=auto tty2
matthew@matthew-S206:~$ 
```

tty2 is running bash and htop.

```

matthew@matthew-S206:~$pstree -p 1452
bash(1452)&#9472;&#9472;&#9472;htop(1531)
matthew@matthew-S206:~$
```

mingetty auto logged and ran bash. bash then started htop. You can see this from the output of pstree above. htop is a child process of bash.

Something is wrong with your configuration here.

EDIT: 

Here are my configuration files:

```

matthew@matthew-S206:~$ cat /etc/init/tty2.conf 
# tty2 - getty
#
# This service maintains a getty on tty2 from the point the system is
# started until it is shut down again.

start on runlevel [23] and (
            not-container or
            container CONTAINER=lxc or
            container CONTAINER=lxc-libvirt)

stop on runlevel [!23]

respawn
#exec /sbin/getty -8 38400 tty2
exec /sbin/mingetty --autologin matthew tty2
matthew@matthew-S206:~$ 
```

```

matthew@matthew-S206:~$ cat .bash_profile 
if [[ "$TTY" == "/dev/tty2" ]];
then

/usr/bin/htop;

fi
matthew@matthew-S206:~$ 
```



Kind regards

---

### Post by ada101 on 2013-04-22
Wow, you are going to think i'm an idiot when I say this. 
I put
```
exec /sbin/mingetty --autologin mcserver tty**3**
```
Into
```
/etc/init/tty**1**.conf
```
instead of
```
/etc/init/tty**3**.conf
```

The CPU is running fine now. Thanks for all of your help guys though it seemed to be my idiocy not a problem with your instructions t.t.

This thread is now officialy [SOLVED] :)

---

### Post by matt_symes on 2013-04-22
Hi

I don't think you're an idiot. 

If you knew the number of times i have done things like that you would double over laughing :D

I'm glad it's fix. Enjoy minecraft.

Kind regards

---

