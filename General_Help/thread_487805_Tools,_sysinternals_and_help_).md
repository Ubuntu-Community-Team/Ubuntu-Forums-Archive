---
title: "Tools, sysinternals and help :)"
date: 2007-06-29
forum: General Help
---

### Post by cytg on 2007-06-29
On my second week of ubuntu on the desktop, and like it very much so far.
However i have aquired som tools and insight on the windows platform that i miss alot here and i realize its the it comes with the noobish terretory..
So i was thinking if i write the corresponding tools in windows, someone could point me in the right direction for linux ?

Sysinternals
Processexplorer, nested processes parent/children, with resource overview and alot more
TCPMonitor, lists all connections and the process that owns them
Filemon, lists all disc access realtime, sort and io bytes

Windows taskmanager, this one has ALOT of optional columns, threads, handles, total io bytes in/out, io bytes/sec, cpu prio, mem usage, peak mem usage, virtal mem usage on a per process level and alot more

Olly debug, an excellent debugger for peeking into the inner workings of apps

Firewall .. this might sound stupid, but i like having a firewall ask me if this and that application may in fact connect to anything anywhere .. i figure and i can script my way out of it, so im really asking for the "usability" side of this aspect (other subjects too i suppose)

For anyone taking the time to read this, and maybe even reply ... Thanks! :)

---

### Post by cytg on 2007-06-29
a bump for me ;)

looking at strace for example, looks useful however needs to run the proccess to be monitored, no attaching or system wide monitoring ..

---

### Post by myoungf1 on 2007-06-29
> **cytg said:**
> On my second week of ubuntu on the desktop, and like it very much so far.
However i have aquired som tools and insight on the windows platform that i miss alot here and i realize its the it comes with the noobish terretory..
So i was thinking if i write the corresponding tools in windows, someone could point me in the right direction for linux ?

Sysinternals
Processexplorer, nested processes parent/children, with resource overview and alot more
TCPMonitor, lists all connections and the process that owns them
Filemon, lists all disc access realtime, sort and io bytes

Windows taskmanager, this one has ALOT of optional columns, threads, handles, total io bytes in/out, io bytes/sec, cpu prio, mem usage, peak mem usage, virtal mem usage on a per process level and alot more

Olly debug, an excellent debugger for peeking into the inner workings of apps

Firewall .. this might sound stupid, but i like having a firewall ask me if this and that application may in fact connect to anything anywhere .. i figure and i can script my way out of it, so im really asking for the "usability" side of this aspect (other subjects too i suppose)

For anyone taking the time to read this, and maybe even reply ... Thanks! :)


Okay here is a few, but not all, apps that you can use to do what you did in Windows

Ksysguard is a great process monitoring tool.
Firestarter is a nice firewall program for Linux.
tcptrack should do the tcp monitoring you are looking for.
for filemon check synaptic or adept to see if you can find an application to do this in linux.

Hope this helps

---

### Post by olejorgen on 2007-06-29
strace can be attached to an allready running process: (use ps -e | grep <process name> to get the pid)
```

sudo strace -p <pid>

```

---

### Post by cytg on 2007-06-30
Nice, thanks!

---

### Post by olejorgen on 2007-06-30
lsof
man proc
gdb
ltrace
ps
might also be of interest

ddd is a gui front end for gdb (quite ugly)

---

### Post by cytg on 2007-07-01
Thanks alot guys .. got some real good material here :)

---

