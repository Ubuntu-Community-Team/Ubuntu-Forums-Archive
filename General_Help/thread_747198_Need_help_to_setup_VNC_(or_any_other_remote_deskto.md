---
title: "Need help to setup VNC (or any other remote desktop)"
date: 2008-04-06
forum: General Help
---

### Post by Vegar on 2008-04-06
Hey guys, this is my first post on this foum ^^ I've been reading alot for a long time, but now i need help with something i didnt find anywere.

Well, what i wanna do is:
I want to see my Ubuntu desktop on a Windows PC, Ive tried vnc and it took me a while to make it work.. but, looks like it didnt work as i thought (and hoped)
this is how it ended: [http://img148.imageshack.us/img148/4681/04062008174625fe8.png](http://img148.imageshack.us/img148/4681/04062008174625fe8.png)
 
I hope you see what i mean, and that some of you know how to get this working. I've seen that the average forum user here is extremle smart! ;)
Thanks in advance.

---

### Post by Vegar on 2008-04-06
bump

---

### Post by ghost_ryder35 on 2008-04-06
Using tightvnc?  are you logged in with the screen locked when remote desktoping in?  do you have Compiz running on the Ubuntu machine?

---

### Post by Vegar on 2008-04-06
> **ghost_ryder35 said:**
> Using tightvnc?  are you logged in with the screen locked when remote desktoping in?  do you have Compiz running on the Ubuntu machine?

Im using vnc enterprice from [www.realvnc.com](www.realvnc.com) for linux. 
The screen locked? I think it's suppose to login with a "new" user, starting a new session and dont touch the current desktop on my ubuntu, so i get 2 users logged in at the same time.
I don't got Compiz.

---

### Post by ghost_ryder35 on 2008-04-06
is there a reason you are not using tightvnc on the windows machine and the default VNC installation on Ubuntu located under ,
System, Prefences, Remote Desktop?
 
From the messed up login you could try 
```

startx

```
from the terminal

---

### Post by Vegar on 2008-04-06
Well, i just recently found out about the default VNC that comes with ubuntu.. Maybe that causes the problem? Or.. cant normal vnc enterprice from realvnc.com connect to the vnc that comes with ubuntu?

Ill try to download tightvnc now. 

(I got loads of questions hehe :D)

edit: [http://img258.imageshack.us/img258/2007/04062008201120sy4.png](http://img258.imageshack.us/img258/2007/04062008201120sy4.png)

---

### Post by ghost_ryder35 on 2008-04-06
it should be able to work as long as the vnc that came wtih ubuntu is properly configured.  and inorder for that to work if you installed realvnc on the ubuntu machine you should remove it so it does not conflict with the default vnc.  in order for the deault vnc to work you must say you do not want a confirmation, set a password, and check allow other users to take control of my machine.  then you must login and lock your screen to login from the remote computer...

---

### Post by Vegar on 2008-04-06
Well, is there any easy way of removing all the files and stuff that got installed with VNC enterprise? I've already configured the vnc that comes with ubuntu exactly like you said.
And, i didnt quite get what you meant by "then you must login and lock your screen to login from the remote computer..." lock my screen to login from the remote computer?

---

### Post by ghost_ryder35 on 2008-04-06
whereever you installed it it might have an uninstall script like
```

sudo ./vnc-uninstall.pl

```
dont know the name of the uninstall file but it might look like that.  
You need to login to your Ubuntu machine and then hit the red power button and choose lock screen.  Then you can remote desktop into it from the XP machine using tightvnc and the password you setup on the ubuntu machine

---

### Post by Vegar on 2008-04-06
Okay, I'll try.

Edit: works now :D used something called synaptic package manager to remove vnc-e :D and i removed a catch in some box that said "only allow local connections". I think the the catch made it work, because before i did that, i couldnt even connect from the ubuntu (with vncviewer random:0) But it all works now ;) thanks.

and, earlier you asked me why i didnt use ubuntu default + tightvnc.. first: i didnt know about it tbh :D and second: vnc-e got shitloads of functions ^^

---

### Post by gsub on 2008-04-06
if you're connecting to an ubuntu (gutsy) pc with realvnc, there is no extra installation required on your ubuntu box. the vncviewer that comes default with the ubuntu installation works quite nicely.

however, other settings might be the reason why you are unable to connect. i'd check the following:

1. does the firewall (e.g. firestarter) allow vnc requests through?
2. are you using a wireless router to connect the ubuntu machine to the 'net? if so, you might need to change the router settings to allow vnc requests through
3. if both of these allow vnc requests, you need to configure the ubuntun box to accept vnc requests at Main Menu -> System Preferences -> Remote Desktop

---

### Post by ghost_ryder35 on 2008-04-06
congrate on getting it up and running.  make sure to mark this thread as SOLVED :)

---

