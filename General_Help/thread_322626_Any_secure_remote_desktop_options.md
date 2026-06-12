---
title: "Any secure remote desktop options?"
date: 2006-12-20
forum: General Help
---

### Post by m.musashi on 2006-12-20
I'm setting up my mother with ubuntu but since she lives several hours from me I'd like to also set up a remote desktop so that I can connect and help her when she needs it.

I think vnc would be an option but in order to connect she would have to open up port 5900 (I think) on her modem/router. That is probably not a good idea.

Does anyone know a good option as well as a how to to set it up (still very much a noob despite my best efforts)?

Thanks.

---

### Post by bodhi.zazen on 2006-12-20
Take a look at this: [http://ubuntuforums.org/showthread.php?&t=256102](http://ubuntuforums.org/showthread.php?&t=256102)

---

### Post by m.musashi on 2006-12-20
Thanks for the link. I didn't see that when searching earlier. However, it didn't specify what to use to connect other than putty from windows. Will ssh actually give me a remote desktop or do I use it in conjunction with vnc or something else? If so, how do I do that?

Thanks.

---

### Post by bodhi.zazen on 2006-12-20
You can use vnc through vnc, ssh give access to the command line, and you can forward X through ssh.

If you forward X to windows you need an X server. I have used cygwin. There are others available :)

---

### Post by m.musashi on 2006-12-20
Sorry for being dense but if I'm on ubuntu and my mother is on ubuntu with an ssh port open as per the link you provided, what would I need to do to get a graphical remote desktop yet still use ssh to keep things secure? Actually, I'm not overly concerned about a secure remote desktop connection but rather just avoiding opening up ports and opening her to whatever. She already has that with windows.

---

### Post by bodhi.zazen on 2006-12-21
Take a look at these links:

[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.cs.rit.edu/~cslab/tutorial/data/ssh/](http://www.cs.rit.edu/~cslab/tutorial/data/ssh/)

ssh -X [email]user@ip.addr[/email]ess ; the -X option forwards X ;)

---

### Post by madcow72 on 2006-12-21
Hey!  I'm sure that ssh is more secure, but I've just gotten the reverse vnc connection to do remote administration to my brothers computer (just got him to delete windoze for Kubuntu 6.10) and I'm definitely a big fan!  I followed [[COLOR="Blue"]these directions[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=299489") and it couldn't have been easier.  If you're behind a firewall, you have to make sure that port 5500 points to your IP address, (the generic 192.168.0.XXX address - this can be found on the firewall settings of your mother's router, perhaps), but other than that, it is extremely handy for remote administration I've found.
You can find my same post on this issue [[COLOR="Blue"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=316221").

---

### Post by m.musashi on 2006-12-21
Thanks for the links guys. I think I have some ideas how to go about this. I really like the reverse vnc idea. Especially since it sounds like I won't have to mess with her router at all.

@bodhi.zazen - The last command you posted (ssh -X [email]user@ip.addr[/email]ess) does that work much like the reverse vnc? Does it work with nothing more than ssh installed (an obviously an open port on the receiving computer)? That sounds pretty slick.

---

### Post by bodhi.zazen on 2006-12-21
> **m.musashi said:**
> Thanks for the links guys. I think I have some ideas how to go about this. I really like the reverse vnc idea. Especially since it sounds like I won't have to mess with her router at all.

@bodhi.zazen - The last command you posted (ssh -X [email]user@ip.addr[/email]ess) does that work much like the reverse vnc? Does it work with nothing more than ssh installed (an obviously an open port on the receiving computer)? That sounds pretty slick.

Yep. You will have to "mess with her router" so to speak, but the -X forwards X to your box :)

---

### Post by scrooge_74 on 2006-12-21
> **m.musashi said:**
> Thanks for the links guys. I think I have some ideas how to go about this. I really like the reverse vnc idea. Especially since it sounds like I won't have to mess with her router at all.

@bodhi.zazen - The last command you posted (ssh -X [email]user@ip.addr[/email]ess) does that work much like the reverse vnc? Does it work with nothing more than ssh installed (an obviously an open port on the receiving computer)? That sounds pretty slick.

Just my opinion, it suppose not a good idea to forward X not even using SSH.  If your mother is going to be using SSH, then you can make all admin and maintenance from the command line using ssh, if you need to open files I use gnome to log in using ssh so i can browse the /home directory.

And some one correct me if I am wrong, but forwarding X wont use up your bandwith?

---

### Post by m.musashi on 2006-12-21
Damn, that was fast. Just to clarify, the computer doing the forwarding will also need to open ports? After reading the reverse vnc thread I thought maybe that computer would not need any port forwarding since it would be going out and not coming in. I take it that's incorrect?

---

### Post by scrooge_74 on 2006-12-21
Well you are going to at least open ports on both machine and the one you are loggin in has to forward ports (from what I remember of using putty)

---

### Post by m.musashi on 2006-12-22
> **bodhi.zazen said:**
> ssh -X [email]user@ip.addr[/email]ess ; the -X option forwards X ;)

I just tried to do this from my desktop to my laptop (cap X and all). I got a login prompt for the laptop and was able to login an ssh session but the desktop was not forwarded. Maybe I misunderstand but I thought the computer I forwarded to would receive a gui of the desktop being forwarded. If that is a correct understanding, any idea why it doesn't work?

Thanks.

---

### Post by bodhi.zazen on 2006-12-22
You may need a little more configuration.

Start by logging in (via ssh -X ...)

Then enter```
gnome-session
```And you should get a remote desktop ...

---

### Post by m.musashi on 2006-12-22
Now I get it. I keep thinking my mother would "send" me her desktop but really I'm logging in to the remote computer and "taking" the desktop. However, this didn't work real well. I got panels (which covered up my own panels) but that's it. It would be enough to fix whatever needed fixing but she would not be able to see what I'm doing. Actually, without the full gui desktop it may be hard for me to fix anything. If I can't see what it's doing it will be hard to fix.

Still, a cool option and I'm glad to know I have it. Do you think the lack of a full desktop could be because of differing resolutions?

---

### Post by scrooge_74 on 2006-12-22
You usually can make changes using the termina, can even reboot or shutdown remotely.  You can update her PC. Install programas, etc. You don't really need a GUI for most things

---

### Post by m.musashi on 2006-12-22
> **scrooge_74 said:**
> You usually can make changes using the termina, can even reboot or shutdown remotely.  You can update her PC. Install programas, etc. You don't really need a GUI for most things

Thanks for the vote of confidence, but I need the gui because I'm not that much of an expert - really not much more than a noob. I'm sure I can do most of the normal maintenance from the terminal but my main concern was if something odd was happening I wouldn't be able to observe it. If I do a good job at install it may not matter and I can always use vnc if I just want to see what's going on. Also, vnc would let me show her how to do things rather than just do it all for her.

---

### Post by madcow72 on 2006-12-22
I think I'm like you in that I'm too much a noob and need the GUI as well as the terminal to totally get myself around.  Did you try the reverse vnc thing?  With my brother, I got him to connect up to a chat through Gaim (or Kopete) and then gave him the code to connect to me through there:
```
sudo aptitude install x11vnc
x11vnc -connect your.ip.address:5500
```
For some reason, however, his computer could not find x11vnc in the US repositories, so I switched him to the Canadian repositories for ubuntu and the package was then immediately found and installed - that was the only complication we ran into.  If you've put your computer into listen mode, ```
vncviewer -listen
``` then as soon as she issues the -connect command, you get a window on your monitor over which both you and your mother have control - so it's great for tutorials.  With dual monitors this is even better because you can keep Gaim open on one to communicate, and her desktop on the other.  

Even though we both have the same resolution, however, (1280x1024), his desktop forwards slightly larger than mine somehow, so I sometimes have to use the bottom and side scrollbars, but that was only a minor downside to having immediate control over his computer.  Also, his bandwidth isn't great, downloads ~ 20kb/s, but was able to forward his X to me with only a slight drop in performance (mouse and other animations are a little jerky.)

---

### Post by m.musashi on 2006-12-22
I don't have access to the computer yet but I will in a couple days. I will set up both ssh and the reverse vnc options. I won't be able to test anything though until she is on her network and I'm on mine. I hope there won't be any router issues with the reverse vnc because I'm not sure I will be able to walk her through port forwarding over the phone and I won't have access to the router as she is bringing the tower to me.

With regards to ssh, is it always listening on port 22 or whatever port you set up? Does that mean it would be possible to hack in if someone just tried a bunch of usernames and passwords. I know that would be hard but certainly not impossible. I have rather simple passwords for my kids so just wondering. I actually turn off port forwarding on my router except when I'm using it.

---

### Post by madcow72 on 2006-12-22
I think I mentioned something incorrectly on my previous post, because it doesn't matter if she's behind a router, firewall, or anything - you don't have to touch her router.  You only have to touch your own router and make sure that any request coming from her external IP address (I just tell my brother to go to [www.whatismyipaddress.com](www.whatismyipaddress.com) and read me the numbers) will be forwarded to your internal IP using port 5500.  This way, almost all of the configuration is done on your end, and all your mother has to do is paste the "install x11vnc" and "x11vnc -connect" lines into a terminal.  If your router is configured right, Voila! You've got her desktop in a window.

Like I said, though, I don't know much yet about ssh - most hardcore linux people I know like to use ssh and I'm sure there's a good reason behind that.  I did, however, find vnc to be as easy as the tutorial said it would be.

---

### Post by bodhi.zazen on 2006-12-22
ssh is secure, and you can tunnel vpn through ssh to increase security ....

ssh is nice because it gives a CLI (with a little experience you will find a terminal is all it takes). You can run a gui if you like, or just enter the name of program if you do not want  a full desktop. For example, ssh -X ....

Then synaptic & 

gives synaptic on your desktop ;)

---

### Post by fakie_flip on 2007-05-20
> **m.musashi said:**
> I don't have access to the computer yet but I will in a couple days. I will set up both ssh and the reverse vnc options. I won't be able to test anything though until she is on her network and I'm on mine. I hope there won't be any router issues with the reverse vnc because I'm not sure I will be able to walk her through port forwarding over the phone and I won't have access to the router as she is bringing the tower to me.

With regards to ssh, is it always listening on port 22 or whatever port you set up? Does that mean it would be possible to hack in if someone just tried a bunch of usernames and passwords. I know that would be hard but certainly not impossible. I have rather simple passwords for my kids so just wondering. I actually turn off port forwarding on my router except when I'm using it.

Yes, it is called a brute force dictionary attack. Choosing weak passwords is a very bad idea. You could disable password logins and use encryption keys for logging in instead. run gksu users-admin and generate a random password. it will be much more secure and much less likely to be guessed or cracked.

---

### Post by graigsmith on 2007-05-20
what i have, is a dynamic ip address for both my and my mom's computers, i have her set up with a ssh server, and to allow only my dynamic dns name.  ssh, allows you to have a command prompt on her computer. and the firewall keeps people from trying to log into her VNC server.

---

