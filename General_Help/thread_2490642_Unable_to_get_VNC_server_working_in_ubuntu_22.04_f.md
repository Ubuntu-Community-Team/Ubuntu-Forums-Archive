---
title: "Unable to get VNC server working in ubuntu 22.04 for remote desktop viewer"
date: 2023-09-11
forum: General Help
---

### Post by appusony on 2023-09-11
Dear All,

Good Morning!

As I am in need of remote desktop viewer form windows 10 (vnc client - Real Vnc) trying to view Ubuntu 22.04 (Server). for both of my user accounts called 1. srishanm 2. foreman

I was installing vnc server on my ubuntu machine, 22.04.3 , by using the reference as [https://serverspace.io/support/help/install-tightvnc-server-on-ubuntu-20-04/](https://serverspace.io/support/help/install-tightvnc-server-on-ubuntu-20-04/) -> though this link is for ubuntu 20.04, assumed this would work even for ubunut 22.04

I have two user accounts 1. srishanm & 2. foreman. Need to switch between these two user accounts.

For now, Currently I am unable to start vncserver/get vnc server working on one user account ie., 'srishanm' itself (but later I need to switch from srishanm user account to even foreman account as well please) -> it is throwing: "Failed to start [EMAIL="vncserver@:2.servic"]vncserver@:2.servic[/EMAIL]e: Unit [EMAIL="vncserver@:2.servic"]vncserver@:2.servic[/EMAIL]e not found."


Tried even removing this file also ,** ie., /tmp/.X1-lock**

> srishanm@srishanm-Cloudripper:~$ vncserver


You will require a password to access your desktops.


Password:
Verify:
Would you like to enter a view-only password (y/n)? y
Password:
Verify:


Warning: srishanm-Cloudripper:1 is taken because of /tmp/.X1-lock
Remove this file if there is no X server srishanm-Cloudripper:1


New 'X' desktop is srishanm-Cloudripper:2


Creating default startup script /home/srishanm/.vnc/xstartup
Starting applications specified in /home/srishanm/.vnc/xstartup
Log file is /home/srishanm/.vnc/srishanm-Cloudripper:2.log


srishanm@srishanm-Cloudripper:~$

As I am facing the below:

> srishanm@srishanm-XXXXXXXXXXX:~$ systemctl start [EMAIL="vncserver@:2.servic"]vncserver@:2.servic[/EMAIL]e
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to start 'vncserver@:2.service'.
Multiple identities can be used for authentication:
1. srishanm,,, (srishanm)
2. ,,, (foreman)
Choose identity to authenticate as (1-2): 1
Password:
==== AUTHENTICATION COMPLETE ===
**Failed to start [EMAIL="vncserver@:2.servic"]vncserver@:2.servic[/EMAIL]e: Unit [EMAIL="vncserver@:2.servic"]vncserver@:2.servic[/EMAIL]e not found.**
srishanm@srishanm-XXXXXXXXXXX:~$


1.

root@srishanm-XXXXXXXXXXX:/# vncserver


```
New 'X' desktop is srishanm-XXXXXXXXXXX:2


Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/srishanm-XXXXXXXXXXX:2.log

```

root@srishanm-XXXXXXXXXXX:/#

2.
srishanm@srishanm-XXXXXXXXXXX:~$ cat /etc/systemd/system/vncserver.service
```
[Unit]
   Description=TightVNC server
   After=syslog.target network.target


[Service]
   Type=forking
   User=root
   PAMName=login
   PIDFile=/root/.vnc/%H:1.pid
   ExecStartPre=-/usr/bin/vncserver -kill :2 > /dev/null 2>&1
   ExecStart=/usr/bin/vncserver
   ExecStop=/usr/bin/vncserver -kill :2


[Install]
   WantedBy=multi-user.target
srishanm@srishanm-XXXXXXXXXXX:~$

```

Could you please help me with you inputs or pointers please, is there something am I missing or doing wrong please? , I have even tried installing xrdp, & I have done all the settings  ubuntu 22.04 side ,  shown as per the link [https://linuxhint.com/enable-remote-desktop-ubuntu-access-windows/](https://linuxhint.com/enable-remote-desktop-ubuntu-access-windows/)

many many thanks in advance.

Best wishes,

---

### Post by appusony on 2023-09-11
As another option, I tried even with xrdp. Though I somehow got xrdp protocol status to be running.

> srishanm@srishanm-XXXXXXXXX:~$ sudo service xrdp status
&#9679; xrdp.service - xrdp daemon
     Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-09-11 17:21:17 IST; 10min ago
       Docs: man:xrdp(8)
             man:xrdp.ini(5)
    Process: 1831 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
    Process: 1862 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=0/SUCCESS)
   Main PID: 1895 (xrdp)
      Tasks: 1 (limit: 154204)
     Memory: 2.8M
        CPU: 111ms
     CGroup: /system.slice/xrdp.service
             &#9492;&#9472;1895 /usr/sbin/xrdp


Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] xrdp_wm_log_msg: sesman connect ok
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] sesman connect ok
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] sending login info to session manager, please wait...
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] xrdp_wm_log_msg: login successful for display 10
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] login successful for display 10
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] loaded module 'libxup.so' ok, interface size 10296, version 4
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] started connecting
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] lib_mod_connect: connecting via UNIX socket
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] lib_mod_log_peer: xrdp_pid=5886 connected to X11rdp_pid=5889 X11rdp_uid=1000 X11rdp_gid=1000 client_ip=::ffff:10.252.204.161>
Sep 11 17:27:10 srishanm-XXXXXXXXX xrdp[5886]: [INFO ] connected ok


srishanm@srishanm-XXXXXXXXX:~$




Now that XRDP disconnects immediately (after I enter my  correct credentials ie., after entering my password) from my windows 10.

ie., [COLOR=#000000][FONT=verdana]When I try to connect with Remote Desktop from Windows 10 , I am asked for the credentials of the PC, in the XRDP login panel.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]But after the OK, after only a few seconds, the window closes and the connection panel returns in Windows.[/FONT][/COLOR]

Any advises , would be highly appreciated onto this.

Many thanks in advance

---

### Post by TheFu on 2023-09-11
VNC is the wrong tool for this.  Use **x2go**. 
[https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)

If you don't actually need a GUI, then ssh/PuTTY would be much preferred.

---

### Post by kurt18947 on 2023-09-11
Does x2go work with Wayland? My understanding that the lack of remote desktop viewer is one of the shortcomings of Wayland. I don't need a remote desktop viewer right now  but my system likes Wayland better than Xorg, video is less crash-prone. Trying to be prepared.

---

### Post by TheFu on 2023-09-11
> **kurt18947 said:**
> Does x2go work with Wayland? My understanding that the lack of remote desktop viewer is one of the shortcomings of Wayland. I don't need a remote desktop viewer right now  but my system likes Wayland better than Xorg, video is less crash-prone. Trying to be prepared.

IDK, doubtful.  I can't use Wayland. It doesn't support a number of my workflows.

---

### Post by MAFoElffen on 2023-09-11
Your errors above note that you were trying to access vnc as root, and failed when it tried to look for Xauthority in the root user directory. That is not possible, as root cannot do X... Did you try to use it as a regular user instead, that does have an account that can start an X Session? (not Wayland)

With Windows as the client, accessing an Ubuntu Server, I use xrdp as the server, using RDP from Windows. That is native to Windows OS, with nothing to install on that end. One limitation that you must understand with RDP, is that you cannot access a server with an account that is logged in. So most admin's will create a dummy account for that access, to insure it is only used for xrdp access. The next limitation is in the name... xrdp, implies an XServer session... Same thing, the user has to have rights and privilegdes to have a working GUI session.

x2go also uses XServer... Not Wayland.

You can also do XForwarding on Windows if you install XServer on it via XMing or Cygwin/X, tunneled in SSH... 

VNC uses it's own protocol... If you want to use VNC, you need to find a VNC Viewer that works on Windows. And a compatible VNC Server for Ubuntu. Vino used to be the default VNC Server for Ubuntu. Not sure what is now: [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

Note that my experience with VNC viewers it that there is always going to be some lag. It's just in the way they send the graphical desktop.

---

### Post by appusony on 2023-09-11
Thank you very much to all my dear friends for all your valuable & wonderful inputs & pointer above.

With the below portion of comment:

> [COLOR=#000000]With Windows as the client, accessing an Ubuntu Server, I use xrdp as the server, using RDP from Windows. That is native to Windows OS, with nothing to install on that end. One limitation that you must understand with RDP, is that you cannot access a server with an account that is logged in. So most admin's will create a dummy account for that access, to insure it is only used for xrdp access. The next limitation is in the name... xrdp, implies an XServer session... Same thing, the user has to have rights and privilegdes to have a working GUI session.

Could you please let me know:

As I got my xrdp server up & running, but [/COLOR][COLOR=#000000][COLOR=#000000][FONT=verdana]When I try to connect with Remote Desktop from Windows 10 , I am asked for the credentials of the PC, in the XRDP login panel.[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=verdana]But after the OK, after only a few seconds, the window closes and the connection panel returns in Windows. -> Any tips or pointers, how to resolve this please?[/FONT][/COLOR][/COLOR][COLOR=#000000]

 Could you please elaborate, what is meant by in the above portion of the comments please: 

1. [/COLOR][COLOR=#000000]One limitation that you must understand with RDP, is that **you cannot access a server with an account that is logged in**. **So most admin's will create a dummy account for that access?**, to insure it is only used for xrdp access.
[/COLOR][COLOR=#000000]2. [/COLOR][COLOR=#000000]The next limitation is in the name... xrdp, implies an XServer session... Same thing, **the user has to have rights and privilegdes to have a working GUI session?**[/COLOR][COLOR=#000000]
[/COLOR]
Many thanks in advance.

Best Wishes,

---

### Post by TheFu on 2023-09-12
a) if you use x2go, those limitation don't exist.  x2go uses Linux credentials and ssh for authentication.
b) x2go is based on VNC, actually, but a more efficient, compressed, encrypted, protocol.  The remote x2go-server provides it's own X-server (actually from 2009).  The x2go client has been implemented for Windows, Linux, BSD, and MacOS.

If you aren't allowed to install the x2go-client on the workstation you sit behind, then it won't work. x2go and all NX clients/servers are tightly coupled. A server from one team won't work with a client from another.

As for RDP, over the last 10 yrs, MSFT has added different authentication and encryption modes to the RDP clients and servers.  For a while, the xrdp project has been behind on support for newer MSFT attempts to prevent unauthorized access.  RDP is commonly hacked.  So is VNC.  x2go, being NX-based and using ssh credentials+encryption has the same liabilities of ssh, which are well-known and mitigated, especially if we use ssh-keys, never passwords, for our credentials.

Additionally, when crossing OSes, x2go feels 2-3x faster than the other alternatives and it can be tuned for slower connections.  For really fast connections, especially on the same LAN, just use the normal X/Windows remote tunneling through ssh. That has worked well for 25+ year.  I use it constantly. In fact, this browser window is running over a remote-X11 connection from another system. It works that well.  

For about a year, I used a Windows desktop with NX to run Linux full screen nearly all day, every day. It was very good. That was over a decade ago.  Eventually, my need for MS-Windows dissipated and when I finally realized it wasn't needed, except for niche requirements, then I loaded a Linux desktop and basically use Windows just 1-2 a month.

---

### Post by MAFoElffen on 2023-09-12
Most viewers are going to Use XServer to connect to a Linux Machine, except for VNC and RDP.

RDP (Remote Desktop Protocol) is Single User Access: By default, Windows only allows one user an active RDP user session at a time. This means that if you log in using Remote Desktop, on a Windows machine- you will be logged out of the local session. On anything else, you will be exclude from connecting the session. This is how xrdp handles that, in that grouping.

This is an Ubuntu Linux machine with a local user logged in, with another user (username=xrdp-user) connected:
```

mafoelffen@xrdp-02:~$ w
 07:35:20 up  1:44,  1 user,  load average: 0.19, 0.05, 0.01
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
mafoelff tty2     tty2             07:04    1:44m  0.00s  0.00s /usr/libexec/gd
mafoelffen@xrdp-02:~$ echo 'XRDP USERS:'; \
echo 'USER     PID'; \
ps -ef | awk '/gnome-keyring/ {print $1,$2,$10}' | \
awk '/--components=secrets/ {print $1 " " $2}'

XRDP USERS:
USER     PID
xrdp-us+ 8429

```
You can configure a Windows System to allow multiple active sessions by enabling "Remote Desktop Services and Terminal Services". That feature is a paid, extra added/installed service for Windows Server (only).

RDP is native to Windows OS, not to Linux. That means you have to install things on the Linux side. XServer is native to Linux, but not to Windows. That means you have to install things on the Windows side. VNC is not native to either, so you install things on both sides. 

IMHO: Remote XServer sessions are going to be faster in how it does things. It renders the graphics locally, and just has to send very little information for XServer to render it. With most network connections, it is truly like you are there on that computer, performance wise... Graphically, the quality of the desktop is better than other methods. RDP, even Windows machines to other Windows machines, the desktop always looks different. That is just the truth.

---

### Post by appusony on 2023-09-12
Thank you I tried to install x2Go, as per screenshot by following the link [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go) , I was unable to connect to my remote Ubuntu desktop, I installed on ubuntu 22.04.3 ie., "[COLOR=#000000][FONT=Consolas]**apt-get install**[/FONT][/COLOR][COLOR=#666666][FONT=Consolas] x2goclient" -> [/FONT][/COLOR]https://wiki.x2go.org/doku.php/doc:newtox2go, On client side ie., my windows 10 side - > "X2GoClient_latest_mswin32-setup" -> Any tips or pointers here please?, any additional configuration needs to be done on Windows or Ubuntu side please?

---

### Post by TheFu on 2023-09-12
> **appusony said:**
> Thank you I tried to install x2Go, as per screenshot by following the link [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go) , I was unable to connect to my remote Ubuntu desktop, I installed on ubuntu 22.04.3 ie., "[COLOR=#000000][FONT=Consolas]**apt-get install**[/FONT][/COLOR][COLOR=#666666][FONT=Consolas] x2goclient" -> [/FONT][/COLOR]https://wiki.x2go.org/doku.php/doc:newtox2go, On client side ie., my windows 10 side - > "X2GoClient_latest_mswin32-setup" -> Any tips or pointers here please?, any additional configuration needs to be done on Windows or Ubuntu side please?

Did you get **ssh** working between the systems first?

---

### Post by MAFoElffen on 2023-09-12
+1 --

LOL. I have what might seem like a dumb question. In Post #1:
> **appusony said:**
> 
As I am in need of remote desktop viewer form windows 10 (vnc client - Real Vnc) trying to view [COLOR=#ff0000]Ubuntu 22.04 **(Server)**[/COLOR]. for both of my user accounts called 1. srishanm 2. foreman

For a Linux Server, I connect and manage them solely via 'ssh'. There is no installed GUI desktop on Server, so there is no GUI to render. Later you mentioned "Wayland", so I assumed that you must have installed a Desktop on your server...

Do you have a Desktop installed on your 'server'? 

If not, then none of those viewers have a Desktop to render... No judgement. Just a curious observation.

---

### Post by appusony on 2023-09-12
X2go is getting timed out, as per screenshot, any advises here please?

---

### Post by appusony on 2023-09-12
> [COLOR=#000000]Did you get [/COLOR]**ssh working between the systems first?**

yes please, ssh is working , I checked via Mobaxterm.

---

### Post by appusony on 2023-09-12
> [COLOR=#000000]Do you have a Desktop installed on your 'server'?[/COLOR]

No please, this was a Ubuntu desktop 22.04.3 version installed on my desktop machine.

---

### Post by appusony on 2023-09-12
Just for references, here is the x2go beginning screen please (where I enter ip addr) . & after that it proceeds to "x2go_2 screenshot" & after this it gets timeout please. pls let me know if am I missing anything in this beginning screen please?

---

### Post by appusony on 2023-09-12
X2go is saying "Unable to excute: startkde" in this screenshot, when I was trying after logging in, anything please, should I need to change from KDE to something else in the beginning screen, as I am trying to connect Ubuntu 22.04 from windows please?

---

### Post by appusony on 2023-09-12
Sorry I forgot to attach one more screen shot, before I get unable to startKDE", the pulse audio is not working

---

### Post by TheFu on 2023-09-12
Looks to me like Canonical is having network problems.

```
 7:  68.85.92.105                                         14.641ms 
 8:  no reply
 9:  ae-9.edge4.Atlanta2.Level3.net                       22.504ms asymm 10 
10:  swp10.il3-core1.canonical.com                       112.775ms asymm 23 
11:  il3-fw2.canonical.com                               101.891ms asymm 24 
12:  il3-fw2.canonical.com                               102.639ms asymm 24 
13:  no reply
14:  no reply
...
```

Anyway, picking a light GUI is best, so above KDE or Gnome, which really want direct access to the GPU and that isn't possible over a remote connection.  Install and use something like xfce or lxqt instead if you need a DE. Or if you want something lighter, choose just a window manager like openbox or fvwm.  I always specify the _**full path**_ to the WM I use in the x2go-client settings.  That means it starts with a '/' .... for example, /usr/bin/fvwm is what I use for fvwm as my window manager.  You probably would be happier with **openbox**.  Be certain that is installed on the remote system.

---

### Post by MAFoElffen on 2023-09-12
Network speed issue? When I am testing network speeds between two servers, I use 'iperf'
```

[LIST]
[*]Server. Run the following command on the server machine: iperf -s -i 10. ... 
[*]Client. On the client run the following command: iperf -i 10 -c <SERVER> ... 
[*]Result. Every 10 seconds the measured network speed will be printed on the client and server. 
[/LIST]

```
'iperf' ([https://iperf.fr](https://iperf.fr)) is Cross-platform: Windows, Linux, Android, MacOS X, FreeBSD, OpenBSD, NetBSD, VxWorks, Solaris... So works on most anything.

If on a local network, using x2go with KDE should be fine. Look at the error...

---

### Post by MAFoElffen on 2023-09-12
From x2go's documentation... When x2go has this error: 
```

ERROR: "Unable to execute: xfce4-session"

```
That error means that the desktop session is not installed correctly and most likely either needs to be reinstalled or reconfigured. That error does not mean that it has a connection problem.

Remember when I said that the user you use on a remote viewer in Linux needs to have the right permissions and right to display a Desktop Session? That implies, that you can physically go to that machine, log in with that User's credentials, and that User has a functioning Desktop Session. Please test this to ensure you haven't skipped over that step... If there is a problem with that, fix that first.

---

### Post by TheFu on 2023-09-13
> **MAFoElffen said:**
>  
If on a local network, using x2go with KDE should be fine. Look at the error...

From x2go's documentation... When x2go has this error: 
```

ERROR: "Unable to execute: xfce4-session"

```
That error means that the desktop session is not installed correctly and most likely either needs to be reinstalled or reconfigured. That error does not mean that it has a connection problem.

Remember when I said that the user you use on a remote viewer in Linux needs to have the right permissions and right to display a Desktop Session? That implies, that you can physically go to that machine, log in with that User's credentials, and that User has a functioning Desktop Session. Please test this to ensure you haven't skipped over that step... If there is a problem with that, fix that first.

I use iperf3.

x2go provides a virtual X/Server on the remote system, so there doesn't actually need to be a GPU and you don't need to be able to walk up and run a desktop session on it.
KDE became unsupported by x2go when they moved to Plasma. Plasma wants direct access to the GPU. x2go doesn't have any GPU. [https://wiki.x2go.org/doku.php/doc:de-compat](https://wiki.x2go.org/doku.php/doc:de-compat) has suggestions for DEs/WMs.  Seems that KDE 5 might work, but it isn't plug-in-work easy.  Best to use xfce.  KDE used to work, pre-plasma.

---

### Post by appusony on 2023-09-14
> **TheFu said:**
> Looks to me like Canonical is having network problems.

```
 7:  68.85.92.105                                         14.641ms 
 8:  no reply
 9:  ae-9.edge4.Atlanta2.Level3.net                       22.504ms asymm 10 
10:  swp10.il3-core1.canonical.com                       112.775ms asymm 23 
11:  il3-fw2.canonical.com                               101.891ms asymm 24 
12:  il3-fw2.canonical.com                               102.639ms asymm 24 
13:  no reply
14:  no reply
...
```

Anyway, picking a light GUI is best, so above KDE or Gnome, which really want direct access to the GPU and that isn't possible over a remote connection.  Install and use something like xfce or lxqt instead if you need a DE. Or if you want something lighter, choose just a window manager like openbox or fvwm.  I always specify the _**full path**_ to the WM I use in the x2go-client settings.  That means it starts with a '/' .... for example, /usr/bin/fvwm is what I use for fvwm as my window manager.  You probably would be happier with **openbox**.  Be certain that is installed on the remote system.


I tried to install fvwm window manager in my ubuntu.

srishanm@srishanm:~$ sudo apt-get install -y fvwm
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libperl4-corelibs-perl librplay3 libstroke0
Suggested packages:
  perl-tk stalonetray
The following NEW packages will be installed:
  fvwm libperl4-corelibs-perl librplay3 libstroke0
0 upgraded, 4 newly installed, 0 to remove and 15 not upgraded.
Need to get 2,461 kB of archives.
After this operation, 7,105 kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/main amd64 libperl4-corelibs-perl all 0.004-2 [37.4 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 librplay3 amd64 3.3.2-18 [22.5 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 libstroke0 amd64 0.5.1-9 [9,696 B]
Get:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 fvwm amd64 1:2.6.8-1build1 [2,391 kB]
Fetched 2,461 kB in 3s (828 kB/s)
Selecting previously unselected package libperl4-corelibs-perl.
(Reading database ... 242826 files and directories currently installed.)
Preparing to unpack .../libperl4-corelibs-perl_0.004-2_all.deb ...
Unpacking libperl4-corelibs-perl (0.004-2) ...
Selecting previously unselected package librplay3.
Preparing to unpack .../librplay3_3.3.2-18_amd64.deb ...
Unpacking librplay3 (3.3.2-18) ...
Selecting previously unselected package libstroke0:amd64.
Preparing to unpack .../libstroke0_0.5.1-9_amd64.deb ...
Unpacking libstroke0:amd64 (0.5.1-9) ...
Selecting previously unselected package fvwm.
Preparing to unpack .../fvwm_1%3a2.6.8-1build1_amd64.deb ...
Unpacking fvwm (1:2.6.8-1build1) ...
Setting up libstroke0:amd64 (0.5.1-9) ...
Setting up libperl4-corelibs-perl (0.004-2) ...
Setting up librplay3 (3.3.2-18) ...
Setting up fvwm (1:2.6.8-1build1) ...
update-alternatives: using /usr/bin/fvwm2 to provide /usr/bin/fvwm (fvwm) in auto mode
update-alternatives: using /usr/bin/fvwm2 to provide /usr/bin/x-window-manager (x-window-manager) in auto mode
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin 

I was unable to do few things:

1. I was unable to provide full fvwm path
2. I was unable to execute - "Unable to execute - open-box session"

May I know please, is there anything that am I missing again w.r.t open-box session please?

Many thanks in advance again,

Best Wishes,

---

### Post by TheFu on 2023-09-14
Why would installing fvwm get you openbox? That doesn't make sense. fvwm isn't easy, just what I use. I probably shouldn't have mentioned it at all.

Why can't you provide the full path?  Do you know know how to find it?  Use **which**.  BTW, the output you posted above shows  /usr/bin/fvwm2, which would be the command to use.  Sorry - fvwm2 has been around 20+ yrs, so I don't think of it as different from fvwm (it isn't anymore).

So, if you want **openbox**, you'll need to 
[LIST=1]
[*]install that package.  use ssh.
[*]run "which openbox" to get the full path, use ssh.
[*]setup a custom x2go connection to the system ... put the location of the openbox binary into the custom launcher location. Youj didn't tell x2go which program to run. Fill in the "Command:" field.
[*]Try the connection.  
[*]When it comes up, right-click anywhere on the desktop, hold it down, wait for a menu to appear.  Try left and center clicking menus too.  I think openbox uses an XML config file, though it isn't required. There are lots of config file examples, so you can add specific programs to the menu, if you don't like the defaults.
[/LIST]

You'll need to read the manpage for openbox and do some web searches for anything beyond the defaults.  For many years, openbox was the WM used by LXDE, but that project lost favor as GTK+ versioned made staying with GTK for LXDE extremely difficult. LXDE became LXQt, which is based off Qt libraries - more like KDE, but still light.

fvwm doesn't have many defaults. I believe everything must be customized, including all menus.  I've been pulling the same config file forward since the mid-1990s, slightly changing it when desired or when needed.  fvwm does have packages which will apply a full theme. fvwm-crystal can be nice, but I find the window decorations to be much to large.  Tweaking a text init file can be daunting for noobs.  But fwvm has been doing things like transparency since the mid-1990s. 

To manage a remote server it would be better to learn to use the CLI over ssh instead. OTOH, if you aren't happy with the DEs currently popular, just know that there are options which can be customized exactly to your needs. If you just need something once a month, it isn't worth it, but if you will be using a desktop for the next 2-30 yrs, then spending a little time learning and customizing will pay off over the long term.  Unlike the DE people who have to put up with programmers deciding what they need because it is "new", with fvwm, you get to decide what you need.  OTOH, you HAVE TO decide what you need too.  I think it is much too early in your linux use to know what you need.  

Stick with openbox and the easy stuff for now.

---

### Post by appusony on 2023-09-15
Thanks a lot for your quick & prompt replies, really much appreciate your support.

I have no problem with ssh command line interface, but since my dev machine is connected in remote , I am accessing VM's which is UI based, hence I might need it for longer time

Could you please help me or bear with me, would love to learn from you, in helping me bringing up the X2go demote desktop viewer up and running please?

Now that I have installed openbox

srishanm@srishanm-xxxxxxxxx:~$ sudo apt install openbox obconf
[sudo] password for srishanm:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libid3tag0 libimlib2 libobrender32v5 libobt2v5 scrot
Suggested packages:
  fonts-dejavu libxml2-dev tint2 openbox-gnome-session openbox-kde-session
The following NEW packages will be installed:
  libid3tag0 libimlib2 libobrender32v5 libobt2v5 obconf openbox scrot
0 upgraded, 7 newly installed, 0 to remove and 15 not upgraded.
Need to get 816 kB of archives.
After this operation, 3,584 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 libid3tag0 amd64 0.15.1b-14 [31.3 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 libimlib2 amd64 1.7.4-1build1 [195 kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 libobt2v5 amd64 3.6.1-10 [35.5 kB]
Get:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 libobrender32v5 amd64 3.6.1-10 [42.4 kB]
Get:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 obconf amd64 1:2.0.4+git20150213-2build1 [141 kB]
Get:6 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 openbox amd64 3.6.1-10 [311 kB]
Get:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) jammy/universe amd64 scrot amd64 1.7-1 [60.5 kB]
Fetched 816 kB in 3s (298 kB/s)
Selecting previously unselected package libid3tag0:amd64.
(Reading database ... 243070 files and directories currently installed.)
Preparing to unpack .../0-libid3tag0_0.15.1b-14_amd64.deb ...
Unpacking libid3tag0:amd64 (0.15.1b-14) ...
Selecting previously unselected package libimlib2:amd64.
Preparing to unpack .../1-libimlib2_1.7.4-1build1_amd64.deb ...
Unpacking libimlib2:amd64 (1.7.4-1build1) ...
Selecting previously unselected package libobt2v5.
Preparing to unpack .../2-libobt2v5_3.6.1-10_amd64.deb ...
Unpacking libobt2v5 (3.6.1-10) ...
Selecting previously unselected package libobrender32v5.
Preparing to unpack .../3-libobrender32v5_3.6.1-10_amd64.deb ...
Unpacking libobrender32v5 (3.6.1-10) ...
Selecting previously unselected package obconf.
Preparing to unpack .../4-obconf_1%3a2.0.4+git20150213-2build1_amd64.deb ...
Unpacking obconf (1:2.0.4+git20150213-2build1) ...
Selecting previously unselected package openbox.
Preparing to unpack .../5-openbox_3.6.1-10_amd64.deb ...
Unpacking openbox (3.6.1-10) ...
Selecting previously unselected package scrot.
Preparing to unpack .../6-scrot_1.7-1_amd64.deb ...
Unpacking scrot (1.7-1) ...
Setting up libid3tag0:amd64 (0.15.1b-14) ...
Setting up libobt2v5 (3.6.1-10) ...
Setting up libimlib2:amd64 (1.7.4-1build1) ...
Setting up libobrender32v5 (3.6.1-10) ...
Setting up scrot (1.7-1) ...
Setting up obconf (1:2.0.4+git20150213-2build1) ...
Setting up openbox (3.6.1-10) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for shared-mime-info (2.1-2) ...
srishanm@srishanm-xxxxxxxxx:~$ which openbox
/usr/bin/openbox
srishanm@srishanm-xxxxxxxxx:~$ ifconfig


[LIST=1]
[*]install that package. use ssh.
[*]run "which openbox" to get the full path, use ssh.
[*]setup a custom x2go connection to the system ... put the location of the openbox binary into the custom launcher location. Youj didn't tell x2go which program to run. Fill in the "Command:" field.
[/LIST]
While performing this third step ie., "[COLOR=#000000]setup a custom x2go connection to the system ... put the location of the openbox binary into the custom launcher location. Youj didn't tell x2go which program to run. Fill in the "Command:" field." 

I am unable to fill the the command "[/COLOR]/usr/bin/openbox" in the command field of xGoClient UI in windows.

Any tips here further please?

Once again many many thanks in advance,

---

### Post by TheFu on 2023-09-15
> **appusony said:**
>  
I am unable to fill the the command "[/COLOR]/usr/bin/openbox" in the command field of xGoClient UI in windows.

I can only guess that the versions of ssh or x2go are different enough to be incompatible.  Besides ensuring that libssh is compatible ( there have been bugs ), be certain to use the PPA version of x2go client and server.  

I tested it here from 20.04 to 22.04. Worked fine with ssh-keys for authentication.
I don't usually go the opposite way, but set that up too.  22.04 --> 20.04 and it didn't work.  Looks like libssh isn't compatible, but the default server logs weren't helpful. No errors show.

```
sudo add-apt-repository ppa:x2go/stable
sudo apt install x2goserver x2goserver-xsession
```

I'm assuming that the add-apt-repository cmd automatically runs "apt update", if it doesn't, do that.

Can't test MS-Windows, sorry.  I won't risk my only Windows system by installing anything. It hasn't been touched since around 2015 before MSFT changed the EULA in a way I didn't like.  If I work it right, it will remain static for the rest of my life. ;)

---

### Post by appusony on 2023-09-15
Many thanks once again Fu,

1. Just a small doubt please, May I know, if ubuntu desktop machine that is in remote - if it is entered into sleep mode (though I am able to access via ssh thro CLI interface), still by connecting via x2go -> can we wake up this machine by waking it up by pressing any keys from windows x2go client please, or is it the remote system should be always turned on with GUI.

2. I am seeing the below:

x2go client console

NXPROXY - Version 3.5.0


Copyright (C) 2001, 2010 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.


Info: Proxy running in client mode with pid '15876'.
Session: Starting session at 'Sat Sep 16 07:57:30 2023'.
Info: Connecting to remote host 'localhost:58767'.
Info: Connection to remote proxy 'localhost:58767' established.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Warning: Failed to read data from the X auth command.
Warning: Generated a fake cookie for X authentication.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display 'localhost:1'.
Session: Session started at 'Sat Sep 16 07:57:30 2023'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Sat Sep 16 08:07:02 2023'.
Session: Session terminated at 'Sat Sep 16 08:07:02 2023'.


NXPROXY - Version 3.5.0


Copyright (C) 2001, 2010 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.


Info: Proxy running in client mode with pid '8924'.
Session: Starting session at 'Sat Sep 16 08:07:18 2023'.
Info: Connecting to remote host 'localhost:58767'.
Info: Connection to remote proxy 'localhost:58767' established.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Warning: Failed to read data from the X auth command.
Warning: Generated a fake cookie for X authentication.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: Using cache file '/cygdrive/C/Users/srishanm/X2GO~1/cache-unix-kde-depth_32/S-90C35BD58786DEFF10A14DA5696C3C05'.
Info: Forwarding X11 connections to display 'localhost:1'.
Session: Session started at 'Sat Sep 16 08:07:23 2023'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.

Many thanks in advance,

---

### Post by appusony on 2023-09-15
May I know please, I am seeing this screen shot, does it means -> connection is fine & working, any additional settings needs to checked or done on ubuntu 22.04?

---

### Post by appusony on 2023-09-16
Thanks infinity Fu!, Finally I got open-box up and running!, the below did this trick!, once again thank you so much for all my dear friends supporting this thread, Highly appreciate for all your valuable inputs & pointers & for all your valuable time. Best Wishes,

sudo add-apt-repository ppa:x2go/stable
sudo apt install x2goserver x2goserver-xsession

---

### Post by TheFu on 2023-09-16
> **appusony said:**
> May I know please, I am seeing this screen shot, does it means -> connection is fine & working, any additional settings needs to checked or done on ubuntu 22.04?

I don't allow any of my server systems to sleep, period. I don't allow HDDs to spin down, if I can stop it.  It is a hardware longevity choice for me.  Don't read more into those statements than what I've said. It means I don't know the answer to your question, but I suspect if the system is in sleep mode, then it won't work.  That's sorta the entire point of sleep mode.

I would assume if you want some sort of wake-on-sleep capability, then you'd need to set that up yourself. I know nothing useful about that, having never used WoL ... er ... ever.  I do know that it is extremely hardware, BIOS and OS dependent.

---

### Post by TheFu on 2023-09-16
> **appusony said:**
> May I know please, I am seeing this screen shot, does it means -> connection is fine & working, any additional settings needs to checked or done on ubuntu 22.04?

"need"?  No.  I usually disable file sharing, audio, and set the connectivity to be 1-less than what is actually available.  For example, if I'm connecting to a LAN system, I'll tell x2go that it is a WAN connection.  If it is a WAN connection, I set the speed to be a slower WAN than I have, like ADSL.
Also, I set the screen compression from 16mb to 4kb. I'm not doing high quality graphics. Having a snappy GUI is more important than seeing barely compressed screens.  I'm of the age who remember 20 inch monitors with 256 colors as being completely awesome.  Who could need more colors than that?   For a spreadsheet or to read email?  Not me.

The whole point of a remote desktop to me it NOT to have anything local. Leave it all remote, including files. It is a security mindset.

For accessing remote files on my local system, since we already have ssh working, I'd use sftp or sshfs. These work well when remote for emergency needs.  It would be odd for me to need access to files at home. When I travel, I'll bring entertainment files with me of sufficient number to easily fill in dead time. I've never watched more than a few movies or noticed how much music/audiobooks were heard.  The point of travel to me is NOT to be trapped in some hotel, but to be out doing things except when I'm sleeping. If I wanted to watch movies all day, I'd stay at home and send my better half on a trip instead.  She-who-must-be-obeyed only allows a certain amount of male laziness.

---

### Post by MAFoElffen on 2023-09-16
> **TheFu said:**
> I don't allow any of my server systems to sleep, period. I don't allow HDDs to spin down, if I can stop it.  It is a hardware longevity choice for me.  Don't read more into those statements than what I've said. It means I don't know the answer to your question, but I suspect if the system is in sleep mode, then it won't work.  That's sorta the entire point of sleep mode.

I would assume if you want some sort of wake-on-sleep capability, then you'd need to set that up yourself. I know nothing useful about that, having never used WoL ... er ... ever.  I do know that it is extremely hardware, BIOS and OS dependent.
On some of my servers I have a light Desktop installed as minimal-on-demand, as that is not their normal state, and the GUI unloads when I am done. The problem with most GUI's is that they load power profiles about going to sleep.

Like TheFU, I do not want my servers to ever go to sleep, nor to let the disks go to sleep. That causes some chaos on my RAIDz Arrays. To prevent that from happening, this is what I do:
```

sudo systemctl disable sleep.target suspend.target hibernate.target hybrid-sleep.target
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

```
You can reverse that, if ever needed again via
```

sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target
sudo systemctl enable sleep.target suspend.target hibernate.target hybrid-sleep.target

```
I would suggest that a VM, or machine that is there for remote login should not go to a sleep state. Or if used as a Desktop or Workstation, I used to use WOL (Wake On Lan)... But that isn't really a thing that moder hardware supports these days. I mean, I have brand new Intel NIC's that support SR-IOV, and PXE booting, but do not support WOL.

Linux still supports it, but now with SystemD, you have to have the hardware that supports, it, then you create a systemd unit file to enable it on boot.

---

