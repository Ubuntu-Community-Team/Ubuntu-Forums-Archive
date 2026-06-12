---
title: "Samba will not run"
date: 2019-01-02
forum: General Help
---

### Post by merlinus on 2019-01-02
I just did a fresh install of 18.04, all the upgrades, and installed samba.  I can set up shared folders, etc. via sudo -H system-config-samba.  But samba will not run.  

Ideas and suggestions?  Thanks!

---

### Post by david503 on 2019-01-02
What does it say when you try to run it?  (And how do you run it?)

---

### Post by merlinus on 2019-01-02
$ sudo /etc/init.d/smbd start
[sudo] password for merlin: 
[ ok ] Starting smbd (via systemctl): smbd.service.

But it does not show up as a process in system monitor, the shared folders are not available in various apps such as Logitech Music Server, and in System/Administration/Shared Folders an error message says that sharing services are not installed.

---

### Post by david503 on 2019-01-02
> **merlinus said:**
> $ sudo /etc/init.d/smbd start
[sudo] password for merlin: 
[ ok ] Starting smbd (via systemctl): smbd.service.

But it does not show up as a process in system monitor, the shared folders are not available in various apps such as Logitech Music Server, and in System/Administration/Shared Folders an error message says that sharing services are not installed.

What do you get from this:

sudo systemctl status smbd

---

### Post by merlinus on 2019-01-02
sudo systemctl status smbd 
[sudo] password for merlin: 
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: ena
   Active: active (running) since Wed 2019-01-02 12:13:51 MST; 52min ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
 Main PID: 24236 (smbd)
   Status: "smbd: ready to serve connections..."
    Tasks: 4 (limit: 4915)
   CGroup: /system.slice/smbd.service
           &#9500;&#9472;24236 /usr/sbin/smbd --foreground --no-process-group
           &#9500;&#9472;24263 /usr/sbin/smbd --foreground --no-process-group
           &#9500;&#9472;24264 /usr/sbin/smbd --foreground --no-process-group
           &#9492;&#9472;24268 /usr/sbin/smbd --foreground --no-process-group

Jan 02 12:13:50 athena systemd[1]: Starting Samba SMB Daemon...
Jan 02 12:13:51 athena systemd[1]:

---

### Post by david503 on 2019-01-02
Well we're making progress- the good news is that it is, in fact, running.

So have you tried connecting to it?

---

### Post by merlinus on 2019-01-02
I have set up a samba share at 192.168.1.2/storage/music, but it does not show up as a remote music library in Logitech Music Server.

What else might you suggest in terms of connecting to samba, in order to test it?  

And many thanks for your assistance!

---

### Post by david503 on 2019-01-02
> **merlinus said:**
> I have set up a samba share at 192.168.1.2/storage/music, but it does not show up as a remote music library in Logitech Music Server.

What else might you suggest in terms of connecting to samba, in order to test it?  

And many thanks for your assistance!

Sure.  

Ok I'm not familiar with logitech music server.  So there are two machines at work here right- one is, what, you're pc? laptop?  And the other is this console style single-purpose jobby from logitech that, like presumably connects to speakers or something right?  So you want the logitech to talk to samba on your PC?

I mean, see? Ya gotta throw me a bone here, man, what's the scenario; what's the setup? Ya gotta give me more information man.

---

### Post by merlinus on 2019-01-02
LMS resides on an RPi, which is hooked up to my sound system.  The shared folder is on my PC in another room.  I used to be able to stream music from the PC to the RPi using wireless (via my router).  Now it does not work.  

And I can longer run LMS on my PC (I have no idea why, as it ran fine previously), which is why it is now on the RPi using piCorePlayer linux-based OS (it is on a micro SD card).

---

### Post by david503 on 2019-01-02
> **merlinus said:**
> LMS resides on an RPi, which is hooked up to my sound system.  The shared folder is on my PC in another room.  I used to be able to stream music from the PC to the RPi using wireless (via my router).  Now it does not work.  

And I can longer run LMS on my PC (I have no idea why, as it ran fine previously), which is why it is now on the RPi using piCorePlayer linux-based OS (it is on a micro SD card).

OK so you're doing this (setting up the samba share), logged into the raspberrypi, and trying to see it's samba share from windows?

---

### Post by merlinus on 2019-01-02
From Ubuntu, not windows.  BTW, /var/lib/samba/usershares/ is empty.

---

### Post by david503 on 2019-01-02
> **merlinus said:**
> From Ubuntu, not windows.  BTW, /var/lib/samba/usershares/ is empty.

Oh I see.  Well what's the behavior when you try to connect? It just doesn't show up at all?  You can actually try to connect via CLI to the (LAN) ip address; I've done that before for troubleshooting a couple years ago.  

Other thing I can think of is maybe try a portscan with the nmap command. (Can't remember the arguments for it, but look at the man page or google for a tutorial, it's pretty straightforward; common.)   

Oh also if you haven't tried already- can you ping it?

You can get nmap by just "sudo apt-get install nmap", nothing fancy, it's an old command.

---

### Post by merlinus on 2019-01-02
I can connect to the RPi via firefox using its IP address, and to its LMS similarly.  But I cannot get LMS to connect to the samba shared folder on the PC.

---

### Post by david503 on 2019-01-02
> **merlinus said:**
> I can connect to the RPi via firefox using its IP address, and to its LMS similarly.  But I cannot get LMS to connect to the samba shared folder on the PC.

OK see I'm still confused- "[COLOR=#000000]the samba shared folder on the PC"?  The PC has a samba share too?  I thought you were saying that you want the PC to connect to the samba share on the rpi?  [/COLOR]

---

### Post by merlinus on 2019-01-02
No, the other way round.  The samba share is on the PC.

---

### Post by david503 on 2019-01-02
> **merlinus said:**
> No, the other way round.  The samba share is on the PC.

oohhhh ok so the Pi can't connect to the PC's (ubuntu's) samba share, got it.  

Well anyway, did you try what I suggeted- do a portscan from the Pi scanning the PC?

---

### Post by merlinus on 2019-01-02
This is scanning the RPi.

nmap 192.168.1.9

Starting Nmap 7.60 ( [https://nmap.org](https://nmap.org) ) at 2019-01-02 15:33 MST
Nmap scan report for 192.168.1.9
Host is up (0.013s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
9000/tcp open  cslistener
9090/tcp open  zeus-admin

Nmap done: 1 IP address (1 host up) scanned in 0.36 seconds

nmap is not installed on the RPi.

---

### Post by david503 on 2019-01-02
> **merlinus said:**
> This is scanning the RPi.

nmap 192.168.1.9

Starting Nmap 7.60 ( [https://nmap.org](https://nmap.org) ) at 2019-01-02 15:33 MST
Nmap scan report for 192.168.1.9
Host is up (0.013s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
9000/tcp open  cslistener
9090/tcp open  zeus-admin

Nmap done: 1 IP address (1 host up) scanned in 0.36 seconds

nmap is not installed on the RPi.

No, scanning the rpi is irrelevant.  You should scan the PC from the rpi.  Install nmap on the rpi is easy- ssh into it and just run "apt-get install nmap", it's a simple package.

---

### Post by merlinus on 2019-01-02
It does not recognize the apt command.  :confused:

---

### Post by david503 on 2019-01-02
Are you using apt or apt-get?  apt is like a squishy watered down wrapper for apt-get.

Also, do you know what os [COLOR=#000000]piCorePlayer is running?  Sounds like it's not debian.  

Type "yum" or "dnf".  Does it have either?


[/COLOR]

---

### Post by merlinus on 2019-01-02
No yum or dnf.  piCorePlayer uses piCore linux, a very small embedded Linux distribution that runs in RAM.

---

### Post by david503 on 2019-01-02
But it has a samba client... I guess that makes sense.  But it's running from an SD card right?  

When I had a rpi I set it up to be a classic game console using RetroPie, which was an SD card image... and anyway, it was running debian and had apt-get and stuff....  ug sounds like yours doesn't.  

well anyway it's 7pm my time, I gotta go out and eat, but I'll be around tomorrow.  someone else should chime in here, I maybe can't know it all myself!

Oh- maybe if you have another PC, like- do you have a laptop maybe?  You could try a port scan from that...

Anyway, gotta eat, good luck,

m

---

### Post by merlinus on 2019-01-02
Thanks for all your efforts and expertise.  Greatly appreciated!

Yes, it all runs from a microSD card.  And I can successfully scan my PC from another on the network.

---

