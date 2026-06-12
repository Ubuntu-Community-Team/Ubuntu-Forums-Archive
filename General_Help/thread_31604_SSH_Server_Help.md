---
title: "SSH Server Help"
date: 2005-05-03
forum: General Help
---

### Post by dmccarney on 2005-05-03
Hello, I'm brand new to Linux and Ubuntu in general. Recently I've been trying to set up an SSH server on my new ubuntu box. I've so far managed to get the ssh packages, set up a dyndns account, install a python script for updating dyndns and set up a crontab to run the python script every 40 min or so. I'm behind a 4 port Linksys BEFSR41 router and I /think/ I have the port-forwarding set up correctly for port 22 (SSH as far as I know), I have followed the router instructions and other websites. I have the ports forwarded to 192.168.1.3 (the ip I've set up, hopefully successfully, to be my static ip.) I'm quite sure if my ssh server is running right now (remember I'm brand new to linux) but I can't seem to ssh to my dyndns url even though it is pointing to my correct external ip (i checked with ping and on the dyndns site). I'm not sure if my problem lies in: A) The static ip, B) Dyndns (the most doubtfull errors of all since it points to the correct ip), C) The SSH server, or D) My port forwarding/router setup in general. If anyone can help me at all with this or has any experiance it would be greatly apprectiated. Remember not to take any knowledge for granted, I'm new to this :P 

Below is an exerpt from my ifconfig output for eth0
" inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0" That should mean I have the internal static ip set correctly?

Thanks in advance.

(Added: I have even tried adding myself to the DMZ (De-militarized Zone) in an attempt to see if that would pass the SSH traffic but it didn't work either, besides I'd much prefer to be able to just use port forwarding)

---

### Post by mlmurray on 2005-05-03
Sorry,  I just typed a bunch of stuff, that, if I'd actually read your post, I'd have noticed you'd done already.

Can you connect to yourself?  As in "ssh localhost"?  if it lets you connect to localhost, then your server is running.  I would suspect your router not forwarding the port, but it sounds like you've configured it right.

You're not running iptables (firewall) on your machine are you?  If you notice if "Guarddog or Firestarter" are installed, they may be blocking the port.

---

### Post by mlmurray on 2005-05-03
[QUOTE=mlmurray]Sorry,  I just typed a bunch of stuff, that, if I'd actually read your post, I'd have noticed you'd done already.

Can you connect to yourself?  As in "ssh localhost"?  if it lets you connect to localhost, then your server is running.  I would suspect your router not forwarding the port, but it sounds like you've configured it right.

You're not running iptables (firewall) on your machine are you?  If you notice if "Guarddog or Firestarter" are installed, they may be blocking the port.[/QUOTE]
 Have you tried just ssh'ing to the actuall IP address of the router (the public IP, i mean)?

Also, when I had DSL, I couldn't connect to my public (external) IP from behind the router (I can now, on Cable), so I had to first ssh to some other remote computer (not on my own network), then ssh back to myself from there (or http, ftp, depending on what service I was testing).  This may be your problem.

Or, you may have someone external to you try it (just to see if the get a logon prompt).

---

### Post by dmccarney on 2005-05-04
Ok, thanks for the suggestions. I have a few things to try now. I had installed Firestarter when I first got Ubuntu but never actually configured it and it shouldn't be running, but I uninstalled it anyway. I'll check for iptables later when I get home. As for sshing to localhost, that works. I can log in no problem. As for trying to ssh to daniel@(my external ip) that doesn't work. So I /believe/ that the problem lies in either iptables/firestarter blocking the port or my router not forwarding the port correctly. I'll try some more stuff when I get home from work tonight. Thanks for all the help! I was quite proud I've even managed to get this far, having never used linux or anything like it before.

(Added, I tried to ssh to my external ip from here (my work) but I think my dyndns account has the incorrect ip atm, so I can even ping it. I'll have to try the external ip later. I do have adsl so that might be the problem too)

---

### Post by mlmurray on 2005-05-04
It sounds like your server is running.  And, if you uninstalled firestarter, you're probably not blocking your server's ports.  I would bet that you are forwarding your ports properly at the router (Linksys hardware is pretty easily set up), but that you're just not able to test it at home, since (at least in my experience) ADSL doesn't let you connect to yourself externally.

When you get Dyndns working right, you can go here:  [http://www.dslreports.com/scan](http://www.dslreports.com/scan) and scan for open ports (from home).  Hopefully, it will find port 22 open.

On the Dyndns issue.  I'm not familiar with the model Linksys you have, but most recent ones I've seen have a feature which will update dyndns (and some other dynamic ip services) automatically.  If not (or if, as in my case, you want a little more redundancy) you can still run your python script if you've tested it and it works or you can install (apt-get install) "ddclient".  It runs as a service and will update dyndns on an ip change.  Ddclient isn't all that well documented, though, but it works great.  If you want to use it I can send you my ddclient.conf file for reference.

Good luck! :)

---

### Post by segrewb on 2005-05-04
I would remove the router to remove it from the equation.  Of course you will need to update your ip address, etc.  I think your on the right path, just keep eliminating all the variables.

Segrewb

---

### Post by dmccarney on 2005-05-04
Ok, I think everything should be A-OK now :).
I double checked my python ipupdate script. Its all good, should run via crontab every 30 minutes and output all errors to a log file in my home dir. Next I installed ddclient and set it up (should be set up correctly, we'll see). Hopefully this redundancy will keep my dyndns account updated. I also did the port scan on that website and lo and behold:

TCP 22 : OPEN	The port is open.

Yaaaaay. My port forwarding is working I assume because it shows port 22 accepting TCP traffic (that should allow ssh correct?). I guess half the problem was trying to SSH into my external ip on dsl. I'll try to ssh in tomorrow with putty from work. 

Thanks for all of your help. Hopefully I won't be back here with more problems ;)

---

