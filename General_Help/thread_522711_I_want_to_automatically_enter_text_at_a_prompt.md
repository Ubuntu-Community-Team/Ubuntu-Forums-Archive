---
title: "I want to automatically enter text at a prompt"
date: 2007-08-10
forum: General Help
---

### Post by bns on 2007-08-10
I've created a script.  One of the commands it calls asks for a password.  I'd like to automate it so that it runs at boot, and I want the text entered at the prompt without me touching it.  How do I do that?

---

### Post by bodhi.zazen on 2007-08-10
enter the commands in /etc/rc.local

/etc/rc.local is run as root at boot

---

### Post by bns on 2007-08-10
Thanks for the reply.

I have already done so.  My script runs automatically like I want it to.  But my script calls another command which asks for a password, and I don't want to have to enter it.  I tried putting ```
command && password
``` but it doesn't enter it at the prompt, it waits until the command has failed and quit and then tries to execute password.

---

### Post by bodhi.zazen on 2007-08-10
can you not put that second command or set of commands into /etc/rc.local ?

If not, you could set the SUID on your script/command

Or you can run the command with yes :

yes <password> | command

do these other things with caution (I am not sure if the yes <password> will work or not)

---

### Post by bns on 2007-08-11
> **bodhi.zazen said:**
> can you not put that second command or set of commands into /etc/rc.local ?

no, because it's conditional.
> 
If not, you could set the SUID on your script/command

Or you can run the command with yes :

yes <password> | command

do these other things with caution (I am not sure if the yes <password> will work or not)
'yes' may work, but I don't know.

---

### Post by bns on 2007-08-11
I probably should have posted my script to begin with.  Here it is.

```
#!/bin/bash
if iwlist eth0 scanning | grep -q 'ESSID1'
then iwconfig eth0 essid ESSID1 key WEP-KEY && dhclient eth0
elif iwlist eth0 scanning | grep -q 'ESSID2'
then iwconfig eth0 essid ESSID2 && iu-vpn-ipsec start
fi

```
the script 'iu-vpn-ipsec' which I did not write, asks for a password.  I'm trying to enter that password automatically, but only if it actually runs.

EDIT: Before anyone asks, I wrote the script because my wireless card doesn't play nice with any of the clever programs out there.  The only way I can make it work is with shell commands.  It's a bcm4311, and I use ndiswrapper.

---

### Post by bettlebrox on 2007-08-11
Have you tried using the bcm43xx module instead of ndiswrapper? It's may support your card if you have a 2.6.20-6 or later kernel:

[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

I've a  BCM4309 Wireless card, and I used to use ndiswrapper which stopped working when I upgraded to Feisty. To my surprise it works perfectly with the BCM4309 driver.

Luck

---

### Post by bns on 2007-08-11
I've tried it.  It does work, but the wireless programs (network-manager or wicd, and one other that I can't remember the name of) still don't work with my card, and the signal is stronger with ndiswrapper.  I'll try again with gutsy, but until then, my script works.  I just need to get the password thing figured out.

---

### Post by bns on 2007-08-11
I tried running ```
yes "PASSWORD" | iu-vpn-ipsec start
``` When I did, on the line where the password prompt was it said ```
stty: standard input: Invalid argument 
```Any ideas?  BTW, my password contains both spaces and a semicolon---there's no problem when I enter it manually though.

---

### Post by kerry_s on 2007-08-11
have you tried using sudo?

sudo visudo

%iu-vpn-ipsec ALL=(root) NOPASSWD: /usr/bin/iu-vpn-ipsec

sudo addgroup iu-vpn-ipsec
gksudo gedit /etc/group

then add your user to the iu-vpn-ipsec group
then you should be able to just use sudo iu-vpn-ipsec

taking another look, you might also need to modify the iu-vpn-ipsec script to not ask for a password internally, just go in there and remove the line that asks for a password.

---

### Post by bns on 2007-08-11
That's not the problem.  It runs as root, I just can't get the password to enter automatically.

---

### Post by kerry_s on 2007-08-11
> **bns said:**
> That's not the problem.  It runs as root, I just can't get the password to enter automatically.

if it runs as root, you shouldn't need a password. you just need to take out the part of the script that is asking for the password.

---

### Post by bns on 2007-08-11
> **kerry_s said:**
> if it runs as root, you shouldn't need a password. you just need to take out the part of the script that is asking for the password.
It doesn't ask for my system password, it asks for a network password to establish a vpn (virtual private network).  Sorry about the confusion, I guess I wasn't clear.

---

### Post by strider1551 on 2007-08-11
For what it's worth, if you know Python, [pexpect]("http://pexpect.sourceforge.net/") could do what you want.

> Pexpect is a pure Python module for spawning child applications; controlling them; and responding to expected patterns in their output. Pexpect works like Don Libes' Expect. Pexpect allows your script to spawn a child application and control it as if a human were typing commands.

---

### Post by bns on 2007-08-11
I got it to work using 'expect.'  Thanks guys.

---

