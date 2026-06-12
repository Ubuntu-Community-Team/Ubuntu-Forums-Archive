---
title: "HLDS not working"
date: 2008-02-19
forum: General Help
---

### Post by TotalRetard on 2008-02-19
Hello.

I've ran HLDS on Ubuntu 6.06 and 7.04 many times, I've installed it and reinstalled it multiple times now, but it refuses to work.

This is what happens:

> 
kk@Thinkpad:~$ cd HLDS; ./hlds_run -game cstrike +ip 192.168.0.66

Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash

Console initialized.
scandir failed:/home/kk/HLDS/./platform/SAVE
Protocol version 47
Exe version 1.1.2.5/Stdio (cstrike)
Exe build: 20:02:49 Oct 24 2006 (3651)
STEAM Auth Server
couldn't exec language.cfg
Server IP address 192.168.0.66:27015
couldn't exec listip.cfg
couldn't exec banned.cfg
exit

Adding master server 69.28.151.162:27010
Adding master server 72.165.61.190:27010
Tue Feb 19 19:24:10 EET 2008: Server Quit

kk@Thinkpad:~/HLDS$


I can't see the server in my LAN. I think it's because the "Adding master server" happens AFTER I type **exit**.

I can leave the server on for an hour, and it doesn't add the master servers until I type exit.

If I kick up another terminal and do a nestat, it doesn't show any activity on HLDS or the port 27015.
Having had many working HLDS's before, and solving alot of problems before, it sucks I can't find a solution for this.

Someone help me?  :confused:

Edit: I am running Gutsy on the server box.

---

