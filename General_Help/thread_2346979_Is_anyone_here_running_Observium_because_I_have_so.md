---
title: "Is anyone here running Observium because I have some questions"
date: 2016-12-20
forum: General Help
---

### Post by cazz on 2016-12-20
They have no forum but they have a mailinglist but I wonder if someone here use the program


I have a questions

How can I edit device name right now it have the devices ip numbers as names.
I have try with 

```
sudo php rename_device.php <ipnr> <newname>
```

But I got

```
NOT renamed. Could not resolve newname
```

---

### Post by cazz on 2017-01-01
A little update here

Observium works greate but I can't still change the hostname??

---

### Post by dragonfly41 on 2017-01-01
I am not a user of Observium .. never heard of it before you posted.

But you can see that error message in this post (4 years old).

[https://gist.github.com/dobber/5901818](https://gist.github.com/dobber/5901818)

Perhaps add some debug lines into renamehost.php to find out more?

The error message is printed on ...[COLOR=#333333][FONT=Consolas]       // Failed DNS lookup

The mailing archive list seems to be dead.[/FONT][/COLOR]

---

### Post by cazz on 2017-01-01
Thanks for the fast replay
hmm that give me some more to go on but is strange

I can ping a server with IP address but not the hostname.
Have never think about that Before

But the both servers (that server that running Observium and the other server that I want to monitor) have the nameserver 192.168.1.1 that is my router 
I can't ping the other servers with the hostname but I can ping google.com

---

### Post by dragonfly41 on 2017-01-01
[http://dns.squish.net](http://dns.squish.net) is a useful tool to resolve problems

[Later edit] Further clues found here ..

[http://serverfault.com/questions/314864/cant-ping-one-server-of-two-by-name-but-can-ping-both-by-ip](http://serverfault.com/questions/314864/cant-ping-one-server-of-two-by-name-but-can-ping-both-by-ip)

---

### Post by cazz on 2017-01-01
mm is strange
I can ping google.com but not another server on my local LAN

I Think I have to start a new thread about my ping problem.

---

### Post by dragonfly41 on 2017-01-01
I see .. local LAN .. then try looking for clues in here ...

[http://askubuntu.com/questions/462643/pinging-computers-on-local-network-destination-host-unreachable](http://askubuntu.com/questions/462643/pinging-computers-on-local-network-destination-host-unreachable)

---

### Post by cazz on 2017-01-01
Thanks for the replay.
I did make it easy for med and edit host file so it now can understand what i want to go with the hostname.

---

