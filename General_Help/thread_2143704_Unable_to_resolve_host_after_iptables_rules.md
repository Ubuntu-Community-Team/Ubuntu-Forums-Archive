---
title: "Unable to resolve host after iptables rules"
date: 2013-05-09
forum: General Help
---

### Post by pedrommone on 2013-05-09
I've ran the following rules:

```
[COLOR=#000000][
"iptables --flush",
"iptables -P INPUT DROP",
"iptables -P FORWARD DROP",
"iptables -P OUTPUT DROP",
"iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --sport 53 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i lo -j ACCEPT",
"iptables -A OUTPUT -o lo -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7171 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7175 -m state --state NEW,ESTABLISHED -j ACCEPT"
][/COLOR]
```

Now Im getting this error

```
ubuntu@ip-10-252-5-178:/etc$ sudo su
sudo: unable to resolve host ip-10-252-5-178
```

when I try to run any command, whats wrong with the rules? Thanks in advance.

---

### Post by The Cog on 2013-05-09
DNS uses udp, not tcp (usually).

You have a weakness. I can connect to any port on your box by making sure my source port is 22, 53 or 80. You probably don't need to allow new connections incoming at all, and if you do you probably want to worry about the destination port, not the source port.

---

### Post by pedrommone on 2013-05-10
This server is running as a ssh proxy, so everyone connects with port 22 and I block all outputs, except 7171 and 7175.

---

### Post by pedrommone on 2013-05-10
Also, now I cant connect to mysql server and I cant make curl requests, whats wrong with my rules?

---

### Post by The Cog on 2013-05-10
Sorry, I wasn't clear enough. 

Resolving hosts requires using DNS protocol (port 53) to a name server. But DNS normally uses UDP, not TCP. You are allowing TCP:53 out but not UDP:53. Try allowing udp:53 out and in again.

Also, you are allowing 7171,7175 out but not allowing the return packets back in, so these won't work.
Try adding these 4 lines:
```
"iptables -A OUTPUT -o eth0 -p udp --dport 53 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --sport 53 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --sport 7171 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --sport 7175 -m state --state ESTABLISHED -j ACCEPT",

```

And I was wrong about the weakness allowing connections in from port 22. I didn't read the rules carefully enough. Oops.

Since a connection can't become established unless the first (new) packet was allowed anyway, you can probably simplify by just allowing any established connections in or out.
The whole thing becomes:
```

[
"iptables --flush",
"iptables -P INPUT DROP",
"iptables -P FORWARD DROP",
"iptables -P OUTPUT DROP",
"iptables -A INPUT -i eth0 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i lo -j ACCEPT",
"iptables -A OUTPUT -o lo -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 80 -m state --state NEW -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 53 -m state --state NEW -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p udp --dport 53 -m state --state NEW -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7171 -m state --state NEW -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7175 -m state --state NEW -j ACCEPT"
]

```

---

### Post by pedrommone on 2013-05-10
Now Im using those rules

```
[COLOR=#000000][
"iptables --flush",
"iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i lo -j ACCEPT","iptables -A OUTPUT -o lo -j ACCEPT",
"iptables -A INPUT -p tcp --dport 22 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 22 -j ACCEPT",
"iptables -A INPUT -p tcp --dport 80 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT",
"iptables -A INPUT -p udp --dport 53 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p udp --dport 53 -j ACCEPT",
"iptables -A INPUT -p tcp --dport 3306 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 3306 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7171 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7175 -j ACCEPT",
"iptables -P INPUT DROP",
"iptables -P OUTPUT DROP",
"iptables -P FORWARD DROP"
][/COLOR]
```

What do you think?

---

### Post by The Cog on 2013-05-11
That's looking pretty good. I'll just add a few comments on some lines:

"iptables -A OUTPUT -o eth0 -p tcp --dport 22 -j ACCEPT",
Allows making outgoing connections to other SSH servers. I didn't think you wanted that.

"iptables -A INPUT -p tcp --dport 80 -j ACCEPT",
Allows incoming connections to your web service. I didn't think you were running a webserver.

"iptables -A INPUT -p udp --dport 53 -j ACCEPT",
Allows incoming connections to your DNS server. I didn't think you were running a DNS server.


"iptables -A INPUT -p tcp --dport 3306 -j ACCEPT",
Allows incoming connections to your mysql server. I hope that's not publicly accessible. You may want to restrict which source addresses can connect to it, to keep the hackers at bay.

"iptables -A OUTPUT -o eth0 -p tcp --dport 3306 -j ACCEPT",
Allow outgoing connections to other people's mysql servers.

I wonder if you're confusing in/out and client/server with source/dest port numbers. Just in case, here's a short explanation.
When a client connects to a service, the client generally calls **from** a random port number, typically > 1024.
But the server he connects to must be listening on a well-known port number, e.g. 80 is usual for http web servers.
So the connection ends up being something like client:1025 - server:80. So for controlling access to services, you need to control access to the server port number (80, 22 etc).
When a client makes a new connection, it is always the client that calls the server, so the server's port number is always the destination port number.

If you are allowing new outgoing connections, use the OUTPUT chain and allow connections to the destination server port number.
If you are allowing new incoming connections, use the INPUT chain and allow connections to the destination server port number.
The remainder of the connection is always taken care of by the ESTABLISHED ACCEPT rule.

---

### Post by pedrommone on 2013-05-11
Well, I'm running a proxy server, so the 'entrance' port is 22 and the output port is 7171 and 7175, my rules now are:

```
[COLOR=#000000][
"iptables --flush",
"iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i lo -j ACCEPT",
"iptables -A OUTPUT -o lo -j ACCEPT",
"iptables -A INPUT -p tcp --dport 22 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p udp --dport 53 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 3306 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7171 -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7175 -j ACCEPT",
"iptables -P INPUT DROP",
"iptables -P OUTPUT DROP",
"iptables -P FORWARD DROP"
][/COLOR]
```[COLOR=#000000]

They are okay now?[/COLOR]

---

### Post by The Cog on 2013-05-11
They look good to me.

---

### Post by pedrommone on 2013-05-11
Ok, thanks mate!

---

