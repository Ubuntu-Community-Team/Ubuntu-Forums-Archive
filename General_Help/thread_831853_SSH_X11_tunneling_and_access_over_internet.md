---
title: "SSH X11 tunneling and access over internet"
date: 2008-06-17
forum: General Help
---

### Post by patrickaupperle on 2008-06-17
Ok, I install ssh and now have sshd running. I can access it through putty, winscp, and ssh 127.1.1.100. The first problem is that I can not get any x11 apps to tunnel through. This is supposed to be supported, afaik. The other problem I am having is that I can only ssh in to my laptop from another computer on the same network. Afaik, I am supposed to be able to access it over the internet from anywhere world wide.  Can anyone help?

---

### Post by angelmartinezn on 2008-06-17
ssh -X user@machine

once inside if you run any app (like gedit) it will be opened remotely


Other system you can use is freenx.

---

### Post by bingoUV on 2008-06-17
What do you mean when you say **I can not get any x11 apps to tunnel through** ? 

1. What command did you use to try to achieve this?
2. Any errors?
3. Window simply does not show up at the intended location?
4. Have you verified the xhost settings at the server and DISPLAY variable at the client? ssh should take care of it but still verify if it is fine.


You say **I can only ssh in to my laptop from another computer on the same network** . 
1. Are you sure the system is visible outside your own network? 
2. Can you ping it from outside the network? 
3. telnet at port 22 ? 
4. ftp?

---

### Post by patrickaupperle on 2008-06-17
> **bingoUV said:**
> What do you mean when you say **I can not get any x11 apps to tunnel through** ? 

1. What command did you use to try to achieve this?
2. Any errors?
3. Window simply does not show up at the intended location?
4. Have you verified the xhost settings at the server and DISPLAY variable at the client? ssh should take care of it but still verify if it is fine.
I forgot to mention That I did do ssh -X 127.1.1.100. Then I just typed "gedit" 
```
X11 connection rejected because of wrong authentication.
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

```
4. No, and I don't know how.
[QUOTE=bingoUV;5203285You say **I can only ssh in to my laptop from another computer on the same network** . 
1. Are you sure the system is visible outside your own network? 
2. Can you ping it from outside the network? 
3. telnet at port 22 ? 
4. ftp?[/QUOTE]
1. No, how would this be accomplished?
2. have not tried
3. ssh over port 22
4. No, I do not have ftp

---

### Post by eldragon on 2008-06-17
hmm, ive had this one before.
backup
.ICEauthority
and delete it. should be in your home.

i dont remember if it was that file or 
.Xauthority


do the same with both :)

BACKUP and then DELETE the file.

---

### Post by patrickaupperle on 2008-06-17
> **eldragon said:**
> hmm, ive had this one before.
backup
.ICEauthority
and delete it. should be in your home.

i dont remember if it was that file or 
.Xauthority


do the same with both :)

BACKUP and then DELETE the file.

That worked. Sort of. Now when I ssh in via ssh -X 127.1.1.100, I can tunnel apps.:guitar: I still can't tunnel them through putty, though:(.

---

### Post by eldragon on 2008-06-17
> **patrickaupperle said:**
> That worked. Sort of. Now when I ssh in via ssh -X 127.1.1.100, I can tunnel apps.:guitar: I still can't tunnel them through putty, though:(.


you can actually tunnel through putty, but if you use putty, i asume you are doing this through a windows client.

you need to have the X11 environment installed in that windows client in order to work. remember the windows are being drawin locally, its just that all stuff is being done at the xorg server ;)

i never done this before, i even found X11 forwarding through the internet slow and useless. but if you get it working, post a nice howto :D

edit
and you could try -X -C which is supposed to compress data before sending it...

---

### Post by bingoUV on 2008-06-17
1. The system administrator should be able to tell you whether the machine is supposed to be visible from outside the network. If you are the system administrator, ask your network service provider.

2. To test whether the machine is visible from outside the network, do this from a machine outside the network : 
```

ping <the name of your server>

```

If it does not reply, or says timed out, the machine is not visible. The system administrator or the network service provider can help you.

3. If the above ping replies properly, try
```

telnet <the name of your server>

```

If it connects and gives you a > prompt, port 22 is accepting connections.

4. forget about ftp for now.

---

### Post by patrickaupperle on 2008-06-17
> **bingoUV said:**
> 1. The system administrator should be able to tell you whether the machine is supposed to be visible from outside the network. If you are the system administrator, ask your network service provider.

2. To test whether the machine is visible from outside the network, do this from a machine outside the network : 
```

ping <the name of your server>

```

If it does not reply, or says timed out, the machine is not visible. The system administrator or the network service provider can help you.

3. If the above ping replies properly, try
```

telnet <the name of your server>

```

If it connects and gives you a > prompt, port 22 is accepting connections.

4. forget about ftp for now.

Unfortunately, I do not have an machine outside the network to test this with. Last I checked, the ping did not reply properly. Is there a way to make yourself visible?

---

### Post by bingoUV on 2008-06-17
Ask the network service provider for making you visible. Even after that, you need to test it with an outside machine to confirm that it is working and some local / router / firewall setting is not preventing outside access to the service.

---

### Post by patrickaupperle on 2008-06-17
> **bingoUV said:**
> Ask the network service provider for making you visible. Even after that, you need to test it with an outside machine to confirm that it is working and some local / router / firewall setting is not preventing outside access to the service.

That's a job for another day.:) Also one more thing, Are you saying that I can not tunnel my x11 apps through putty onto a windows computer?

---

### Post by bingoUV on 2008-06-17
If the machine is not visible from the windows computer, of course you cannot tunnel x11 apps.

Otherwise I have no experience on windows, putty and x11.

---

### Post by eldragon on 2008-06-17
> **patrickaupperle said:**
> That's a job for another day.:) Also one more thing, Are you saying that I can not tunnel my x11 apps through putty onto a windows computer?

you are missing the concept of tunneling. and how X works

with X11, there is a client and a server involved.

if you wish to tunnel X11 to a windows machine, the windows machine needs a client that will talk to that server.

under a linux client to a linux server, this is no problem, because you have the client installed.

under windows. you will need to install the X11 environment (the client), in order to work, anyway, i never done that, and wouldnt know where to start. id rather stick with vnc.

---

### Post by patrickaupperle on 2008-06-20
> **eldragon said:**
> you are missing the concept of tunneling. and how X works

with X11, there is a client and a server involved.

if you wish to tunnel X11 to a windows machine, the windows machine needs a client that will talk to that server.

under a linux client to a linux server, this is no problem, because you have the client installed.

under windows. you will need to install the X11 environment (the client), in order to work, anyway, i never done that, and wouldnt know where to start. id rather stick with vnc.

Thank you. Sorry I am a noob. I know I am not as knowledgeable as many of you all. Thank you for the time you took to clear this up. I was asking because putty does have a tunnel option, but it would not work. Also, can VNC work if I am not visible on the internet?

---

### Post by eldragon on 2008-06-20
> **patrickaupperle said:**
> Thank you. Sorry I am a noob. I know I am not as knowledgeable as many of you all. Thank you for the time you took to clear this up. I was asking because putty does have a tunnel option, but it would not work. Also, can VNC work if I am not visible on the internet?
No problem, knowing is not knowledge, knowing where and who to ask is :D


if you can ssh into the computer then anything can work. Remember tunneling works for anyport.
so you could run putty tunneling the vnc port and then attempt to vnc locally.

for instance:
1. make sure you have a vnc server up and running on the ubuntu server machine.
2. make sure you have a ssh server up and running on the ubuntu server machine.
3. make sure port 22 is open and you have a strong password <-- that is important.
4. install fail2ban (apt-get install fail2ban) to protect yourself from bruteforce attacks at the ssh server.
5. download a vncclient for windows ([www.realvnc.com](www.realvnc.com) is a good place to look for)
6. run putty with the following command:
```

putty -L 5900:localhost:5900 username@server

```
remember to replace username with the username you use to connect to your linux machine and server with your server-ip.

this will send any connection to the 5900 port at your windows machine to the server at its 5900 port through the ssh connection.

7. use the vnc client to connect to localhost at the windows machine.


good luck

---

### Post by patrickaupperle on 2008-06-21
> **eldragon said:**
> No problem, knowing is not knowledge, knowing where and who to ask is :D


if you can ssh into the computer then anything can work. Remember tunneling works for anyport.
so you could run putty tunneling the vnc port and then attempt to vnc locally.

for instance:
1. make sure you have a vnc server up and running on the ubuntu server machine.
2. make sure you have a ssh server up and running on the ubuntu server machine.
3. make sure port 22 is open and you have a strong password <-- that is important.
4. install fail2ban (apt-get install fail2ban) to protect yourself from bruteforce attacks at the ssh server.
5. download a vncclient for windows ([www.realvnc.com](www.realvnc.com) is a good place to look for)
6. run putty with the following command:
```

putty -L 5900:localhost:5900 username@server

```
remember to replace username with the username you use to connect to your linux machine and server with your server-ip.

this will send any connection to the 5900 port at your windows machine to the server at its 5900 port through the ssh connection.

7. use the vnc client to connect to localhost at the windows machine.


good luck

Thank you once again.:KS I will have to try this. Eventually.

---

