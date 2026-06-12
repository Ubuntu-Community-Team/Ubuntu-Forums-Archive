---
title: "OpenSSH Question"
date: 2008-06-01
forum: General Help
---

### Post by ShinHadoken on 2008-06-01
Say I'm going to log into a friend's machine using SSH. SSH (by default) uses port 22. My friend's machine, as well as other pcs in the house, are behind a router. How do I connect to him? Do I forward port 22 to his pc? What would I do then if I wanted to connect to a different pc behind the same router?

---

### Post by jpkotta on 2008-06-01
Most NAT routers will allow you to forward an inbound port to a different port.  For example, I have inbound 40022 going to port 22 on my desktop and 18022 going to port 22 on my server.  I use the weird ports because it minimizes the chance that some random person on the internet will see my open ports.

---

### Post by Monicker on 2008-06-01
Yes, you need to port forward at the router.  Depending on the particular router, you would either use a different port at the external ip and forward  to 22 on a different machine, or you might need to change the ssh port on the other machine you want to connect to.

The ssh port can be changed in /etc/ssh/sshd_config.  You can also configure a  machine to listen on several different ports for ssh.

---

### Post by ShinHadoken on 2008-06-01
Ok, cool. Any side-effects I should know about in changing the default port SSH listens to?

---

### Post by quelx on 2008-06-01
> **ShinHadoken said:**
> Ok, cool. Any side-effects I should know about in changing the default port SSH listens to?

Just that any program the tries to connect to **sshd** will need to have the port set to whichever you decide to use.

Most ssh capable applications will default to **22** but also give you the option to change it.

---

### Post by ShinHadoken on 2008-06-01
One question: Say I set up my buddy's router to forward inbound port 9922 to port 22 on his machine. What command line arguements do I need to pass to cause "ssh user@buddysip" to connect over port 9922?

---

### Post by quelx on 2008-06-01
> **ShinHadoken said:**
> One question: Say I set up my buddy's router to forward inbound port 9922 to port 22 on his machine. What command line arguements do I need to pass to cause "ssh user@buddysip" to connect over port 9922?

```
ssh -p9922 user@buddysip
```

---

### Post by ShinHadoken on 2008-06-01
Duh, sorry. Had a blonde moment, lol. Cool then! Now if I can just get Snort working...

---

### Post by mbeach on 2008-06-01
On the question on how to get to more than one machine behind the router, you can use that one connection to create a tunnel to the others.  It'll likely take a moment to get the hang of it, but it allows you to open up only the one port (rather than one for each machine), then port forward through your ssh connection.  Putty does a nice job of assisting in setting up the tunnels, but you can use the command line as well. 

First description I found on the web - there are probably many more:
[http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall](http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall)

---

### Post by ShinHadoken on 2008-06-02
> **mbeach said:**
> On the question on how to get to more than one machine behind the router, you can use that one connection to create a tunnel to the others.  It'll likely take a moment to get the hang of it, but it allows you to open up only the one port (rather than one for each machine), then port forward through your ssh connection.  Putty does a nice job of assisting in setting up the tunnels, but you can use the command line as well. 

First description I found on the web - there are probably many more:
[http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall](http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall)
Umm, ok, lemme see if I got this straight... I'll forward port 22 to HostA, and then type 

ssh user@buddysip -L 22:hostB's private ip:22

to connect to hostB, my buddy's machine.

...right?

---

### Post by mbeach on 2008-06-02
The port after the -L is the port that you want to forward your local machine to, to get to the final port.  Since you are already using 22 to make the initial connection, use another.

Initial connection:
ssh user@buddysip -L 2222:hostBsPrivateIP:22

Then on your local machine, I belive you'd use ssh again with something like:
ssh -P2222 properuser@localhost
where properuser is a user on HostB.

I've actually never used it to ssh, usually VNC.

good luck,
mb

---

### Post by mbeach on 2008-06-02
actually - that may not work - let me toy with it a bit.

---

### Post by ShinHadoken on 2008-06-02
I *think *I get it..

Instead of this:

Ext Port 11122 --> HostA Port 22
Ext Port 22222 --> HostB Port 22
Ext Port 33322 --> HostC Port 22

I get this:

Ext Port 22 --> HostA Port 22
                      HostA Port 11122 --> HostB Port 22
                      HostA Port 22222 --> HostC Port 22

How do I connect then?

---

### Post by mbeach on 2008-06-02
actually, once you've ssh'd into the first machine, just start another ssh session to hostb from hostA's terminal.

---

### Post by ShinHadoken on 2008-06-03
So I would go:
 
**ssh hostAuser@buddysip -L 2222:hostBsPrivateIP:22**
 
to set it up, then:
 
**ssh hostAuser@buddysip**
**ssh hostBuser@buddysip**
 
?
 
Or, since I'm logging in from hostA,
 
**ssh hostAuser@buddysip**
**ssh hostBuser@localhost**
 
?

---

### Post by mbeach on 2008-06-03
Well, you wouldn't really need the port forwarding to another ssh I wouldn't think.

ssh hostAusr@buddysip

login, then at the prompt, 
ssh hostBuser@hostBlanIP
or 
ssh hostBuser@hostBmachineName  (if things are working correctly)

---

### Post by ShinHadoken on 2008-06-03
Ok, cool! That makes it easy. I can just forward my router's port 22 to my server's port 22, and I can access my other pc's from there.

---

### Post by jpkotta on 2008-06-05
You can also use ProxyCommand and netcat to make it automatic.

I can't ssh directly to my work machine (shannon), but I can ssh to one of the servers (waterson), from which I can ssh to shannon.  netcat is installed on waterson, and the following is in ~/.ssh/config on each machine I want to ssh from (goedel, my laptop).
```

[jpkotta@goedel][~][0]
$ cat /home/jpkotta/.ssh/config 
Host shannon
HostName shannon.example.com
ProxyCommand ssh -q waterson.example.com "nc -q 1 %h %p"

```

Then to ssh sort of directly to my work machine, I just 
```
[jpkotta@goedel][~][0]
$ ssh shannon

```

The nice thing is that even though I have to give a password for both waterson and shannon, netcat makes the connection sufficiently transparent that most applications work as though I sshed directly into shannon.  I think you can basically do the same thing with ssh forwarding, but this was more robust for some reason I can't remember.

---

