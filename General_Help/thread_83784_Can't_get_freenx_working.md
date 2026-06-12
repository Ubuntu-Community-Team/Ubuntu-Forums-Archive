---
title: "Can't get freenx working"
date: 2005-10-29
forum: General Help
---

### Post by ghoshe on 2005-10-29
I have installed freenx server on my brand new Kubuntu 5.10 server but I can't connect to it.

Here is my client connection info:

--------------------------------------------------------------------------

NX> 203 NXSSH running with pid: 2231
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.0.1 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: xxxx
NX> 102 Password: 
NX> 103 Welcome to: xxxx user: xxxx
NX> 105 listsession --user="xxxx" --status="suspended,running" --geometry="1280x1024x24+render" --type="unix-kde"
NX> 127 Sessions list of user 'xxxx' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: xxxx
NX> 105 startsession --session="xxxx" --type="unix-kde" --cache="8M" --images="32M" --cookie="******" --link="adsl" --kbtype="pc105/es" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="800x600+240+188" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="800x600x24+render" 

Killed by signal 15.

--------------------------------------------------------------------------

Somebody can help me?:confused:

---

### Post by andygodwin on 2005-10-30
Same here; I get precisely the same problem on an almost-fresh Kubuntu 5.10 install.

I used the packages off [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl), as most threads seem to suggest. Use standard NX client (I tried using the Linux client), connects, authenticates, sits there for a while and then you get the error mentioned above.

Help would be really useful, since VNC feels sluggish and is a bit of a bandwidth hog...

---

### Post by ghoshe on 2005-10-30
I found the problem... i have my own iptables rules, by default i drop all packets, nxagent needs to make a loopback proxy connection, so you only have to allow loopback connections adding a new rule like this one:

iptables -A INPUT -i lo -s 127.0.0.1 -j ACCEPT

It worked for me, i only had to be thinking (and studying) about it 3 days :rolleyes: 

TOOOMA moreno!

---

### Post by Beau on 2005-11-30
I get almost the same error except instead of the "Killed by signal 15" I get a connection timeout.
I haven't setup any iptables. 

Can anyone help me?

---

### Post by waster on 2006-04-03
Make sure the loopback interface is running. It is needed for ssh to be used to authenticate.

sudo ifconfig lo up

---

### Post by kford on 2006-06-07
Hey there all,

Just upgraded from Kubuntu 5.10 to Dapper and attempted to get Freenx working.  Lo and behold, when I uninstalled the firewall (Kmyfirewall) I was able to log into the machine no problem with the nx client (I could already ssh to the machine without difficulties).

I found this post and would like to be able to run the firewall as well as log into the machine with freenx but I cant figure out how I would add a loopback rule to Kmyfirewall.  Can anyone give me some pointers on how to accomplish this? 

Waster: I would imagine that my problem isnt related to "sudo ifconfig lo up" since I can ssh to the machine (and use freenx without the firewall on), correct?

Thanks in advance,

kford

---

### Post by treris on 2006-06-11
I was having some trouble logging into FreeNX too, but 
*sudo ifconfig lo up *

has somehow fixed it, so now I can happily log in from just about everywhere!!! 

BRILLIANT, thanks

Edit: actually it only worked for a little bit, now I get the same error message again, while I didn't change anything as far as I can tell, how weird is that?

---

