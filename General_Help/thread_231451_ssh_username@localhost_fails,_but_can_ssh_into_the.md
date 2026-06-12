---
title: "ssh username@localhost fails, but can ssh into the computer from another computer"
date: 2006-08-07
forum: General Help
---

### Post by Tauceti38 on 2006-08-07
I've run into an unusal problem with ssh. I've set up a central fileserver for our network and have been working on getting backuppc working to make it easy to restore any lost files. Unfortunatly I keep getting a ssh error when I try to restore files.
The strange part is that I log into the fileserver from a windows machine through ssh every day. But when I log onto the server through ssh, using putty, and type ssh username@localhost (replacing username with a valid username) I get the error: 
ssh: connect to host localhost port 22: connection refused.
There are no firewalls on the server that could be closing port 22. I have a firewall set up on the router, but it allows all trafic between machines on the network.
Any suggestions on ways to fix this?

---

### Post by Ramses de Norre on 2006-08-07
Is ssh properly installed? I got the exact same error here and fixed it with ```
sudo aptitude install ssh
```
You'll need to run this on _both_ machines.

---

### Post by mlind on 2006-08-07
Yeah, you probably need **openssh-server** package (which is provided by transitional **ssh** package)

---

### Post by Tauceti38 on 2006-08-07
I was using the openssh packages before but went ahead and installed ssh as well like you suggested, unfortunatly I still can't connect to localhost.

I think I didn't quite state my problem clearly.
I can ssh into the fileserver from a windows machine using Putty just fine.
However, running the command ssh username@localhost (with a real username) on the fileserver fails giving me the error:
ssh: connect to host localhost port 22: Connection refused.

I need to get ssh username@localhost to work properly on the fileserver because the backup software uses ssh to restore backups, even if its restoring to the computer the server runs on, and the restore fails since ssh can't connect to localhost.

---

### Post by Ramses de Norre on 2006-08-07
Ignore this..

---

### Post by mlind on 2006-08-07
ssh username@localhost should work fine if your /etc/hosts maps localhost to 127.0.0.1.

I guess you don't have router either?

---

### Post by NewWithoutClue on 2006-08-07
Can you connect at all? maybe via nc, telnet, or even hping..

is it just blah@hostname that is not working?

Paul

---

### Post by Tauceti38 on 2006-08-07
I checked the /etc/hosts file and localhost is mapped to 127.0.0.1. I tried replacing localhost with 127.0.0.1 and the ip address, neither of which worked.
I just tried connecting with telnet but recieved the error:
telnet: could not resolve username@localhost
Nc localhost 22 gave the following error:
localhost [127.0.0.1] 22 (ssh) : Connection refused
I tried a different username and tried root (bad practice I know, just wanted to check it once) for both telnet and ssh, but recieved the same errors.

Here's a bit more information about my network setup:
The network consists of about 10 windows XP computers and a single ubunut fileserver. All of this is hooked into a switch, which is connected to a custom router, which connects to the internet. There are no firewalls on the fileserver, and the firewall on the router is configured not to block any traffic originating inside the network. All of the computers use DHCP to obtain an ip address, but the router is set to give a specific ip address to each computer, including the fileserver.

Thanks for all the suggestions so far.

---

### Post by slakkie on 2006-08-07
Hi,

Please check the following:


Wow, I mis read the title, please check the following line in your sshd_conf:

```

ListenAddress 0.0.0.0

```

I think you have mapped this to the IP set on one of your interfaces. 

I cannot open a connection to localhost if the config is set to my IP address:

```

grep -i listen sshd_config 
ListenAddress 192.168.1.9

18:37 [wesleys@nomad:/etc/ssh] # netstat -an | grep :22
tcp        0      0 192.168.1.9:22          0.0.0.0:*               LISTEN     
tcp        0     48 192.168.1.9:22          194.134.32.192:4598     ESTABLISHED
18:38 [wesleys@nomad:/etc/ssh] # ssh localhost
ssh: connect to host localhost port 22: Connection refused
18:38 [wesleys@nomad:/etc/ssh] # 

```

This I will leave, maybe others can use it.

```

# first of all, check wheter you have the sshd daemon installed:
dpkg --list | grep ssh-server
ii  openssh-server                    4.2p1-7ubuntu3                          Secure shell server, an rshd replacement

# If you have this, check wheter sshd is running:
18:26 [wesleys@nomad:/etc/init.d] # ps -ef | grep sshd     
root      4566     1  0 Aug06 ?        00:00:00 /usr/sbin/sshd

# Check wheter the service is listening on port 22:
18:28 [wesleys@nomad:/etc/init.d] # netstat -na | grep :22 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     

#If you haven't started the sshd yet:
/etc/init.d/ssh start

# And please check wheter you have root logins disabled in your 
# sshd config. I found out that Ubuntu sets this default to yes, 
# which is a bad thing IMO. Make sure you have a line like this:
# PermitRootLogin no
grep -i root /etc/ssh/sshd_config

```

---

### Post by Tauceti38 on 2006-08-07
Well, it wound up being a very simple problem. I'd forgotten I'd changed the port ssh used to a non standard port when I set it up, and that was causing all the trouble. Thankfully I noticed that the port number was different when I was looking to see what the listen address was set to. Works great once I add in the right port to use.

I always tell people that 9 times out of 10 the problem is the simplest thing you can think of, but always forget to follow my own advice. Thanks for all your help.

---

### Post by mnml on 2007-11-03
> **Tauceti38 said:**
> Well, it wound up being a very simple problem. I'd forgotten I'd changed the port ssh used to a non standard port when I set it up, and that was causing all the trouble. Thankfully I noticed that the port number was different when I was looking to see what the listen address was set to. Works great once I add in the right port to use.

I always tell people that 9 times out of 10 the problem is the simplest thing you can think of, but always forget to follow my own advice. Thanks for all your help.

lol thanks for the solution , i was gettin crazy :(

---

