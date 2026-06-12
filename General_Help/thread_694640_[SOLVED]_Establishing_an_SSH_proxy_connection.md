---
title: "[SOLVED] Establishing an SSH proxy connection"
date: 2008-02-12
forum: General Help
---

### Post by Zeroangel on 2008-02-12
Hey all. I'm working on a little project, and the goal of this project is to be able to tunnel into my home PC and also use it as a secure proxy server.

This guide was very helpful for the basic stuff:
[http://ww.buzzsurf.com/surfatwork/](http://ww.buzzsurf.com/surfatwork/)

And I had to adapt the guide to fit in with Ubuntu (read my next post to find out the modifications I made) because the instructions for making an SSH server is for the Windows version of OpenSSH.

Success! I can SSH into my Ubuntu computer using my username/password for my user accounts on that machine. But! I find that I am unable to use it as a proxy because Firefox gives me the error that the SOCKS server is refusing connections.

Which is too bad, since I do enjoy the security aspect of SSH particularly when using wireless hotspots and such.

My question here is **How do I get my home Ubuntu computer to allow proxy connections through SOCKS?**

---

### Post by Zeroangel on 2008-02-12
OK, so the above guide contained instructions for setting up SSH server using OpenSSH for windows. Well, for Ubuntu its a little different, but just as simple.

First of all I installed OpenSSH for linux
```
sudo apt-get install openssh-server
```Then I edited /etc/ssh/sshd_config file to change the port to **443** which is the HTTPS port. In effect, my connection now looks like a HTTPS connection to a normal webserver.

Then I restarted the SSH server using
```
sudo /etc/init.d/ssh restart
```For those of us who have a dynamic IP, its tricky since our IP changes. Following that guide's recommendation I set up a user account at no-ip.com and installed the no-ip daemon for Ubuntu.
```
sudo apt-get install no-ip
```On my Windows machine. I then downloaded putty.exe and wrote a windows batch script called shunnel.bat
```
@ECHO OFF
ECHO. Establishing SSH Connection on Ubuntu (Dave)
start putty -D 8080 -P 443 -ssh Guest@myserver.no-ip.com
```When I run the script, it establishes connection using the username "Guest" (which I have set up on my machine) and asks for my password.

   Login! I can even access all of my commands and folders as if I were right there at the terminal. As a test, I navigated to my music folder and ran the command "play whatever.mp3"And the song started to play on my Ubuntu PC. Success! 

Now it is just the matter of finding a way to enable my computer to act as a SOCKS proxy.

P.S.: On the Windows script replace the "Guest" with the name of one of the user accounts on your Ubuntu PC, and replace the phrase "myserver.no-ip.com" with your IP address or your no-ip.com account URL. Your password will be the same as your user account's password in ubuntu.

---

### Post by Zeroangel on 2008-02-12
Found the problem!

It turns out that I set myserver.no-ip.com -- port 8080 as the SOCKS proxy -- when I shouldve used 127.0.0.1 -- port 8080 as the SOCKS proxy.

WHOOPS! :KS

Anyways, I've installed and configured FoxyProxy to auto-use the proxy server, so now all I have to do is:
1) Run my script
2) Enter my password and then minimize the putty window
3) Use Firefox

Secure, unrestricted browsing FTW!

---

### Post by Zeroangel on 2008-02-12
OK, another conundrum here. 

This time I want to establish a VNC connection through SSH, and I want it to look like encrypted HTTPS traffic again.

I have created the following script (called securevnc.bat):
```
CLS
@ECHO OFF
ECHO. Establishing SSH connection to Ubuntu (Dave) 
start putty -D 5900 -P 443 -ssh Guest@myserver.no-ip.com
ping -n 1 127.0.0.1 >NUL
ECHO. Success.
ping -n 2 127.0.0.1 >NUL
ECHO. 
ECHO. Enter your password to log into Ubuntu before continuing
PAUSE
ECHO. Launching VNC Viewer
start vncviewer 127.0.0.1:5900
ping -n 2 127.0.0.1 >NUL
EXIT
```What this ATTEMPTS to do is:
1) Launch an SSH session on port 443
2) Wait for user input (login using password)
3) Launch TightVNCViewer

(the PING and ECHO lines are for presentation only, when the script is run)

Problem is -- I can't get anywhere. The VNC message window comes up saying "Establishing Connection" -- and it just stays there.

Can anyone enlighten me to why this is? And what I can do to fix it?

---

### Post by Spitphire on 2008-02-12
I would connect to localhost:50000 and have putty forward it to your no-ip.com:5900...

here's everything you need and more: (this way is alot more secure..)

[VNC and SSH guide]("http://ubuntuforums.org/showthread.php?t=383053")

---

