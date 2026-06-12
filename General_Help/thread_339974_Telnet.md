---
title: "Telnet"
date: 2007-01-16
forum: General Help
---

### Post by christodoulos77 on 2007-01-16
How do i enable telnet on ubuntu?

---

### Post by christodoulos77 on 2007-01-16
This is how i use it in my firewall

#Telnet
iptables -A INPUT -i $LAN_IN -p TCP --dport 23 -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -p TCP --sport 23 -j ACCEPT

---

### Post by schilcha on 2007-01-16
This is probably a question with a too-obvious answer, but anyways:

Have you checked that your telnet-server is up? Try:
```

netstat -lt

```
and see, if telnet is listed as port on the local-address-column.

---

### Post by dcstar on 2007-01-16
> **christodoulos77 said:**
> How do i enable telnet on ubuntu?

Incoming telnet is not installed as a default package, you just install it.

---

### Post by christodoulos77 on 2007-01-16
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 *:dict                  *:*                     LISTEN     
tcp        0      0 localhost:3557          *:*                     LISTEN     
tcp        0      0 *:4006                  *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp        0      0 *:webcache              *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 172.16.202.1:domain     *:*                     LISTEN     
tcp        0      0 172.16.26.1:domain      *:*                     LISTEN     
tcp        0      0 192.168.0.182:domain    *:*                     LISTEN     
tcp        0      0 192.168.1.1:domain      *:*                     LISTEN     
tcp        0      0 localhost:domain        *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 192.168.1.1:3128        *:*                     LISTEN     
tcp        0      0 localhost:953           *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp6       0      0 *:58400                 *:*                     LISTEN     
tcp6       0      0 localhost:6880          *:*                     LISTEN     
tcp6       0      0 localhost:45100         *:*                     LISTEN     
tcp6       0      0 *:www                   *:*                     LISTEN     
tcp6       0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 ip6-localhost:953       *:*                     LISTEN 

How Do I Install It As A Default?

---

### Post by seuaniu on 2007-01-16
The short answer to your question is this:

```


user@host$ sudo apt-get install telnetd


```

Or, if you're trying to avoid using a terminal, click system --> Administration --> Synaptic Package Manager, do a search for telnetd, and install it that way.

The long answer is a bit more difficult.  If you're running a firewall, you'll need to open up telnet's port.  There's a chance that the telnet server won't get started on install (I do not have it installed here), so you'll need to do something similar to:

```


user@host$ sudo /etc/init.d/telnetd start


```

Make sure to have a look at telnetd's config file, somewhere in the /etc directory.  there will be quite a few options there that you may want to change.  And, here's the default telnet rant:

Do not use telnet as a server.  It is not encrypted and transmits plain text information, including your username and password over the network.  ssh is a safer alternative if you want remote shell access.  Rant off :)

---

### Post by Wim Sturkenboom on 2007-01-16
Why do you want to install telnet? To access your box over the internet? In that case, don't. It's a security risk and you're better of with ssh (which encrypts the communication so passwords can't be snooped.
For local network, telnet is usually fine.

---

### Post by christodoulos77 on 2007-01-17
its for my local lan 

Thank you very much
I'll try it

---

### Post by christodoulos77 on 2007-01-17
Can I login from Windows to my Ubuntu using ssh?

---

### Post by christodoulos77 on 2007-01-17
I have another question

I loged-on my server using an Ubuntu LiveCD on another PC using ssh

Is there a way that I can use a graphical interface?

---

### Post by schilcha on 2007-01-17
> **christodoulos77 said:**
> Can I login from Windows to my Ubuntu using ssh?

Try the world-famous ssh-client for windows: PuTTY (don't know the web-page, but your favourite search engine will know)

Regarding your other question (graphical interface ...), try "ssh -X user@host". The "-X" will tell ssh to forward the X-stuff through the ssh-tunnel from the remote to the local machine.

---

### Post by christodoulos77 on 2007-01-17
> **schilcha said:**
> Try the world-famous ssh-client for windows: PuTTY (don't know the web-page, but your favourite search engine will know)

Regarding your other question (graphical interface ...), try "ssh -X user@host". The "-X" will tell ssh to forward the X-stuff through the ssh-tunnel from the remote to the local machine.

I try ssh -X user@host but i get 
"/usr/bin/X11/xauth: error in locking authority file /home/user/.Xauthority"

---

### Post by christodoulos77 on 2007-01-19
I found that with "xauth" I can do that 
but i don't understand how can i use this command

Can someone help?

---

### Post by schilcha on 2007-01-19
Hm, I see this message once in a while, but it usually goes away on a second try. You can try adding the command-line parameter "-v" to make ssh talk a little more about its problems. Maybe that'll give you some help. 
Is the ssh-server configured to forward X11-connections? (look for parameter X11Forwarding in the file /etc/ssh/sshd_config)

---

