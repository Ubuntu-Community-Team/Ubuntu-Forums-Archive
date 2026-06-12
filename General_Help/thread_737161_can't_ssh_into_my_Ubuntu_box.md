---
title: "can't ssh into my Ubuntu box"
date: 2008-03-27
forum: General Help
---

### Post by guitarMan666 on 2008-03-27
I am running Ubuntu Gutsy Gibbon with an SSH server on it so that I can log in to my home PC from school through the internet.

To do this, I am running Damn Small Linux in a QEMU window so that I am compliant with the rules of my college's network (not allowed to boot the computer from your own device).  Every morning I run the SSH start command in the terminal window (today i left said window open to see if it made a difference) and everything seems to be ok (it even says the little [OK] message).  When I get to school, I fire up QEMU, which can browse the internet from any school computer that I've tried so connectivity is not an issue, open up an Xshell.

Unfortunately, pinging my server times out, as does my SSH connection.  It doesn't seem to matter which address I use, I've tried both my numeric IP address and my address on dyndns.org  Am I missing something that is required to SSH over the internet?

I haven't tried SSH over the LAN from the other computer in the house.  There is no hardware-based firewall and the router *should* forward all ports to my machine (which at least for now is un-firewalled).

If anyone has any ideas they would be greatly appreciated.

---

### Post by justleen on 2008-03-27
routing seems the obvious answer..

are you trying as root by any chance?
can you ssh to localhost, when logged on to your system (as good as trying from local LAN) ?
is sshd actually running? (ps -ef|grep sshd)
 do you see any entries in your  /var/log/auth.log  or messages.log?

can you ssh from a different location? the mere fact that you can browse the internet doenst mean port 22 is open as well...
If you dont have a webserver running on your box, try setting op sshd.conf to listen to port 80 (and make sure your client in QEMU uses port 80 as well)
even better, let your host listen on the HTTPS port, since all traffic on that port is encrypted anyway.. that way your schools sysadmins dont see encrypted traffic on port 80

---

### Post by guitarMan666 on 2008-03-27
Thanks I'll try those as soon as I get back home.

---

### Post by guitarMan666 on 2008-03-27
Yes, sshd is running.
Yes, I can ssh in using the home IP (127.0.0.1)

The auth.log file is full of cron sessions for user "root" that open and close a few times a second if i'm reading the timestamp correctly.  It also contians a record of my USB key-drive being added and removed as well as my ssh attempt from the home ip.

The messages.log file (assuming its in the same folder as auth.log) is blank.

I'm not entirely sure what you mean "trying as root" though.  I have to use sudo to start sshd and trying as root in DSL doesn't change anything.
I'll take those config changes into consideration i want to see if i can make this work first...unless you think that would help.

---

### Post by guitarMan666 on 2008-03-31
I've changed the port the ssh server listens on to the HTTPS port, but when I run the command to log in using the home IP, I get an error.  Below is a copy of the command I'm using and the error.

eric@linus:~$ ssh eric@127.0.0.1:443
ssh: 127.0.0.1:443: Name or service not known

Any ideas where I went wrong?

---

### Post by Nameless_one on 2008-03-31
try 
```
$ ssh eric@127.0.0.1 -p 443
```

the ssh man page specifies a -p switch for remote port.

---

### Post by guitarMan666 on 2008-03-31
Oh lol ok that should have been the first thing I checked.  Heh, now I feel a little dumb for not doing that to begin with.
Thanks.

---

### Post by guitarMan666 on 2008-03-31
I'm at school right now and this newfound information isn't doing any good as far as truly remote logins are going (from DSL in QEMU), even running in a shell with root access.

---

### Post by guitarMan666 on 2008-04-03
Ok, I have figured out the issue here.  The IP address I see when I get my internet IP address is actually the IP address of my router.  I've seen several websites that say I need to set the router to forward the desired port(s) but no clear answers on how to do it.

I have Verizon DSL with a Westell 327w router.  Does anyone have any ideas on how to forward a port on this kind of router (or at least where the config setting for doing so is)?

---

### Post by mangoes on 2008-04-05
Looks like port forward howto for your westell router is included [here]("http://portforward.com/english/routers/port_forwarding/routerindex.htm")

Also, have you changed the listening port in
/etc/ssh/sshd_config
and restart ssh

hope that helps

EDIT: 
-oops from your previous post it seems you already change the listening port in sshd_config. mybad.
-need to make your server's LAN ip address static and outside dhcp range before port forward.

---

### Post by KeyserSoze93 on 2008-04-06
yes, you need to use port forwarding if you have a router. also, make sure you have configured your firewall (if you have on). if/when you do get it working, you might also want to try PuTTY on the windows machine (windows SSH client) since it will probably be quick to start and run... Also winSCP for copying files from/to the ubuntu box...

---

