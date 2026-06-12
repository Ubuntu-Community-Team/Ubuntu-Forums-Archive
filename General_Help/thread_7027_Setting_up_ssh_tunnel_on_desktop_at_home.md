---
title: "Setting up ssh tunnel on desktop at home"
date: 2004-12-03
forum: General Help
---

### Post by 2fargon on 2004-12-03
I would be grateful if someone could help me do the following, considering I am a newbie...

I have a ubuntu box at home. I use my laptop at school. I cannot access any IRC chat channel from school, since the ports are blocked.

I would like to set up the box at home to act as a tunnel or proxy, so that I can access IRC channel through that box, even when I am at school. The box at home is connected to the internet through a dhcp connection, and it is always on.

I would love for someone to tell me step by step the thing that I need to do to get things setup so that I can do what I want, as described above. At the end of the thread, if and when (I am sure I will) I find a solution that works, I promise to write a HOWTO :)

Thank you.

---

### Post by M@t on 2004-12-04
I don't well irc, but I know you can access it in command line. 

So, in first, you have to install an ssh server:
```
sudo apt-get install openssh-server
```
when you are at school, login to your ubuntu box, you have to know your ip:
```
ssh user@host
```
Type your user password, and you are in your ubuntu box. Now you could do what you want in your pc, and if that is correclty set-up, access irc.

---

### Post by 2fargon on 2004-12-04
Thanks for the lead! Now I have to figure a way to use xchat from my machine, using this tunnel. I recall reading something like it once, just cant seem to find the document on the 'net now. Any help will be appreciated :)

---

### Post by jdong on 2004-12-04
**ssh user@host -L:local_port_to_listen_on:remote_host_to_forward_to:remote_port**

---

### Post by 2fargon on 2004-12-04
[QUOTE=jdong]**ssh user@host -L:local_port_to_listen_on:remote_host_to_forward_to:remote_port**[/QUOTE]

What would the ports be, any guesses?

I think the default port for the IRC client is 6667, so do I do

ssh myself@myhomebox -L:8080:6667:22 ?

It would be great if I could get some default numbers, for the ports.

---

### Post by 2fargon on 2004-12-05
I consistently get a "connection refused" when I try to ssh to my server, even after openssh-server is installed. What is the best i can do to start finding out where the problem is?

---

### Post by 2fargon on 2004-12-05
I can connect and chat using a tunnel through my webhosting shell account, but I still cannot seem to do it using my own computer at home, where I get a connection timed out or refused each time I try to connect to it thru ssh.

To connect using my server, I do the following :

In my linux box at school, I fire up a terminal window and execute the following command:
```

 ssh -l jeremy -L 6667:irc.freenode.net:6667 example.net
```

where  jeremy is my username that I use to login to my hosting account server, and example.net is my domain name/URI used to connect to the server through ssh. I want to connect to the freenode chat network/room.

It then asks me a question, to which I reply YES. 

Then it asks me for the password, I give it the password for jeremy.

Now I am logged into to SSH and port forwarding is active.

Now I fire up XCHAT on my school computer, which I use to chat on IRC.

It tries to connect, but cannot since there is a firewall at school. So in xchat's dialog bar(where you normally  type things during chat) I type 
```

/server localhost
```
and press enter

Now I can connect and join #ubuntu :)


I would be REALLY grateful if someone could tell me why I get timed out/refused at my homebox. I have sshd running there, and I have tried directly typing the IP address, and I also setup a name at dyndns.org, to no avail.

Thank you.

---

