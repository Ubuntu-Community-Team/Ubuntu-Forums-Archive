---
title: "FreeNX in Feisty"
date: 2007-04-17
forum: General Help
---

### Post by jon21 on 2007-04-17
Any word on running FreeNX in Feisty?

---

### Post by chomafin on 2007-04-20
> **jon21 said:**
> Any word on running FreeNX in Feisty?

The Dapper packages for FreeNX work.  I just went through [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) and got it up and running. For this version, if connecting from windows, you will need to download the older version of the client. For me, I am using the windows client 1.5.0-138, and it works like a champ.

---

### Post by inverder on 2007-04-23
I followed that same guide, but I am getting some problems:

First of all, I am able to use putty to login and work fine so I think I did almost everything right. Second, I am using the 2.x client (I don't know where to find the older version). But yeah, this is the error I get:

```

NX> 203 NXSSH running with pid: 1908
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 140.228.109.93 on port: 8888
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: derek
NX> 102 Password: 
NX> 103 Welcome to: MARK-II user: derek
NX> 105 listsession --user="derek" --status="suspended,running" --geometry="1600x1200x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'derek' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: derek
NX> 105 startsession  --link="lan" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="1" --mediahelper="esd" --session="MARK-II" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/en_US" --screeninfo="1600x1170x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: MARK-II-1000-2B29D6DC2FA775F12A0B84236430BE2D
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: f2f66c4e67cdeb54dd3519e89f54c2e4
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 769f2b8a75180c1e8c9b37ccbcf9e049
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
NX> 105 /usr/lib/nx/nxserver: line 891: 12432 Terminated              ( sleep $AGENT_STARTUP_TIMEOUT; exit 1 )
Killed by signal 15.

```

close, but no cigar?

oh and I am running ubuntu 7.04

any suggestions?

---

### Post by malaprohibita on 2007-04-24
I'm going to hazard a guess that you need to downgrade your NX client to the 1.5xxx referenced above.  The newer 2.x client is incompatible with the NX server that Ubuntu uses.  You may have to google for the executable, though, as I think it's no longer available on the NoMachine site.

Hope that helps.

---

### Post by matcram on 2007-04-25
you can download the 1.5 client from a french website. Click this link and start enjoying freenx ;-)

[http://ftp.dedibox.fr/pub/dedibox/utils/nxclient-1.5.0-138.exe](http://ftp.dedibox.fr/pub/dedibox/utils/nxclient-1.5.0-138.exe)

---

### Post by forgeuk on 2007-04-26
Just a quick question on this thread...

I've been using the trial commercial NXserver, and now of course they want $700 from me to buy a licence, when its only worth about $7, so I've switched to FreeNX server, and noticed that the NXclient 2.0 almost works, but not quite, so taken the advice above and got the 1.5 version of the client. Seems to work fine, but it won't resume a suspended session, always starts a new one, I don't get the "select a session" window pop up, it just creates session 1001.

Is this just one of the "features" of the free server, or is there a setting I can tweak here, I even tried:

"MyIPxxx:1000" in the login name, but it ignores the 1000 and just creates a 1001.

Is there a FreeNX client I should be using instead of NoMachines ?

Thanks in advance.

p.s. I'm going from Windows -> Ubuntu

---

### Post by eyelessfade on 2007-04-26
I haven't got the server working in feisty. (tried 4 computers) The client just give up and dies when it starts up a new X session. Up until that it works for me. So close but no cigar. :(

---

### Post by forgeuk on 2007-04-26
I'm on Feisty, seems fine. I went through the step-by-step guide on the FreeNX Wiki if thats of any help to you. Also make sure "Use SSL" option is switched on, that stopped mine originally from doing the final step in the connection.

---

### Post by Divan Santana on 2007-04-26
Mine works on Feisty just for everyones interest!

I install it from dapper packages.
Did a nxserver --adduser test
nxserver --passwd test123
nxserver --restart

When connecting with nx client tick enable ssl encryption.

Worked for me.

---

### Post by mrmonaro on 2007-04-26
Worked like a charm from the deb's on the official website, then all i had to do was enable ssh on port 22. 
/etc/ssh/config or something like that and just uncomment a line and i was away, tried it on both a linux (suse...god its bad) and a windows machine.
Little note, if you're using Xubuntu, use custom desktop and type "startXfce4"

---

