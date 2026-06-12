---
title: "I can only connect via SSH from one machine......why?"
date: 2014-09-02
forum: General Help
---

### Post by Maheriano on 2014-09-02
I've got an Ubuntu server and an employee's laptop whom was in charge of the server before leaving the company. I'm now in charge of the server and am using my own laptop instead of the old one he was using. I can easily access the production server via SSH from his laptop (his IP) but cannot access it from any other machine. I have the root password which, like I said, works fine from his machine but I can't get it to work from mine.

I thought there might be something in the hosts.allow or hosts.deny files but they're both just the default configuration, there's nothing custom in there. So then I thought it might be SSH key authentication but when I connect from his machine it still asks me for a password so it can't be that. Can it?

What should I check next?

Other information:
- his machine = Windows 7
- my machine = Ubuntu 14.04
- server = Ubuntu 10.04

---

### Post by Lars Noodén on 2014-09-02
What about /etc/ssh/sshd_config on the server?  There might be something there restricting which ip number you can log in from or something like that.

---

### Post by TheFu on 2014-09-02
Are you using his account or yours on the client AND/OR on the server.

Why is there a root password at all?  That's not how Ubuntu does it. Also - security best practices say to not allow remote root connections from ANYWHERE.

---

### Post by Maheriano on 2014-09-02
> **Lars Noodén said:**
> What about /etc/ssh/sshd_config on the server?  There might be something there restricting which ip number you can log in from or something like that.
There are a lot of things in there, what could be some things to look for? I'll check Google for what I should be looking for as well.
> **TheFu said:**
> Are you using his account or yours on the client AND/OR on the server.

Why is there a root password at all?  That's not how Ubuntu does it. Also - security best practices say to not allow remote root connections from ANYWHERE.
My mistake, I actually DO NOT have root access to production, the only username / password I have is for a user named 'web'. Also, 'allowrootaccess' is set to 'no' in the sshd_config file for this machine.
I'm using my own login on his machine, then using the login for the web user to SSH into production. I actually have an account on his Windows machine so I can log into it via Remmina.

---

### Post by Lars Noodén on 2014-09-02
> **Maheriano said:**
> There are a lot of things in there, what could be some things to look for? I'll check Google for what I should be looking for as well.

That would be a [Match Address](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) stanza in sshd_config if it's there.  I was also thinking of keys, which would not be in sshd_config.  On the server side of things, keys can be configured to restrict access to specific IPs or ranges of IPs.  

What is the exact method that you use to connect successfully?  What is the exact error message (and method) when it fails?  Presumably the same account is being used on the server each time.

---

### Post by Maheriano on 2014-09-02
> **Lars Noodén said:**
> That would be a [Match Address](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) stanza in sshd_config if it's there.  I was also thinking of keys, which would not be in sshd_config.  On the server side of things, keys can be configured to restrict access to specific IPs or ranges of IPs.  

What is the exact method that you use to connect successfully?  What is the exact error message (and method) when it fails?  Presumably the same account is being used on the server each time.

I don't see 'match' in the file anywhere (I performed a search).
The exact method I use to connect:
- RDP into Bob's Windows 7 laptop using my network login. The IT guy set me up with an account on his machine.
- Open PuTTy and SSH into the production server with user 'web' and the password.
- This gives me my console window to the production server.

When I try to SSH directly from my own laptop it just hangs for a long time and eventually times out. 

I looked in the sshd_config file and did fine these lines, could these do it? I'm typing them out manually since I can't seem to copy out of PuTTy:

```

HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes

StrictModes yes

RSAAuthentication yes
PubKeyAuthentication yes

IgnoreRhosts yes

```

Does this mean there's a key on his machine that I need to copy to my machine?

---

### Post by Lars Noodén on 2014-09-02
HostKey in sshd_config refers to the private keys identifying the SSH server itself.   

If you're connecting with a password from Bob's machine, you're probably not also using keys for authentication.  Though it would be good to implement them later after initial connections are figured out.

If you're not even getting a login prompt, then there might be some filtering going on.  Are you on the same subnet as the machine that works?  You can check to see what is filtered using [ufw](http://manpages.ubuntu.com/manpages/trusty/en/man8/ufw.8.html) on the server

```

sudo ufw status verbose

```

and look for port 22 or ssh.  It should say something like this:

```

22                         ALLOW IN    Anywhere

```

The only other thing that I can think of at the moment would be if PuTTy on Bob's vista7 machine is set to default SSH connections to a port other than 22.

---

### Post by Maheriano on 2014-09-02
> **Lars Noodén said:**
> HostKey in sshd_config refers to the private keys identifying the SSH server itself.   

If you're connecting with a password from Bob's machine, you're probably not also using keys for authentication.  Though it would be good to implement them later after initial connections are figured out.

If you're not even getting a login prompt, then there might be some filtering going on.  Are you on the same subnet as the machine that works?  You can check to see what is filtered using [ufw](http://manpages.ubuntu.com/manpages/trusty/en/man8/ufw.8.html) on the server

```

sudo ufw status verbose

```

and look for port 22 or ssh.  It should say something like this:

```

22                         ALLOW IN    Anywhere

```

The only other thing that I can think of at the moment would be if PuTTy on Bob's vista7 machine is set to default SSH connections to a port other than 22.

I don't have root access on production and my 'web' user is not in the sudoers file. Is this as far as we can go?
I do have to enter the password when connecting from Bob's machine, that's why I didn't think it was key authentication.
I set up the connection in PuTTy on his machine, I left the port to default 22. He didn't have a saved connection in PuTTy, I'm assuming he must have typed in the IP every time. Or he deleted it before he left.
When trying to connect from my machine I do not get a login prompt, it just hangs as soon as I hit enter.
I'm not too familiar with subnets but I know both of these machines are in another part of the country on a 192.168.3.X address. I'm on a 192.168.1.X address.

EDIT - I just talked to the network guy and he's telling me we can SSH between the 1.X networks and 3.X networks no problem but Bob had set up IP tables on the production server to restrict access. I guess I need to start there and I need root access in order to do so.

---

### Post by Lars Noodén on 2014-09-02
> **Maheriano said:**
> I'm not too familiar with subnets but I know both of these machines are in another part of the country on a 192.168.3.X address. I'm on a 192.168.1.X address.

It may be a networking problem.  That's not my area at all, but somehow you'll either have to get onto the same subnet (3.x) or else route from the 1.x net to the 3.x net, if it's not already done.  Can you ping the server even from your machine?

```

ping -c 5 -w 1 192.168.3.*x*

```

If not, you'll have to get some kind of help from the network administrator, if both networks are managed by the same company.  If one is home and the other is work, then that's a different can of worms.

---

### Post by Maheriano on 2014-09-02
> **Lars Noodén said:**
> It may be a networking problem.  That's not my area at all, but somehow you'll either have to get onto the same subnet (3.x) or else route from the 1.x net to the 3.x net, if it's not already done.  Can you ping the server even from your machine?

```

ping -c 5 -w 1 192.168.3.*x*

```

If not, you'll have to get some kind of help from the network administrator, if both networks are managed by the same company.  If one is home and the other is work, then that's a different can of worms.

See edit in previous post regarding network communication and IP tables.
Yes, I can ping it no problem.

---

### Post by Lars Noodén on 2014-09-02
> **Maheriano said:**
> 
EDIT - I just talked to the network guy and he's telling me we can SSH between the 1.X networks and 3.X networks no problem but Bob had set up IP tables on the production server to restrict access. I guess I need to start there and I need root access in order to do so.

That will do it.  Anyone with root access could adjust UFW for you.  But that looks like the next step.

---

### Post by Maheriano on 2014-09-02
Thank you very much! You've been a huge help.

---

### Post by TheFu on 2014-09-02
If you have physical access to the box, that root password can easily be changed using a liveCD - but I'd just add your account to the sudoers file and remove the root password. Of course, if different systems connect as root directly to do things - well, then migrating those other systems over to non-root would be important.

Get used to using sudo and please, please, document any changes you make for the next guy.  In the old days, we had a notebook for every server and put notes into it. Kept is locked up, for obvious reasons. It is a good habit for a new admin to learn.

---

### Post by Habitual on 2014-09-02
Or....you could assign his machine IP to your computer and try, but the correct answer is contact the network administrator.

---

