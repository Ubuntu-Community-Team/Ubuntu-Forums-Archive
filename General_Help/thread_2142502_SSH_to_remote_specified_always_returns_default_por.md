---
title: "SSH to remote specified always returns default port 22"
date: 2013-05-05
forum: General Help
---

### Post by dongpt on 2013-05-05
Hey guys,

I believe my thread belongs to General section but if you guys think it should be under Networking, please Mod help to move into it.

I have on Ubuntu Server LTS 12.04 installed on physical machine. SSH default port is changed from 22 to 8889. My problem is when I try to connect other host which SSH default port is changed - SSH process always returns that I'm connecting to remote hosts with default port. 

- No any standalone firewall stands between those hosts.
- No forwarding rules applied in system firewall.

```
    root@ubuntu2:~# netstat -npl | grep :22
root@ubuntu2:~# netstat -npl | grep :8889
tcp        0      0 0.0.0.0:8889            0.0.0.0:*               LISTEN      1013/sshd       
tcp6       0      0 :::8889                 :::*                    LISTEN      1013/sshd       
root@ubuntu2:~# service ssh status
ssh start/running, process 1013
root@ubuntu2:~# ssh dongpt@'<my Centos server IP>' 2345
ssh: connect to host '<my Centos server IP>' port 22: Connection timed out
root@ubuntu2:~# ssh dongpt@'<an other Ubuntu server 12.04 IP>' 8888
ssh: connect to host '<an other Ubuntu server 12.04 IP>' port 22: Connection timed out
root@keeto2:~# telnet ubuntu2 8889
Trying 127.0.1.1...
Connected to ubuntu2.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1


```

My system informaiton:

```

root@ubuntu2:~# uname -a
Linux ubuntu2 3.5.0-28-generic #48~precise1-Ubuntu SMP Wed Apr 24 21:42:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

ps: I can connect from outside (Window) to this host via the changed SSH default port

Thanks!

---

### Post by steeldriver on 2013-05-05
unlike telnet (where you just append the port number), for ssh you need to specify it with the -p option

```
ssh [COLOR=#0000ff]**-p 8889**[/COLOR] dongpt@'<an other Ubuntu server 12.04 IP>'
```

---

### Post by dongpt on 2013-05-05
> **steeldriver said:**
> unlike telnet (where you just append the port number), for ssh you need to specify it with the -p option

```
ssh [COLOR=#0000ff]**-p 8889**[/COLOR] dongpt@'<an other Ubuntu server 12.04 IP>'
```

Your answer makes me laugh myself a lot :) But thanks, it works!

---

### Post by Lars Noodén on 2013-05-06
You might want to skim through the manual pages for the program [ssh](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh.1.html) and the configuration file [ssh_config](http://manpages.ubuntu.com/manpages/raring/en/man5/ssh_config.5.html).  On your Ubuntu system, the configuration file for the ssh client (ssh_config) will be found in ~/.ssh/config.  If it does not exist, you can create it.  It will be useful.

```

mkdir -m 700 ~/.ssh
touch ~/.ssh/config
chmod 600 ~/.ssh/config

```

One way the config file can help you with your current set up is to make a shortcut so you don't have to keep appending the non-standard port number when you connect.

```

Host ubuntu2
  Hostname *xx.yy.zz.aa*
  User dongpt
  Port 8889

```

Obviously substitute the host name or ip number for your machine for the field **Hostname**.  That will allow you to connect to your machine, on the right port, simply by typing **ssh ubuntu2**.  Many more tricks are available.

---

