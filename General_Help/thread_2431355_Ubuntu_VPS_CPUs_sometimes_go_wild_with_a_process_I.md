---
title: "Ubuntu VPS CPUs sometimes go wild with a process I don't recognize"
date: 2019-11-15
forum: General Help
---

### Post by amosss on 2019-11-15
My VPS sometimes goes wild because of:

  /tmp/.X17-unix/.rsync/c/lib/64/tsm --library-path
/tmp/.X17-unix/.rsync/c/lib/64/ /tmp/.X17-unix/.rsync/c/tsm64 -t 302 -f 1 -s 8 -S 8 -p 0 -d 1
  After killing the PID and restarting the VPS, I saw 3 PIDs that kill my CPU with just ./cron in the command. After killing the ./cron PID, it is quiet but I guess it will return at some point.

  I tried cd-ing into .X17-unix to see what's  in there but it says the folder does not exist. Running ls -ld .?* also does not show .X17-unix though it does show .X11-unix. 
Any idea what it is and  what does it do? And more important, how can I make sure it doesn't  kill my VPS?

     Thanks

---

### Post by TheFu on 2019-11-15
Very suspicious.  I'd begin thinking the VPS has been hacked.  
Compare your backups from before this began with the current system files.  

Why I suspect hacking?
* using /tmp/
* using multiple directories beginning with . - which doesn't show in normal listings.
* using X17 ... which looks a lot like X11
* VPS
* google: [https://askubuntu.com/questions/1115770/crond64-tsm-virus-in-ubuntu](https://askubuntu.com/questions/1115770/crond64-tsm-virus-in-ubuntu)

What is the system supposed to be doing?

If it were me, I'd destroy the VPS, get a new one, and this time keep it patched, follow all best practices you can find, and figure out how they got in last time.  For example, do you allow ssh with passwords from anywhere in the world?  Stop that.  Passwords shouldn't be used.

---

### Post by amosss on 2019-11-15
Thanks for replying,

What is  .X11-unix folder?

After killing the PIDs, it calmed down. I expect a  malware to wake up immediately, no?

While the CPUs went crazy, the  network didn't so it looks like it just tried to exhaust the VPS.

I only installed tomcat/java and htop, that is basically it.

I read the link before posting, it has the same symptoms but different behavior and I'm not that familiar with linux, so I didn't know how to replicate the steps to my need.
How can I delete ALL folders under tmp? Is it a good thing to do?
What about deny port 22 outgoing in firewall? Will my ssh still work?
What about running an antivirus? clamav or something else?

---

### Post by TheFu on 2019-11-15
Dude.  If you are new, you need to wipe the machine, start over, and don't open any ports to the entire internet.

Tomcat/java was enough, but obviously, other stuff was installed since you can ssh in.  That means ssh was installed. The default ssh install isn't too secure. It uses passwords, which really shouldn't be allowed over the internet.

On a server, there shouldn't be any X11 anything. On a desktop, it is used for the GUI.

Flush this machine. It can't be trusted.  Once any machine is hacked, it cannot be trusted.  Period. Kill it off.
Start with a fresh, new, vps.
Begin by setting up a firewall that doesn't allow access by anyone in the world except the 2 machines you use.

How to secure ssh is well-travelled.  I've written about it many times.

Forget about AV on Linux. It scans for Windows viruses.  None will clean.

Wipe the system.  Do better next time.  Start over.

---

### Post by amosss on 2019-11-15
Where can I read about this?
Begin by setting up a firewall that doesn't allow access by anyone in the world except the 2 machines you use.

---

### Post by TheFu on 2019-11-15
> **amosss said:**
> Where can I read about this?
Begin by setting up a firewall that doesn't allow access by anyone in the world except the 2 machines you use.

I would use google - "ubuntu firewall" - and look for results with "ubuntu" in the URL domain.  You'll need a basic understanding of IPv4 and IPv6 networking too.  My skills with IPv6 are poor, so I disable it on all my systems and block it at the WAN router both directions.  I've read enough about IPv6 to know it can tunnel through IPv4 networks unseen.

People spend years learning about firewalls.  Unfortunately, Ubuntu networking has been changing every few releases, so dealing with network configurations is highly release specific.  As the networking changes, I would expect the firewall interfaces to change too.

If you want to learn Linux, my best advice is here: 
[https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux)

If you want to know a little bit more about security, a mind-set change is needed first:
[https://blog.jdpfu.com/2016/10/04/lamp-server-security](https://blog.jdpfu.com/2016/10/04/lamp-server-security) where you assume every connection is evil first and only allow known-good source IPs access.

My articles don't show many commands.  Commands are fairly easy and change from time to time.  I try to explain the "why", which doesn't change.  Provide the least access necessary to accomplish the task and no more.  That idea was valid in 1990 and it is just as valid today.

---

