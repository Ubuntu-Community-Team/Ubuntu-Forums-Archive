---
title: "fail2ban ignores my bantime"
date: 2013-09-06
forum: General Help
---

### Post by piramiday on 2013-09-06
I've installed fail2ban in order to ban ssh attackers, but even though my jail looks like this:
```
[ssh]
enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 1
findtime = 300 # 5m
bantime  = 86400 # 24h
```
when I start the fail2ban service I get the following:
```
fail2ban.filter : INFO   Set maxRetry = 1
fail2ban.filter : INFO   Set findtime = 600
fail2ban.actions: INFO   Set banTime = 600
fail2ban.jail   : INFO   Jail 'ssh' started
```
how come my find/ban times are NOT what I configured?

---

### Post by TheFu on 2013-09-06
Did you restart both Fail2Ban AND sshd?
Are there any errors reading the config file?

Changed it in the **jails.conf** file and this was the result:

```
2013-09-06 07:14:46,075 fail2ban.filter : INFO   Set maxRetry = 6
2013-09-06 07:14:46,077 fail2ban.filter : INFO   Set findtime = 600
2013-09-06 07:14:46,077 fail2ban.actions: INFO   Set banTime = 86400
2013-09-06 07:14:46,107 fail2ban.jail   : INFO   Jail 'ssh' started
```

On Ubuntu Srv 12.04.3 with LXDE loaded.

I put a 35 second setting into **filter.d/sshd.conf** and that was NOT taken. Don't know why not.

I don't know if this is an option for you, but if you have the router do port translation from any other port - perhaps 63099 on the internet to port 22 on the server, 95% of the attempts will go away.  Then on the clients, setup the ~/.ssh/config file to automatically use whatever port you select for that specific server connection.  Almost every ssh-based program will honor the ~/.ssh/config settings so there isn't any need to pass the port into those commands.

BTW, changed the time in the jails.conf file again 
```
2013-09-06 07:22:11,642 fail2ban.filter : INFO   Set maxRetry = 6
2013-09-06 07:22:11,643 fail2ban.filter : INFO   Set findtime = 600
2013-09-06 07:22:11,643 fail2ban.actions: INFO   Set banTime = 6400
2013-09-06 07:22:11,671 fail2ban.jail   : INFO   Jail 'ssh' started
```
See - it works.

---

### Post by piramiday on 2013-09-06
> [COLOR=#000000]Did you restart both Fail2Ban AND sshd?[/COLOR]
I tried restarting both, even though restarting the ssh service is not necessary: the maxretry keyword is indeed successfully updated after a fail2ban restart.

> [COLOR=#000000]Changed it in the [/COLOR]**jails.conf file**
I've followed a few guides available on the web, meaning that I copied the jail.conf to a 'local' file, jail.local, and I put my personalized settings there (the .local file overrides the .conf file, and my maxretry modification confirms this).

> [COLOR=#000000]I don't know if this is an option for you, but if you have the router do port translation from any other port - perhaps 63099 on the internet to port 22 on the server, 95% of the attempts will go away. Then on the clients, setup the ~/.ssh/config file to automatically use whatever port you select for that specific server connection. Almost every ssh-based program will honor the ~/.ssh/config settings so there isn't any need to pass the port into those commands.[/COLOR]
unfortunately that is not an option, because at my workplace connections to non-standard ports have to be authorized by the system administrator... I have to stuck with port 22. btw since you're mentioning it, I tried with a non-standard port a few days ago, specifying it in my jail.local file, and fail2ban did NOT ban at all.

just to be sure, I tried the following: I put 4 different values in 4 various config files: bantime=100 in jail.conf [default], bantime=200 in jail.conf [ssh], bantime=300 in jail.local [default] and bantime=400 in jail.local [ssh]. I stopped fail2ban and started it again, and what did it happen? bantime still equals 600. :S

---

### Post by TheFu on 2013-09-06
Remove the comments from the "time" field lines.  I suspect comments only work on separate lines.

Or have you tried that?

---

### Post by piramiday on 2013-09-06
thanks TheFu, I arrived at the same conclusion just a few minutes ago, having read:
> # Comments: use '#' for comment lines and ';' for inline comments
... this means that the problem was indeed my comment!

solved. :popcorn:

---

