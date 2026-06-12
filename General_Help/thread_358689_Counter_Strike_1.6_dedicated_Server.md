---
title: "Counter Strike 1.6 dedicated Server"
date: 2007-02-11
forum: General Help
---

### Post by ashmew2 on 2007-02-11
HI every1 
I have been trying to get a CS 1.6 server up and running (without steam) , so ive followed all the instructions from here :[The CS Website]("http://www.cstrike.ro/tutorial_cs16_nosteam_linux.php")

Ive followed all the steps but when from terminal i try to start the server :
```

ashish@ashish-desktop:~/hlds$ ./hlds_run -game cstrike  +ip XX.XXX.XXX.XX(this is my IP , determined from www.whatismyip.org) +sv_lan 0 -nomaster +maxplayers 18 +map de_dust2 -console

```
It says : 
```

Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash

Console initialized.
scandir failed:/home/ashish/hlds/./platform/SAVE
Protocol version 47
Exe version 1.1.2.5/Stdio (cstrike)
Exe build: 02:38:31 Jul  7 2004 (2738)
STEAM Auth Server
couldn't exec language.cfg
WARNING: UDP_OpenSocket: port: 27015  bind: Cannot assign requested address
FATAL ERROR (shutting down): Couldn't allocate dedicated server IP port 27015.
Add "-debug" to the ./hlds_run command line to generate a debug.log to help with solving this problem
Sun Feb 11 17:05:51 IST 2007: Server restart in 10 seconds
Sun Feb 11 17:05:54 IST 2007: Server Quit

```
Now what shud i do ? Thanks.
btw , im not on a LAN and i want a server which every1 can join :D

---

### Post by davidvasta on 2007-02-11
I found this link when I googled your networking errors. I could just read it and post my thoughts but figured I would link you to the post @ CS

[LINK TO CS FORUM]("http://server.counter-strike.net/forums/showthread.php?t=27951")

---

### Post by davidvasta on 2007-02-11
If you need a short explanation of IP and Ports let me know. I can explain that if needed.

---

### Post by ashmew2 on 2007-02-12
Thanks for the response man but one more thing...i dont know how to open ports and i have a dynamic IP.Would be gr8 if you could tell me! :D 
Thanks

---

### Post by reclusivemonkey on 2007-02-13
Are you behind a router? If so, you need to put in the internal IP address into the start line, not the external IP.

---

### Post by ashmew2 on 2007-02-13
> **reclusivemonkey said:**
> Are you behind a router? If so, you need to put in the internal IP address into the start line, not the external IP.

Even if i put an internal IP , how will the others join te server ? I think my internal IP is 127.0.0.1 but that wont be the IP to give to players...ne ideas?

---

### Post by reclusivemonkey on 2007-02-13
> **ashmew2 said:**
> Even if i put an internal IP , how will the others join te server ? I think my internal IP is 127.0.0.1 but that wont be the IP to give to players...ne ideas?

Nope. You need to set up a fixed internal IP address along the lines of 192.168.1.10, definitely in the range 192.168. Your router will translate the internal IP address when it connects. I ran a home CS server for several years, and if you do have a router, this is definitely the way you should do it.

---

### Post by reclusivemonkey on 2007-02-13
You can use this site to check whether your server is available to people outside your LAN;

[http://www.serverspy.net/site/search/](http://www.serverspy.net/site/search/)

---

### Post by ashmew2 on 2007-02-13
BUt i have like no idea on how to go about it ? any pointers plz ?

---

### Post by ashmew2 on 2007-02-14
Thanks for all your help guys , its finally working. I just switched my Beetel 220 BX modem from routing to Bridge Mode and it works :D
Thanks

---

### Post by rzsolt2 on 2008-06-05
Hi! I would like to set up a dedicated CS 1.6 server with Ubuntu Server edition on an older machine. 

The config of the machine is:
CPU: 466 MHz Intel Celeron
RAM: 256 MB SDRAM
VGA: 1 MB
HDD: WD, 4.3 GB
NET: 2Mbit/512 kbit

What do you think is there any chance to run that server on this machine with at least 6 slots? Or there is no hope?

---

### Post by reclusivemonkey on 2008-06-05
I used to run a server with pretty much the same spec; you should be ok with six slots although ita few years since I ran this. I had to restart the server daily due to the memory leaks in SRCDS, so any more memory you can muster will help. Some maps will certainly run better than others so think about that for your map list.

---

### Post by rzsolt2 on 2008-06-06
What maps do you mean? Default maps? dust, assault, etc. or new small maps? What consumes more memory?

---

### Post by ashmew2 on 2008-06-08
In my opinion , u should be just fine . In my town , we used to host 12 slot servers with much slower network speeds like 256 kbps.

---

### Post by Gjoko on 2008-07-10
I have dug up a Pentium 3 machine and i instaled ubuntu server edition in hopes of making a small CS 1.6 server. I've found several sites explaining how to install it but i have a few issues. I'm relativly new to linux and not used to only text commands.
1st It says that i need to open server.cfg and replace all the text there with the ones given on the sites. Is it posible to open it and type in it ?
2nd There are several files that need copying even unziping i think how do i do this i know there are some copy commands
And also is this machine capable of runing a 2vs2 game ? The procesor is 900mhz and 64mb ram i think 20g disk. 
Would apriciate any sugestions and other install methods also does anyone know practical uses with the aps coming with the server edition?
Oh and will instaling ubuntu make my life easier will it be a big performance hit?

---

### Post by ashmew2 on 2008-07-11
How about Downloading the server , editing all files on a machine with which u r familiar , and then transfer the server files to your Pentium III machine with a pen drive or CD Rom ?

---

### Post by Gjoko on 2008-07-11
that may work but can anyone tell me the copying commmands?

---

### Post by ashmew2 on 2008-07-11
Since you are very new to Linux , This site might help you with the basics :

[http://www.psychocats.net/ubuntu/flashpre804](http://www.psychocats.net/ubuntu/flashpre804)

The copy command is cp
For example i have a file file.txt in /home/me and i want to move it to /home/lala , I would type in the terminal :

```
cp /home/me/file.txt /home/lala
```

If you could point me to the site which u r referring for setting up the server , i might be able to help further.. Let me know if u need nethin else ;)

---

### Post by Gjoko on 2008-07-11
The site i'm using is [http://www.cstrike-planet.com/tutorial/1/6](http://www.cstrike-planet.com/tutorial/1/6). About the copying do u think creating the server before copying on a 64bit linux will be a problem? Oh and is there a way for the server to autostart with certain parameters when the pc is turned on? Sorry for all of the questions and thank you for your patience

---

### Post by ashmew2 on 2008-07-12
You could create the server on a different machine and copy it to your Ubuntu server but since you have all the facilities on your Pentium III machine , why not set it up on that ?

As far as the information on the site is , I think it should work without a problem and if you are concerned or worried about seeing the commands in case you forget or something , you can open the site in your Ubuntu Server (Yes i know its command line) by using elinks or any other similar software.

Just install elinks , do in the console (on your Ubuntu Server) :
```

sudo apt-get install elinks
```

After the download completes , press CTRL+ALT+F2 and type in there :
```

elinks www.cstrike-planet.com/tutorial/1/6
```

The site will open up , you can see the commands here and to go back to your first terminal , press CTRL+ALT+F1 .

Yes , your server can be started with certain parameters when the pc is turned on .
 If you meant the Counter Strike server , you have to edit the server.cfg file for the server configuration. 
If you meant the UBUNTU server , ill get back to you after your post.

---

### Post by Gjoko on 2008-07-14
Well reading it and copying all the commands is not a problem i SSH   into it now but i don't know how to copy files with SSH. For the .cfg files i thought about editing and copying the files from the dedicated server that installs with CS 1.6

---

