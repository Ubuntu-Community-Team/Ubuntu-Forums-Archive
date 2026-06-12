---
title: "Problem with stopping services"
date: 2015-06-07
forum: General Help
---

### Post by peter1897 on 2015-06-07
I have these services running on Ubuntu server:

```
ubuntu@ip-xx-xx-xx-xx:~$ nmap localhost

Starting Nmap 6.40 ( http://nmap.org ) at 2015-06-07 14:25 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00022s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
3389/tcp open  ms-wbt-server
5901/tcp open  vnc-1
5910/tcp open  cm
5911/tcp open  cpdlc
5915/tcp open  unknown
6001/tcp open  X11:1
```

I want to close all services except ssh because i want to close the open ports but if i type **sudo service name_of_service stop** it show **unrecognized service** message"

```
ubuntu@ip-xx-xx-xx-xx:~$ sudo service cm stop
cm: unrecognized service
```

How to close these services? Why does it show unrecognized service?

---

### Post by SeijiSensei on 2015-06-07
Because "cm" is not the name Ubuntu uses.  All the services are started or stopped by symbolic links in /etc/rc0.d through /etc/rc6.d to scripts in the /etc/init.d directory.  Look in that directory to see the names Ubuntu uses.

A quick solution is to block all inbound traffic to the server except for port 22 using iptables like this:
```

/sbin/iptables -I INPUT -p tcp -j REJECT
/sbin/iptables -I INPUT -p tcp --dport 22 -j ACCEPT

```
Using the "-I" switch adds these commands to the top of any existing iptables rule chain.  You thus have to insert them in the reverse of the order which you want them to apply.

Put these two lines in /etc/rc.local to run them at every reboot, or edit your existing iptables firewall (you do have one if the server is publicly-visible, right?) to only allow SSH.

---

### Post by TheFu on 2015-06-07
/etc/services - has the list of services that fills in the values. If there isn't one in the file for 5915, it is "unknown."

Best to scan from a different machine on the network. Just because something is available on localhost, that doesn't mean it is available to the world.

Turn off VNC to remove 3+ of those in your list.
ipp is for printing.
Do you use samba?

---

### Post by peter1897 on 2015-06-07
I don't want to block all inbound traffic because i may install services that will need to receive connection from internet.

But i still can't find to which services this names are connected. I looked at /etc/init.d but there is no entry with the name **cm**. I also looked at /etc/services and there is no entry with this name. I also search for the ports with which the service names are listed but none of the ports was listed in /etc/services.

---

### Post by steeldriver on 2015-06-07
AFAIK nmap's basic scan is only guessing what it thinks the service is, based on a lookup file:

```

$ grep -w 'cm' /usr/share/nmap/nmap-services
ris-cm    748/tcp    0.000113    # Russell Info Sci Calendar Manager
ris-cm    748/udp    0.001120    # Russell Info Sci Calendar Manager
mysql-cm-agent    1862/tcp    0.000228    # MySQL Cluster Manager Agent
mysql-cm-agent    1862/udp    0.000991    # MySQL Cluster Manager Agent
cpdi-pidas-cm    3609/udp    0.000330    # CPDI PIDAS Connection Mon
**cm    5910/tcp    0.000380    # Context Management**

```

For example, it's common to run VNC sessions on ports numbered as '5900+display number' - if I start one on display :10

```

$ vncserver :10

New 'X' desktop is T61p:10

Starting applications specified in /home/steeldriver/.vnc/xstartup
Log file is /home/steeldriver/.vnc/T61p:10.log


```

then sure enough
```

$ nmap localhost

Starting Nmap 6.40 ( http://nmap.org ) at 2015-06-07 12:29 EDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00067s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
631/tcp  open  ipp
3306/tcp open  mysql
**5910/tcp open  [COLOR=#ff0000]cm[/COLOR]**

Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds

```

whereas netstat confirms it's actually Xtightvnc:
```

$ sudo netstat -nltup | grep LISTEN
tcp        0      0 0.0.0.0:6010            0.0.0.0:*               LISTEN      10662/Xtightvnc 
tcp        0      0 0.0.0.0:54336           0.0.0.0:*               LISTEN      838/rpc.statd   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1285/mysqld     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      760/rpcbind     
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1797/dnsmasq    
**tcp        0      0 0.0.0.0:5910            0.0.0.0:*               LISTEN      10662/[COLOR=#0000ff]Xtightvnc [/COLOR]**
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1131/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      29230/cupsd     
tcp6       0      0 :::111                  :::*                    LISTEN      760/rpcbind     
tcp6       0      0 :::44148                :::*                    LISTEN      838/rpc.statd   
tcp6       0      0 :::22                   :::*                    LISTEN      1131/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      29230/cupsd     

```

---

### Post by peter1897 on 2015-06-07
This is the output i get with netstat:

```
ubuntu@ip-xx-xx-xx-xx:/etc/init.d$ sudo netstat -nltup | grep LISTEN
tcp        0      0 127.0.0.1:5910          0.0.0.0:*               LISTEN      4215/Xvnc
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      4119/xrdp-sesman
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1076/sshd
tcp        0      0 127.0.0.1:5911          0.0.0.0:*               LISTEN      4479/Xvnc
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      21762/cupsd
tcp        0      0 127.0.0.1:5912          0.0.0.0:*               LISTEN      4604/Xvnc
tcp        0      0 127.0.0.1:5913          0.0.0.0:*               LISTEN      5191/Xvnc
tcp        0      0 127.0.0.1:5914          0.0.0.0:*               LISTEN      5314/Xvnc
tcp        0      0 127.0.0.1:5915          0.0.0.0:*               LISTEN      5536/Xvnc
tcp        0      0 127.0.0.1:5916          0.0.0.0:*               LISTEN      6509/Xvnc
tcp        0      0 127.0.0.1:5917          0.0.0.0:*               LISTEN      7194/Xvnc
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      4117/xrdp
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      3469/Xvnc4
tcp6       0      0 :::22                   :::*                    LISTEN      1076/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      21762/cupsd
tcp6       0      0 :::5901                 :::*                    LISTEN      3469/Xvnc4
```

But the last column still doesn't display the real name of the services. If i try for example, **service xvnc stop** it still shows **unrecognized service**

---

### Post by steeldriver on 2015-06-07
... because it's probably not a *service*, it's a user-process - try

```

sudo lsof -i :5910

```

to see who owns it; you seem to have a bunch of similar Xvnc processes running on ports 5911-5917 - if you're using xrdp via sesman-Xvnc they may all be a result of that

---

### Post by TheFu on 2015-06-07
So - is your VNC service available over the internet?  Why so many processes? At least they are listening on localhost, not the internet.

[http://ubuntuforums.org/showthread.php?t=2280644](http://ubuntuforums.org/showthread.php?t=2280644) will be an interesting read for you.

I use x2go with 14.04 and later.  FreeNX with 12.04 and earlier. I don't touch VNC. X2go feels 2-3x faster. Night and day is common from people who switch from VNC to x2go.

---

### Post by CharlesA on 2015-06-07
They are listening on localhost, but that still seems odd to have that many VNC processes unless the machine is a VM host or something.

Same with RDP.

Running nmap on localhost will show a bunch of stuff that isn't accessible from outside the local machine, which is why it's a good idea to scan from another host on the same network.

---

### Post by peter1897 on 2015-06-07
I stoped xrdp service with the command **sudo service xrdp stop** but the xvnc entries are still there:

```
ubuntu@ip-xx-xx-xx-xx:/etc$ sudo netstat -nltup | grep LISTEN
tcp        0      0 127.0.0.1:5910          0.0.0.0:*               LISTEN      4215/Xvnc
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1076/sshd
tcp        0      0 127.0.0.1:5911          0.0.0.0:*               LISTEN      4479/Xvnc
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      21762/cupsd
tcp        0      0 127.0.0.1:5912          0.0.0.0:*               LISTEN      4604/Xvnc
tcp        0      0 127.0.0.1:5913          0.0.0.0:*               LISTEN      5191/Xvnc
tcp        0      0 127.0.0.1:5914          0.0.0.0:*               LISTEN      5314/Xvnc
tcp        0      0 127.0.0.1:5915          0.0.0.0:*               LISTEN      5536/Xvnc
tcp        0      0 127.0.0.1:5916          0.0.0.0:*               LISTEN      6509/Xvnc
tcp        0      0 127.0.0.1:5917          0.0.0.0:*               LISTEN      7194/Xvnc
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      3469/Xvnc4
tcp6       0      0 :::22                   :::*                    LISTEN      1076/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      21762/cupsd
tcp6       0      0 :::5901                 :::*                    LISTEN      3469/Xvnc4
```

I tried also **sudo service vncserver stop** but again it shows **unrecognized service**.

If this is process and not service how to stop it? If i run lsof command i get this:
```
ubuntu@ip-xx-xx-xx-xx:/etc$ sudo lsof -i :5910
COMMAND  PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
Xvnc    4215 ubuntu    1u  IPv4  58574      0t0  TCP localhost:5910 (LISTEN)
```

I have so many VNC processes because i tried to create remote desktop connection so i installed bunch of desktop environments for testing but i didn't get much of success.

With x2go and FreeNX can i create remote desktop connection from Windows 7 to Ubuntu 14.04?

---

### Post by Lars Noodén on 2015-06-07
> **TheFu said:**
> 
Best to scan from a different machine on the network. Just because something is available on localhost, that doesn't mean it is available to the world.


+1 

You can safely ignore the output from that scan because it is being done against the very same machine that the scanner resides on.  As a result you won't get any useful results.  In order to see what is really exposed or not you will have to run the scan from a second machine on the same subnet.

---

### Post by peter1897 on 2015-06-07
I tried this command **pkill -U ubuntu** which stopped all processes owned by ubuntu user and now all vnc processes disappeared except one:

```
ubuntu@ip-xx-xx-xx-xx:~$ sudo netstat -nltup | grep LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1076/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      21762/cupsd
tcp        0      0 127.0.0.1:5917          0.0.0.0:*               LISTEN      7194/Xvnc
tcp6       0      0 :::22                   :::*                    LISTEN      1076/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      21762/cupsd
```

---

### Post by TheFu on 2015-06-07
> **peter1897 said:**
> With x2go and FreeNX can i create remote desktop connection from Windows 7 to Ubuntu 14.04?

Use x2go, yes. There is a server for Ubuntu and clients for Windows, Ubuntu, OSX.  I use the Windows and Ubuntu clients daily. They are very stable and if you tune the connection, extremely fast.

When I moved to 14.04, FreeNX wasn't ready, so I switched to x2go. Couldn't be happier, though being forced to use an x2go client is a downside. x2go is just different enough for other NX clients not to be compatible.

Follow the install instructions here: [http://wiki.x2go.org/doku.php/doc:installation:x2goserver](http://wiki.x2go.org/doku.php/doc:installation:x2goserver) which will setup a PPA, then install the server on the remote system and install the clients on which ever clients you need.   Prefer using ssh-key-based authentication, over passwords.  On a fast LAN, audio and video can work.  Also automatic local disk sharing and printing is possible.  Over remote connections through the internet, those things generally aren't possible due to firewalls at the client-side location, as we would expect.  You may want to install more fonts on the Windows side. I don't recall the details, just that there was a separate font package for Windows.

Also, note which DEs are supported and be certain to use (and have previously working) one of the supported choices.  Later, you can mess with the "Custom" option and go crazy. Any DE that requires 3D accel GPU support CANNOT be used.

---

### Post by peter1897 on 2015-06-08
I installed x2go server on Ubuntu server and was able to connect to it from Windows 7. The connection is better than the connection to xrdp, it's faster for sure.

---

### Post by TheFu on 2015-06-08
> **peter1897 said:**
> I installed x2go server on Ubuntu server and was able to connect to it from Windows 7. The connection is better than the connection to xrdp, it's faster for sure.

So ...

a) x2go, is one of those few things that is **both** more secure AND more convenient, like ssh. I switched years ago, and wonder why all these people keep bothering with RDP and VNC at all. Sometimes I'll x2go into a Linux machine on a home network, then use rdesktop to connect to a Windows Media Center box to check the TV schedule in a grid and ensure or schedule a show to be recorded.  remote desktop-to-remote-desktop works.  I've showed people the PgUp/PgDn through those schedules to show how good x2go is for screen updates. Then explain that I was running a rdp to NX to local remote desktop. Yaws drop.

b) **solved**?  If so, mark the thread as solved, please.


I've been using x2go/NX to remote into my primary desktop for a few yrs now. That desktop OS runs inside a private cloud that is available world-wide. No matter what the local situation might be with government tracking, I don't worry, because all the traffic is tunneled to my home network provider and sucked up when it leaves there by the NSA/GCHQ just like normal. They would miss me otherwise. ;)

---

### Post by JKyleOKC on 2015-06-08
> **peter1897 said:**
> This is the output i get with netstat:

```
ubuntu@ip-xx-xx-xx-xx:/etc/init.d$ sudo netstat -nltup | grep LISTEN
tcp        0      0 127.0.0.1:5910          0.0.0.0:*               LISTEN      4215/Xvnc
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      4119/xrdp-sesman
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1076/sshd
tcp        0      0 127.0.0.1:5911          0.0.0.0:*               LISTEN      4479/Xvnc
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      21762/cupsd
tcp        0      0 127.0.0.1:5912          0.0.0.0:*               LISTEN      4604/Xvnc
tcp        0      0 127.0.0.1:5913          0.0.0.0:*               LISTEN      5191/Xvnc
tcp        0      0 127.0.0.1:5914          0.0.0.0:*               LISTEN      5314/Xvnc
tcp        0      0 127.0.0.1:5915          0.0.0.0:*               LISTEN      5536/Xvnc
tcp        0      0 127.0.0.1:5916          0.0.0.0:*               LISTEN      6509/Xvnc
tcp        0      0 127.0.0.1:5917          0.0.0.0:*               LISTEN      7194/Xvnc
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      4117/xrdp
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      3469/Xvnc4
tcp6       0      0 :::22                   :::*                    LISTEN      1076/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      21762/cupsd
tcp6       0      0 :::5901                 :::*                    LISTEN      3469/Xvnc4
```

But the last column still doesn't display the real name of the services. If i try for example, **service xvnc stop** it still shows **unrecognized service**I'm amazed that nobody suggested trying **service [COLOR="#FF0000"]Xvnc[/COLOR] stop** instead of **service [COLOR="#FF0000"]xvnc[/COLOR] stop** before going the long way around...

Could it be that my editor's eye is the only one noting the difference here? Case sensitivity seems to be one of the major causes of problems for those who are relatively new to Linux!

---

### Post by CharlesA on 2015-06-08
> **JKyleOKC said:**
> I'm amazed that nobody suggested trying **service [COLOR="#FF0000"]Xvnc[/COLOR] stop** instead of **service [COLOR="#FF0000"]xvnc[/COLOR] stop** before going the long way around...

Could it be that my editor's eye is the only one noting the difference here? Case sensitivity seems to be one of the major causes of problems for those who are relatively new to Linux!

Possible I guess, but I've never seen any init scripts that were capitalized.

---

### Post by JKyleOKC on 2015-06-09
I'm just going by the netstat report -- it's the only process listed that has an initial capital, and many of the X components seem to swim against the current when it comes to such capitalization. However the only file in my /etc/init.d for this server is named x11-common, making me think that perhaps the netstat process name isn't really a reliable source for use with "service" calls...

---

### Post by CharlesA on 2015-06-09
> **JKyleOKC said:**
> I'm just going by the netstat report -- it's the only process listed that has an initial capital, and many of the X components seem to swim against the current when it comes to such capitalization. However the only file in my /etc/init.d for this server is named x11-common, making me think that perhaps the netstat process name isn't really a reliable source for use with "service" calls...

Gotcha. That makes sense, thanks. :)

---

