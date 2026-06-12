---
title: "The easiest way to keep track of my parents dynamic IP?"
date: 2007-07-20
forum: General Help
---

### Post by tseo on 2007-07-20
My parents are in another country. I left my old computer so we can communicate and installed Ubuntu on it.
Since now it was a smooth ride but I want to be able to connect to the VNC server whenever they need help.
heir ISP provides only dynamic IP and its not very convenient to make them tell me the IP all the time.
Is there some **easy to implement** way for me to keep track on the ever changing IP?

---

### Post by rscott5 on 2007-07-20
I had the same issue and came across this post: [http://ubuntuforums.org/showthread.php?t=470968](http://ubuntuforums.org/showthread.php?t=470968) I've been using dyndns.org and it works great. You install ddclient (which is in the Ubuntu repo) and it runs as a daemon and you can set it to update your ip as often as you want which well then send the ip to dyndns.org. So you never have to worry about the ip, you just go to username.dyndns.org. For instance, when I want to SSH into my machine from away, I ssh to [email]ryan@myusername.dyndns.org[/email] . It works awesome. You just need to make sure you open ports on the router for VNC to be directed to your machine. You should be able to find some good sample config files for ddclient online, but if you have trouble I can post mine when I get home on Sunday (I left my machine off so I can't SSH in oops!). Best of luck!

---

### Post by Stephen Howard on 2007-07-20
Maybe configure their computer with a script that sends you an email with the new IP whenever it changes?

Alternatively, would [dyndns.org]("http://www.dyndns.com/about/home_solutions.html") help?

---

### Post by tseo on 2007-07-20
Well I am a newbie with all the Linux stuff and can't do anything from scratch like setting Ubuntu to send emails with the IP.
This service looks very convenient and will be a challenge to set up remotely and with my limited knowledge but I hope I manage to do it.
If there is some easier to set up way like something sending me mail or something which I can use while struggling with the real deal I will be thankful:)

---

### Post by Yasumoto on 2007-07-21
It actually shouldn't be too bad. go to dyndns.com and register, then go to their dynamic dns section. (it should be [here]("https://www.dyndns.com/account/services/hosts/dyndns/"), just add a new host with your parents IP address.I'm still trying to figure out how I set up my other computer to auto-update, but I'll post it here once I remember.

---

### Post by Yasumoto on 2007-07-21
This should be a better explanation:

[http://ubuntuforums.org/showthread.php?t=247563](http://ubuntuforums.org/showthread.php?t=247563)


I seem to recall using apt-get to install a program, but this'll do the trick regardless.

---

