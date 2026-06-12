---
title: "How to monitor background apps"
date: 2021-03-04
forum: General Help
---

### Post by tc2020 on 2021-03-04
I am developing an application software running on Ubuntu 20.04. It is made up of a few software modules, all running in background. Named pipes are used to pass data/info among these modules, so they are decoupled. Some of these modules use Ubuntu built-in daemons such as syslogd, snmpd, and others.

What I want to do is to develop and add a supervisor module to the application. This module is intended to monitor all other modules and also active daemons and somehow auto restart them if they are down. At the moment I am thinking of using named pipe to each of the modules for alive heartbeat/ping approach. I assume I can use process names for monitoring daemons.

My goal is to look for ways to improve overall software/system operational integrity. 

I am hoping to get some advice or engage with other members on the topic that may be of benefits to others as well.

Thanks.

---

### Post by HermanAB on 2021-03-04
If you save the *PID* when you launch a process, then you can check it with *ps*.

---

### Post by tc2020 on 2021-03-04
Thanks for your input. I will implement that PID check. This leads to my next question below.

Is there a way to make a daemon resilient; i.e. when it dies it can get restarted automatically, maybe through a .service configuration file for systemd?. That would simplify things a lot. If not, maybe I will add a new daemon with its sole purpose of monitoring the supervisor only and that both can check and restart each other.

---

### Post by HermanAB on 2021-03-05
There is/was a supervisory daemon called *inetd* that could be used to start and restart services.  

However, if it is only one service, then you can use a bash script with a *while loop* and a *sleep* statement, to restart a daemon if it would exit - after a 1 second delay.  It is important to wait for the dust to settle before launching the daemon again, otherwise it can fail immediately and the resulting fast spin can bog the whole machine down.

---

### Post by tc2020 on 2021-03-05
I had a quick read and inetd does not seem to fit, more for socket services. The 1 second delay is a good idea and I will keep that in mind instead of instant restart.

Effectively there is only one service (supervisor as I call it) that I want to make sure it's always up. I plan to use the while loop/sleep approach and basically every 30 seconds, it wakes up, checks status of supervisor, restarts it if needed, and goes back to sleep. Instead of a bash script as you suggested, I plan to have it run as a service and have supervisor (using the same while loop/sleep concept) to monitor/restart it as well. As mentioned earlier, these two monitor and restart each other to ensure both are up. I am not sure which is better/more reliable this approach vs bash script and cron. It would be great if Linux has some 'solid' service that once you have registered your services with it, it will make sure they are always up. Is there such a thing?.

---

### Post by HermanAB on 2021-03-05
I don't know whether this is still current and never used it myself (a Bash loop is good enough for me):
[https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps](https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps)

---

### Post by tc2020 on 2021-03-05
I had a look and yes it is available in Ubuntu server 20.04 LTS as I just installed it. It fits exactly what we are discussing here with your suggested bash script. I will add my other foreground programs for it to manage. This is perfect and thanks for your help.

My application has to be resilient for 24/7 unattended use, pushing a reset button on the box can be a venture and expensive... Thanks again!

---

### Post by Holger_Gehrke on 2021-03-05
> **tc2020 said:**
> 
Is there a way to make a daemon resilient; i.e. when it dies it can get restarted automatically, maybe through a .service configuration file for systemd?. That would simplify things a lot. If not, maybe I will add a new daemon with its sole purpose of monitoring the supervisor only and that both can check and restart each other.

You might want to read 'man 5 systemd.unit' (general format of a unit file), 'man 5 systemd.service' (format of a unit of type service; pay special attention to the keywords 'Restart' and 'WatchdogSec') and 'man 5 systemd.exec' (execution environment for processes started by systemd).

Holger

---

### Post by TheFu on 2021-03-05
> **tc2020 said:**
> Thanks for your input. I will implement that PID check. This leads to my next question below.

Is there a way to make a daemon resilient; i.e. when it dies it can get restarted automatically, maybe through a .service configuration file for systemd?. That would simplify things a lot. If not, maybe I will add a new daemon with its sole purpose of monitoring the supervisor only and that both can check and restart each other.

systemd can be setup to restart daemons, if you like. Probably want to limit the restart attempts to prevent infinite looping.

Most of the stuff described was solved decades ago. Look into daemon-tools for examples.  There are other existing solutions too.  I haven't needed anything more than careful logging to syslog. Monitoring and alarming are common on unix servers.
[https://www.tecmint.com/best-linux-log-monitoring-and-management-tools/](https://www.tecmint.com/best-linux-log-monitoring-and-management-tools/)
Zabbix, SysUsage, Nagios, OpenNMS, and similar tools can watch log files, send alarms, and create graphs.

named-pipes are fine, but not as flexible as sockets.

---

### Post by tc2020 on 2021-03-08
I have tried both supervisor (suggested by HermanAB) and systemd (suggested by Holger and TheFu). Both seem to do what I was looking for using my simple setup with RPi3 running Ubuntu 20.04 server LTS and a logger bash script.

Setup for supervisor,

 ```
[FONT=&amp]
$ sudo apt-get install supervisor    [/FONT]
[FONT=&amp]$ service supervisor restart   [/FONT]
[FONT=&amp]$ sudo nano /usr/local/bin/testscript.sh [/FONT]
  
  [FONT=&amp]#/!/bin/bash[/FONT]
  [FONT=&amp]while :[/FONT]

  [FONT=&amp]do[/FONT]
  [FONT=&amp]   logger $(date)[/FONT]
  [FONT=&amp]   sleep 30[/FONT]
  [FONT=&amp]done[/FONT]

[FONT=&amp]$ sudo chmod +x /usr/local/bin/testscript.sh [/FONT]
[FONT=&amp]$ sudo nano /etc/supervisor/conf.d/testscript.conf [/FONT]

  [FONT=&amp][program:testscript] [/FONT]
  [FONT=&amp]command=sudo /usr/local/bin/testscript.sh   [/FONT]
  [FONT=&amp]autostart=true   [/FONT]
  [FONT=&amp]autorestart=true       [/FONT]

[FONT=&amp]$ sudo supervisorctl reread                                    [/FONT]
[FONT=&amp]$ sudo supervisorctl update                         
[/FONT]
```

  
Setup for systemd,

 ```
[FONT=&amp]$ sudo nano /etc/systemd/system/testscript.service[/FONT]

  [FONT=&amp][Unit][/FONT]
  [FONT=&amp]Description= Time Logger testscript[/FONT]

  [FONT=&amp][Service][/FONT]
  [FONT=&amp]Type=simple[/FONT]
  [FONT=&amp]ExecStart= sudo /usr/local/bin/testscript.sh[/FONT]
  [FONT=&amp]Restart=always[/FONT]
 
  [FONT=&amp][Install][/FONT]
  [FONT=&amp]WantedBy=multi-user.target
[/FONT]
[FONT=&amp]$ sudo systemctl restart testscript.service[/FONT]

  

```
In both cases, testscript gets spawned immediately after a kill pid command.

TheFu, you mentioned Nagios, OpenNMS, etc... what are some of the well accepted/commonly used 'open/free' NMS platforms by IT?. I would like to test some.

Thanks for all the inputs.

---

### Post by HermanAB on 2021-03-08
Zabix and Nagios work well.  Zabix is easy to set up.

---

### Post by TheFu on 2021-03-08
In the ExecStart cmds above, no need for sudo.  Everything runs as root from these services.

I listed the commonly used open/free NMS tools.

---

### Post by tc2020 on 2021-03-09
I will look into Zabbix, Nagios, OpenNMS probably in a few weeks from now.

Initially I did not have sudo in both cases and the session terminated pretty much right away with a log message saying ..'code=exited, status=203/EXEC'...'Start request repeated too quickly'... With sudo, they both work... maybe something to do with permission. On systemd in working mode, it keeps count of how many restarts. I just wonder if there is any side effect if the count reaches certain number. I know software must be pretty bad to have high count but I have to think about this possibility.

Sudo is an interesting concept, letting users run things as root. In this application, I need to create two groups of users: sysadmin and genusers to control system access. For genusers, I want to limit them to certain directory and Linux commands (cat, ls, and other non-destructive commands), more like view only actions. With sudo, how would you do that as it allows genusers do anything they want to?. This may be off topic for this thread. I have to read up on this a bit more.

---

### Post by TheFu on 2021-03-09
> **tc2020 said:**
> 
...
On systemd in working mode, it keeps count of how many restarts. I just wonder if there is any side effect if the count reaches certain number. I know software must be pretty bad to have high count but I have to think about this possibility. 

Which is why I wrote:
> systemd can be setup to restart daemons, if you like. Probably want to limit the restart attempts to prevent infinite looping.
Are the scripts set to have execute permissions?  Is the first line (#!) of the script correct?  It **_must be the 1st line_**, not the first non-blank line.

Normal users don't get sudo rights.

---

### Post by tc2020 on 2021-03-09
I have (-rwxr-xr-x 1 root root 75 Mar  8 03:49 /usr/local/bin/testscript.sh) and #/!/bin/bash is on the first line (no preceeding blank line.. doubled checked).

My question was what if restart attempts have reached my limit, if I set it. Asked in a different way, what if a systemd default count has reached its value. Under this condition, does it stop working until next reboot?. Or, does it just continue watching the process?. In my testing, after each kill pid, it restarted and incremented count. It behaved quite consistently even when I kept running this command repeatedly (using up arrow key and cr).

---

### Post by Holger_Gehrke on 2021-03-10
'#[COLOR=#ff0000]/[/COLOR]!/bin/bash' ? I do think that's not quite right. And computers tend to be very literal ...

The limit for restarting is not a simple counter,  there are two options StartLimitIntervalSec and StartLimitBurst that can be given in a unit. Those give the number of times the unit may be started within a given interval. If a service gets restarted more often systemd stops running it. Of course a manual start with 'systemctl start servicename' overrides this condition.

Holger

---

### Post by TheFu on 2021-03-10
> **tc2020 said:**
>  #/!/bin/bash 

There's the problem. Sorry I missed it.

#!  <---- says the next part is the interpreter to be used.
/bin/bash  <--- says this is the exact path for the command interpreter that all remaining lines should be processed by.

```
#!/bin/bash

echo "hello world"

```
is the same as 
```
echo "hello world" | /bin/bash
```

Check out some first lines of other scripts on the system.  You'll see #! with a few different interpreters.

Computers do what we ask, not what we mean to ask.

---

### Post by Holger_Gehrke on 2021-03-10
```
echo "hello world" | /bin/bash
```

There's not enough echo in there ...

```
echo echo "hello world" | /bin/bash
``` 

Holger

---

### Post by TheFu on 2021-03-10
> **Holger_Gehrke said:**
> ```
echo "hello world" | /bin/bash
```

There's not enough echo in there ...

```
echo echo "hello world" | /bin/bash
``` 

Holger

a) You are quite correct.
b) Thanks for the laugh!
c) We are being serious - 2 echos are necessary.

---

### Post by tc2020 on 2021-03-10
My mistake... it works now without that first /

Linux is not my strong thing, a lot to explore. Going back to about 3  months ago, I thought sudo was some Japanese word... now I sudo  everything as you can see.

I will look into those two options, but sounds like hard to test. For  this application, I plan to have a system self reboot, say around 3AM  daily to clear things like this automatically. I also plan to $ ifconfig  eth0 down and then up once every hour to make sure network is up. Would  these regular actions upset IT people who look after the network?. Or,  in Linux, is there a better way to achieve this?. 

(I start to like this forum, will hang around more often for the humor...and of course, knowledge)

---

### Post by HermanAB on 2021-03-10
Linux machines can run for many years without ever needing a reboot.  
If you need to reboot, then you are doing something wrong.

---

### Post by TheFu on 2021-03-10
sudo abuse will lead to a broken system 

Rebooting a system daily?  That's definitely a Windows thing. No needed on Unix.

ifconfig is deprecated. Use the **ip** tool, but taking a system off the network is poor form.

Unix systems, they are expected to run great 24/7/365 for years without reboot.  

If you want a network service to be unavailable, just take that service down. Don't take the entire server off the network.

If you want to know that a system in on the network, use a monitoring tool like nagios ... or just setup a remote ping check process. If the ping fails, either take corrective action automatically or notify someone using an alarming tool.  You could page or email someone.

---

### Post by tc2020 on 2021-03-10
All sounds very comforting on Unix reliability, which is great!

How to make sure my 24/7 unattended system can correct itself for whatever fault that might be (and also make sure it is always reachable because of its remoteness) is the question that has been circling my head. That led to the idea of daily system reboot and frequent network reset. With your inputs, I now have to think about this a bit more...

---

### Post by TheFu on 2021-03-10
For very remote systems, you want a **remote serial console** capability. That needs to be fully locked down and not generally available over the internet, since most of those remote serial console devices have terrible security.  Google RIBLO, IPMI for some examples. Also google "IPMI hacked" to see the risks.  Using these, you can actually load a system over the network if someone local can plug in a flash drive or set a DVD into a drive bay on the system. The remote admin can completely power down the computer just like flipping the BRS, wait 5 minutes, then flip the BRS on. 
 In major company where I worked, all our servers had remote serial console connections for the sys admin team.  These capabilities are part of the server hardware design. They cannot be added later.

If there is only 1 connection method into a network, then you are basically screwed. Be prepared to drive out and touch the equipment if you can't talk someone local through the steps to recover.  Ensure there are redundant WAN connections and that the backup WAN connection is completely secured - 2FA is mandatory.

---

### Post by tc2020 on 2021-03-11
Yes for those devices/systems with console/craft port. We call that out of band system administration. Earlier on, we developed such products having dial-up modem with callback and specific challenge/response procedure (go back and forth 3-4 times), and also 30min-1hr lockout timer on failed attempts. Once logged in, your access/commands then go through RADIUS or TACAC+ servers for AAA. Dial-up is the only thing exposed to the outside world, so pretty secure I think.

For the application that we have been discussing in this thread, I need to think a bit more as Linux is new to me. The more I dig into it the more things I find useful and can solve issues, and also things that make it more difficult to handle. For instance, as of yesterday, I was looking into how to manage Ubuntu update/upgrade for this application (like how frequent should I upgrade, what type of system effects, should I do it interactively, and other considerations) and did (here goes sudo again...)

   $ sudo apt update && sudo apt upgrade -y

This updated the system fine, however, one of the drivers needs recompiling. It was compiled perfectly fine many times before but not now. Errors seem to come from the build-essential package, maybe missing some components/files. I am investigating now...

---

### Post by TheFu on 2021-03-11
Some reading about setup and mantenance:
[LIST]
[*][https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
[*][https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[/LIST]

---

