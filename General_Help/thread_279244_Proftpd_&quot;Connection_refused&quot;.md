---
title: "Proftpd: &quot;Connection refused&quot;"
date: 2006-10-17
forum: General Help
---

### Post by a_f on 2006-10-17
I am trying to set up my proftpd access, and have set up my system as per the non-beginner instructions [here]("http://ubuntuforums.org/showthread.php?t=79588"). 

 - Home webserver is on a static IP, cable. Linux Ubuntu v6.06 on old world PPC mac box.
 - Proftpd is set up using inetd, not standalone.
 - I am using a router with an external IP address, which port forwards port 1980 to my internal machine IP.
 - I have copied and pasted the proftpd.conf file as per the tutorial (setting up my user's ftp account with no issue apparent), as well as added "MasqueradeAddress 80.x.x.x (really my external ip) and PassivePorts 60000 65535" directions in the conf because I'm on a router. Refer to attached config file.

When I try to connect using my external IP, "Connection refused".

On the webserving machine, ftp'ing to 127.0.0.1 again brings "Connection refused". Same error using internal IP address. SSH'ing to all of these brings the same error.

 - I understand that I cannot "reload" an inetd setup because config files are  read with each session initiated.
 - I have rebooted the router.
 - I have ensured that my inetd.conf file has tcp and not tcp6 (re: Ipv6 IPs).

Any further advice, please? I'm on my 6th day of trying to get this to work :???: ](*,)

---

### Post by a_f on 2006-10-17
Oh, I should also add that I have looked at adding items to /etc/xinetd.conf file (i.e. "disable = no" to its options") BUT I do not appear to have this file on my machine.

---

### Post by mjziegle on 2006-10-17
Follow the beginner instructions and then go to advanced.  

Connection refused usually means your authentication method was denied, your port isn't accepting connection, your ssl is screwed up, you require ssh but don't have keys etc etc.

Start small then build up.

---

### Post by a_f on 2006-10-17
Done :)

After installing gproftpd as beginner section instructs, I have entered all applicable details.

However, upon checking the syntax of my .conf file, it says:

[I]If there are no complaints the configuration is ok...

 - IPv6 getaddrinfo 'localhost' error: Name or service not known

Check completed.[/I]

The server (now setup as a standalone it would seem) is online. I have my port forwarding set on the router for port 1980 to go to my internal IP machine.

Any further advice on this new message? :) 

(I can't even figure out where the localhost setting is set - what does this mean - I've looked through my config file (new) and it doesn't seem to appear anywhere so I can't begin to identify what the problem is, nevermind the solution...?)

---

### Post by a_f on 2006-10-17
Gah! Just as I posted that I tried one last time to connect, expecting the same old connection error - and it worked!

I still get the syntax error on checking with the GUI though - any ideas what the deal is? (Just because I'd like to find out what the implications of this error are ;))

---

### Post by mjziegle on 2006-10-18
Just ignore the IPv6 error since it doesn't apply.  In the absence of an IPv6 address the system will default back to IPv4 which is what the 99.9% of systems use now anyway.

For host names use the 'hostname' command to set your name
for dhcp you'll have to make sure your dns is setup properly and you also will have to set /etc/dhcp3/dhclient.conf.

---

