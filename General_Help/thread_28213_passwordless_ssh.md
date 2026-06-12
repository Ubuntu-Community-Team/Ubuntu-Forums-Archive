---
title: "passwordless ssh"
date: 2005-04-19
forum: General Help
---

### Post by fire59 on 2005-04-19
Trying to setup passwordless ssh on my ubuntu(local) machine so I can backup my ubuntu to my osx machine(remote).

I'm following the instruction on this site: [http://madpenguin.org/Article1505.html](http://madpenguin.org/Article1505.html)

Got everything setup and still not working(still asking me for password), read somewhere you had to do an ssh-add so I try to do that on my ubuntu and got this:
```

ssh-add
Could not open a connection to your authentication agent.

```

Has anyone set this up on their ubuntu install?

---

### Post by dataw0lf on 2005-04-19
[QUOTE=fire59]Trying to setup passwordless ssh on my ubuntu(local) machine so I can backup my ubuntu to my osx machine(remote).

I'm following the instruction on this site: [http://madpenguin.org/Article1505.html](http://madpenguin.org/Article1505.html)

Got everything setup and still not working(still asking me for password), read somewhere you had to do an ssh-add so I try to do that on my ubuntu and got this:
```

ssh-add
Could not open a connection to your authentication agent.

```

Has anyone set this up on their ubuntu install?[/QUOTE]

Your shell isn't running under ssh-agent.  Type :
```
exec ssh-agent bash
```

and then try running ssh-add

---

### Post by fire59 on 2005-04-19
Thanx that works.

---

### Post by fire59 on 2005-04-20
Got everything set up and added to cron by doing cron -e.  Didn't see the backup file .  Where are cron log stored?

---

### Post by i-tech on 2005-04-20
I dont know what you did but this public key way also works well
type ssh-keygen -t dsa in your local machine. It will require pass and stuff from you. After creating your key go to your .ssh folder and copy the contents of .id_dsa.pub Login to your server with ssh  go to your .ssh folder at remote host. and paste the contents to .ssh/authorized_keys. 
Enjoy 
:-P

---

### Post by fire59 on 2005-04-20
Got the password less part to work.  Just looking at why it didn't go off at 2am(cron job).  Looking at the /var/log/syslog and my system mail there's some permission error so i'll have to look at that.

---

### Post by kalle314 on 2005-08-10
I am borrowing this thread for a newbie problem with passwordless ssh. (edit: problem solved.)

What I need is passwordless ssh (and/or rsh) to the current host.
The current host happens to be me, localhost. 
Can this be done in a simple way?

This is what I have done:

1. Edited the following files:
~/.rhosts (added <my_hostname> <my_username>)
~/.shosts (added <my_hostname> <my_username>)
/etc/hosts.allow  (added ALL my_IP)
/etc/ssh/hosts.equiv (added <my_hostname> <my_username>)

2. Messing with keys:
ssh-keygen -t rsa
*Generating public/private rsa key pair.*
*Enter file in which to save the key (/home/my_username/.ssh/id_rsa):* (press enter)
*Enter passphrase (empty for no passphrase):* (press enter)
exec ssh-agent bash
ssh-add
*Identity added: /home/my_username/.ssh/id_rsa*

3. Checking that everything is correct:
/etc/ssh/ssh_config (contains "host *  #   Port 22")
/etc/services (contains "ssh  22/tcp")

Bit I do still get 
$ ssh localhost
ssh: connect to host localhost port 22: Connection refused
$ ssh my_hostname
ssh: connect to host my_hostname port 22: Connection refused

EDIT: PROBLEM SOLVED

What was missing was the ssh daemon in Open SSH, everything worked after this was installed.

---

### Post by KittyChunk on 2006-07-18
> **i-tech said:**
> I dont know what you did but this public key way also works well
type ssh-keygen -t dsa in your local machine. It will require pass and stuff from you. After creating your key go to your .ssh folder and copy the contents of .id_dsa.pub Login to your server with ssh  go to your .ssh folder at remote host. and paste the contents to .ssh/authorized_keys. 
Enjoy 
:-P

Thanks for this! I'm busy setting up a scientific compute cluster using ubuntu-server on the nodes, and one of the message passing interfaces we are using requires passwordless ssh (rsh, actually, but if ssh pretends to be rsh and doesn't need passwords that's good enough) access between each machine in the cluster.

I've got an interesting glitch. I have two machines, both running sshd and both happily able to connect to each other using rlogin and providing the password. Following the advice above, I generated a DSA key on machine 1 and copied it to authorized_keys on machine 2, and vice versa. 

Having done that, I am now able to rlogin to machine 2 from machine 1 passwordlessly, but *not* the other way around - rlogin to machine 1 from machine 2 still needs a password! Very strange ;). Any thoughts?

---

### Post by jam1492 on 2008-06-30
> **dataw0lf said:**
> Your shell isn't running under ssh-agent.  Type :
```
exec ssh-agent bash
```

and then try running ssh-add
I get the same error message in xubuntu (hardy) using

sudo ssh-add

However when I use

sudo exec ssh-agent bash

I get the message

sudo: exec: command not found.

However the command is found and works with out sudo.

How do I allow sudo to use this command (or simply to use ssh-add)?

---

### Post by apmcd47 on 2008-07-01
Stupid question, but: why? sudo is really only useful for doing a couple of things as root, or hanging on to your environment while you do an administrative task (eg sudo make install). I would think that the sudo environment is destroyed when the command you sudid(?) exits.

So, doing what you are trying to do, I would suggest "exec ssh-agent bash"; "ssh-add"; "sudo ssh" and see if that works. If not, try running sudo interactively, then doing the ssh-agent/ssh-add/ssh. But, again, why? If you are trying to run as root on another machine, do it directly from your user account on the local machine. But it is probably not suitable to do it passwordlessly, for obvious reasons. Or possibly "ssh <remote> sudo?"

If you want to do something from cron like the orginal poster seemed to do, I think you are on a no-no. First, ssh-agent has to be run at an early stage of boot-up, secondly someone has to be around to type in the passphrase whenever the machine boots up.

If you really really have to do an ssh over cron (for backups perhaps) contact me directly and I'll give you some suggestions.

---

