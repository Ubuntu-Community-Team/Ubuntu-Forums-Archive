---
title: "x11vnc can't change port"
date: 2014-08-14
forum: General Help
---

### Post by cmcanulty on 2014-08-14
I have set up several port forwardings in my router so vnc goes to a specific computer. It works with win 7 but when I
```
sudo x11vnc -rfbport 5916 
``` all that happens is I can't connect but I can still connect through 5900 the problem is then I have to go through another program to get a specific computer as all the xubuntus won't actually change to any number but 5900 unless the above command is incorrect or not permanent I don't know what I am doing wrong.

---

### Post by steeldriver on 2014-08-14
Why are you running x11vnc using sudo? it should normally be run by the owner of the remote session to which you are trying to connect

Fundamentally, I don't see why you need to have different VNC **server **ports for your remote computers - from the client side, you distinguish the connections by hostname (or IP)? Even if you are tunneling over SSH you can configure your tunnel(s) to tunnel each to a different local port.

---

### Post by cmcanulty on 2014-08-14
I ran the port command with sudo because I read that I should. I can easily vnc direct into the windows 7 machines by setting a specific port in router and in vnc when I try to change the port using the previous post to one for xubuntu it does nothing and port stays at 5900. I need to directly connect for support to 10 xubuntu desktops using x11vnc and simply need to set the port to what I need ex 5918 or whatever

---

### Post by steeldriver on 2014-08-14
I'm not aware that running 'sudo x11vnc -rfbport 59xx' will change the port of an already running instance - as far as I know, it will start a new instance (as root) on port 59xx (display :xx)

As I mentioned previously, you should only need to use different VNC server ports if you want to run multiple remote desktop sessions on the same host. That's not typically something you'd do with a desktop sharing style of VNC anyway, since it would require a real X server to be running on the indicated display. It should be perfectly possible (and easier - from a management and maintenance point of view) to run all the remote machine's x11vnc sessions on the default port (5900, corresponding to their real X server on :0.0) and choose which one to connect to at the client end using its hostname (if you have DNS/mDNS) or IP address.

Remember this has nothing to do with the outbound port(s) that your client is using to connect **to** the server(s)

---

### Post by cmcanulty on 2014-08-14
could you please explain how to do that on the win 7 ones I open a port like 5906 for vnc and then can directly go to that computer by ip:port all the machines I need to add are xubuntu and I need x11vnc to see the actual desktops as they are being used to help people.Are you saying linux won't let me port to an individual computer by port forwarding?

---

### Post by steeldriver on 2014-08-14
What VNC client are you using on the Windows side? I am somewhat familiar with the TightVNC client and to a lesser extent with UltraVNC. 

Are you tunneling the VNC connections via SSH or using raw VNC?

---

### Post by cmcanulty on 2014-08-15
I am connecting OK from my xubuntu to win 7 but not from xubuntu to xubuntu I need to permanently set and forward a different port for each of 10 x11vnc servers

---

### Post by steeldriver on 2014-08-15
If you are connecting from within the same LAN (i.e. you can access the individual IP addresses / hostnames of the remote hosts), it should be sufficient to point your VNC client at (say) *host1*:5900, *host2*:5900, etc.  In fact, if you use the default 5900 port, you probably don't even need to specify the port explicitly. For example, if I start

```

x11vnc -o $HOME/.vnc/x11vnc.log -rfbauth $HOME/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb

```

on my laptop (LAN IP 192.168.1.16) and then start an identical

```

x11vnc -o $HOME/.vnc/x11vnc.log -rfbauth $HOME/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb

```

on my HTPC (LAN IP 192.168.1.65), then all I need to do on the Windows box is fire up TightVNC viewer and enter '192.168.1.16' in the **Remote Host:** box, then select **New connection...** and enter 192.168.1.65 - voila - two remote desktops, two different (arbitrary) client ports on the Windows side, ***same (5900) VNC port on both servers***.

If you are doing this from a remote location via a single public IP without tunneling ([COLOR=#ff0000]**you should NOT be doing this**[/COLOR] - but it may help you understand the next part), then it should just be a matter of setting the **port forwarding on the router of the remote location** i.e.

[LIST]
[*]forward port 5900 to remote LAN IP #0, port 5900 
[*]forward port 5901 to remote LAN IP #1, port 5900 
[*]forward port 5902 to remote LAN IP #2, port 5900 
[*]etc. 
[/LIST]

and then from your Windows box, specify the public IP and forwarded port number i.e.

[LIST]
[*]123.45.67.8:5900 --> remote desktop #0 
[*]123.45.67.8:5901 --> remote desktop #1 
[*]123.45.67.8:5902 --> remote desktop #2 
[*]etc. 
[/LIST]

In neither should it be necessary to mess with the actual listening port of any of the x11vnc services on the target machines.

OTOH f you are doing it from a remote location with **SSH tunneling**,  the process is similar except that you would forward the SSH ports, e.g. (the '22000' port number is more or less arbitrary - you can choose any suitably high numbered port)

[LIST]
[*]forward port 22000 to remote LAN IP #0, port 22 
[*]forward port 22001 to remote LAN IP #1, port 22 
[*]forward port 22002 to remote LAN IP #2, port 22 
[*]etc. 
[/LIST]

and then point your SSH client (which may be built into the VNC client) to
  
[LIST]
[*]123.45.67.8:22000 --> remote desktop #0 
[*]123.45.67.8:22001 --> remote desktop #1 
[*]123.45.67.8:22002 --> remote desktop #2 
[*]etc. 
[/LIST]

with tunnels configured respectively as 

[LIST]
[*]L5900:localhost:5900 for remote host #0 
[*]L5901:localhost:5900 for remote host #1 
[*]and so on 
[/LIST]

then point the VNC client to localhost:590x to bring up the xth desktop. (Yes the 'localhost' thing is confusing: in the tunnel setup it refers to the *remote* host, because that's where the tunnel command is being run).

Hope this helps.

---

### Post by cmcanulty on 2014-08-15
It is going to take me a while to digest that. This all is to reach a system over WAN and forward a port to each xubuntu machine behind the WAN router from my home over a WAN . The easiest way to set up for me is to direct each local ip from mywanip:port and set the xubuntu forwarding ports for each machine in the wanip. Is it impossible to set an alternate port in the remote machines for x11vnc? I am running xubuntu at home and need to reach 10 xubuntus behind the wan router. I can easily set alternate ports and forward them in the router and reach the win 7 machines. If I can just set a permanent different x11vnc port from 5900 for each xubuntu machine behind router I think I would be all set.Thank you

---

### Post by steeldriver on 2014-08-15
Sure it is

```

x11vnc -o $HOME/.vnc/x11vnc.log -rfbauth $HOME/.vnc/passwd **-rfbport 5910** -shared -forever -nowf -norc -notruecolor -bg -xkb

```

and (if you are **not **using SSH tunneling - you should be) make sure the corresponding firewall port is open

```

sudo ufw allow from 192.168.1.0/24 to any port 5910 proto tcp

```

where 192.168.1.0/24 is your LAN IP range (or - if you **only **need to connect from outside the LAN, replace it by your gateway IP specifically e.g. 192.168.1.0)

But it really doesn't make things easier - you still need to do everything else that I listed, but now need to maintain DIFFERENT x11vnc and ufw configurations on each remote host, instead of doing it all at the router and client.

---

### Post by Cool_Javelin on 2014-08-22
Hi, I would also like to do the same thing, change the x11vnc listening port.

My reason is:
I am running a headless server on 12.04.2LTS, don't have x installed, and have automatic logins on some different TTY ports (specifically, TTY2, TTY3, & TTY4.) On each of these TTYn ports, I run a different program to maintain my home automation system.

I would like to also automatically login to more TTY ports (say TTY 5-7) and start a vnc server on a different port for each, so I might have access to each of those TTYn from a windows machine simply by specifying a different port number.

Obviously, I cannot change the IP number because they are all on the same machine, and I do not wish to alter my router.

I have tried

sudo linuxvnc 2 -rbfport 5902
sudo linuxvnc 2 -autoport 5902
sudo linuxvnc 2 -redirect 5902

It always starts up saying it is listening on port 5900.

Any more help?
Mark.

---

### Post by cmcanulty on 2014-08-22
I finally got it all working . I did it by setting my router to forward the port number I wanted to use for examp;e 3394  or 5914 to the standard 3389 (rdp)  or 5900 (vnc) for each computer. I had previously set static internal ips for all the machines. On the windows I used tightvnc  which easily lets you change the port number. It seems really crazy that xrdp and x11vnc won't let you set a port. tightvncserver has a ubuntu version but it has so many menus and options I could never understand it and it didn't ever seem to save settings even though I told it to. They do claim to let you change ports but every time I did it only made no connection work.

---

### Post by steeldriver on 2014-08-22
@cmcanulty I'm glad you've got your setup working and pleased you decided to leave the actual x11vnc server ports at the default 5900 and distinguish them by forwarding rules on the router - however I strongly advise you to go through the process one more time, this time forwarding SSH ports and then tunneling your VNC connections over SSH.

VNC is not secure - best case your remote workstations will collapse under the weight of attacks, worst case your whole network will get compromised

FWIW I don't understand what the difficulty is in setting the port, the following shows x11vnc successfully started on port **5901**

```

steeldriver@lap-t61p:~/Desktop$ ps -ef | grep [x]11
1002     31827     1  0 18:17 ?        00:00:00 /usr/bin/x11vnc -localhost -o /home/steeldriver/.vnc/x11vnc.log -rfbauth /home/steeldriver/.vnc/passwd **-rfbport 5901** -shared -forever -nowf -norc -notruecolor -bg -xkb
steeldriver@lap-t61p:~/Desktop$ 
steeldriver@lap-t61p:~/Desktop$ sudo netstat -nltp | grep [x]11
[sudo] password for steeldriver: 
tcp        0      0 127.0.0.1:**5901**          0.0.0.0:*               LISTEN      31827/**x11vnc**    
tcp6       0      0 ::1:**5901**                :::*                    LISTEN      31827/**x11vnc**    

```

---

### Post by cmcanulty on 2014-08-22
Steeldriver thanks for your help and a question. x11vnc says "It has built-in SSL/TLS encryption and 2048 bit RSA authentication" is it still insecure? I would like to try the ssh tunnel but am afraid of losing all the working 
setup I have.

---

