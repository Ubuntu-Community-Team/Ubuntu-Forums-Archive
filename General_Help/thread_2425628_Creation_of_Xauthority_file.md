---
title: "Creation of Xauthority file"
date: 2019-08-28
forum: General Help
---

### Post by sharkwsk on 2019-08-28
I have been viewing thread [https://ubuntuforums.org/showthread.php?t=1863978](https://ubuntuforums.org/showthread.php?t=1863978) to see if I can apply the fix as I might have done the same - messing up the xauthority file :(

Unfortunately below command does not work

[COLOR=#ff0000]test@server1:~$ ll .Xauthority [/COLOR]
[COLOR=#ff0000]-rw-rw-r-- 1 test test 0 Aug 28 16:04 .Xauthority[/COLOR]
[COLOR=#ff0000]test@server1:~$ [/COLOR]
[COLOR=#ff0000]test@server1:~$ [/COLOR]
[COLOR=#ff0000]test@server1:~$ [/COLOR]
[COLOR=#ff0000]test@server1:~$ sudo xauth generate :0 . trusted[/COLOR]
[COLOR=#ff0000]xauth: (argv):1:  unable to open display ":0".[/COLOR]
[COLOR=#ff0000]test@server1:~$ [/COLOR]

Ubuntu version: 18.04
When I login, I cannot see DISPLAY environment variable set

---

### Post by TheFu on 2019-08-28
To see any environment variable, there are multiple ways. Two are:
```
echo $DISPLAY
env|grep DISPL
```

You can just delete the ~/.Xauthority  file, logout and log back in. It will be recreated.
```
rm ~/.Xauthority
```

Simple.

This assumes there is an X/Server on the machine.  If there isn't any X11, then there isn't any reason for the DISPLAY or the .Xauthority file to exist.

---

### Post by sharkwsk on 2019-08-28
Output of the commands show no env value

test@server1:~$ echo $DISPLAY


test@server1:~$ 

I also removed the .Xauthority file in my home directory and logged in again, file was not recreated

test@server1:~$ pwd
/home/test
test@server1:~$ 
test@server1:~$ 
test@server1:~$ ll .X*
ls: cannot access '.X*': No such file or directory
test@server1:~$

---

### Post by TheFu on 2019-08-28
Are you running X11?

---

### Post by sharkwsk on 2019-08-29
1. I have started Xming in windows
2. SSH has remote X11 forwarding enabled
3. After login, still no  Xauthority file

---

### Post by TheFu on 2019-08-29
Way to bury the lead!   Please, please, please always mention that you are trying to use Windows.

The .Xauthority file is on the X/Server.  Windows/Xming is the Xserver, not the remote system.  I haven't touched Xming for more than a month since around 2000. Sorry.

In general, the Xserver runs on the machine you sit behind.  The Xclient is the remote system program, which uses X11 protocol to ship commands to the Xserver for display and actions.  On a Linux desktop, ssh -X will automatically setup the DISPLAY and ssh tunnel for remote X11 between the remote Xclients and local Xserver.  I have no idea how to do that on Windows.

---

### Post by sharkwsk on 2019-08-29
I might have confused you even more. let me explain

1. My client PC is a windows 10 based PC, I have putty & xming
2. My server is the Ubuntu 18.04 machine
3. I have SSH session towards the server from my PC using putty with X11 forwarding enabled and display location set to "localhost:0.0"
4. Prior to SSH'ng, I open xming in the background in my PC
5. After I SSH as non-root user, I print the environment variable using command "export $DISPLAY" and I can see that it is not set. Is this normal ?

I have following set in my ubuntu server SSHD configuration
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes

Thank you for your help

---

### Post by Skaperen on 2019-08-29
putty is the issue.  it is not seeing any place to forward the X11 connections to and so it is not requesting the remote server to set up the remote side of things.  if you were running Ubuntu as your desktop, the ssh client would see where to forward to by looking at the DISPLAY environment variable.  i don't know any of the needed pieces of knowledge needed to tell putty how to forward to the Xming on Windows.  i last used Windows 95 and it was totally isolated from any network dogbert style.

---

### Post by TheFu on 2019-08-29
You'll have to manually set the correct DISPLAY each time you connect.  There are easier ways ... like running a tiny Linux virtual machine on Windows and using ssh -X to connect to the remote system to run Xclient applications.  Then you'll have a real Xserver, normal ssh client that have worked together for decades.

Way back when I did use Windows as my desktop, I tried to do what you are doing.  With commercial X/server software ($200), it wasn't too bad and worked well.  Xming was the free option back then and while it worked, the Xserver would crash a few times a day.  After a few weeks of frustration, I installed a small Linux desktop into a virtual machine and never looked back.

ssh and remote X just work so much easier between Unix systems.

You can definitely have the remote system DISPLAY work outside the ssh-tunnel using the X/Windows client/server methods, just without any encryption.

On the Windows machine, go into the xming settings and set up an [B]xhost +{ip of the remote server}
[/B]On the remote server, use the **who am i** command+options to get the IP for your desktop (X/server), then set 
```
export DISPLAY={that IP addres}:0
```
or example:
```
export DISPLAY=192.168.1.43:0
```
and you can run an **xterm -sb**  and it will show up on your desktop in a few seconds. From that terminal, you can launch most other GUI programs, unless they demand direct access to the GPU.  Don't expect any audio or video playback to work and nothing with opengl requirements will work either.

Don't use the X/Windows method on a non-secure LAN.

The actual DISPLAY env has some specific rules for which monitor and which X/server it will use based on the :0.0 parts.  In theory, you could have that set to be :3.1 on a a system with 4 GPUs and at least 2 monitors for the 4th GPU.

---

### Post by sharkwsk on 2019-08-29
I managed to get this fixed and this is what I did

1. Created Xauthority file using below commands (second command does not work)
**touch ~/.Xauthority**
**xauth generate :0 . trusted **
**xauth add ${HOST}:0 . $(xxd -l 16 -p /dev/urandom)**
[B]xauth list 

[/B]2. Set this attribute in SSHD config and restart SSHD
X11UseLocalhost no

3. After this, when I login to the server, I can see DISPLAY env set properly and I am able to open remote Xapps

---

### Post by TheFu on 2019-08-30
Glad you got it working.

Looks like that takes the place of the xhost + command I provided.
In 25+ yrs using X/Windows, 5 as an X-applications programmer, I've never used the xauth command directly.

---

