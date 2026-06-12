---
title: "large file transfer comuter to computer"
date: 2006-11-12
forum: General Help
---

### Post by highneko on 2006-11-12
Hello. I'm using Gnome, Ubuntu Edgy desktop.

I bought a new computer recently, and my new one only seems to recognize sata hdds, and my old computer with my data uses something else. They are right next to eachother and both connected to the internet.

How would I transfer lots of data from one to the other, without any loss in data? Maybe a simple cord would help? They're right next to eachother, so there should be something simple I could do right?

The file transfers would have to be fast, so I could transfer hundreds of gigabytes easily.

---

### Post by 23meg on 2006-11-12
You could get a crossover ethernet cable and connect them to each other directly. With newer ethernet cards that accept all cables and autodetect if they're a crossover or normal cable, a normal ethernet cable should also do.

---

### Post by highneko on 2006-11-12
> **23meg said:**
> You could get a crossover ethernet cable and connect them to each other directly. With newer ethernet cards that accept all cables and autodetect if they're a crossover or normal cable, a normal ethernet cable should also do.
Someone suggested a crossover connection in #ubuntu irc. He said I would need to buy a cable tho. You're saying just a normal ethernet cord would work? I'll look for some information using google. Thank you.

---

### Post by srunni on 2006-11-12
An RJ54 crossover cable would allow for a direct PC-to-PC connection. You can either buy one of these (which is recommended), or you can modify one of your normal cat5e ethernet cables to be a crossover cable. You just have to switch some wires around.

---

### Post by highneko on 2006-11-13
I have them both connected to a router. I think I'm supposed to give them each their own static ip, then use some ssh-server or something. I'm confused.

---

### Post by 23meg on 2006-11-13
Set the IPs as 192.168.0.1 and 192.168.0.2, and both subnet masks as 255.255.255.0 .

---

### Post by tminuszero on 2006-11-13
No need to be confused. It's rather easy once you do it a few times.

If both computers are on the router then they already have IP addresses assigned, so don't waste your time. Go to the console on your new computer and type "ifconfig eth0" to find out your address. It should be on the second line, which should read somethihng like:

inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0

So the IP is 192.168.1.6. The address may be different for you. 

So go to the other computer, and find your files. Let's say they are in the  xyz folder, then all you need to do is run:

rsync -arvu /your/path/xyz user@192.168.1.6:/your/new/path

Replace "user" with the username on your new computer. Enter the password, and it should start to transfer.

---

### Post by highneko on 2006-11-14
Thank you for your help, unfortunately I'm still unable to connect. The problem is port 22 I think. Do I need sshd? I don't have this sshd thing running. There is no package "sshd".

telnet: Unable to connect to remote host: Connection refused
ssh: connect to host 192.168.0.X port 22: Connection refused
rsync gives me many different errors, I don't wanna paste them all.

I tried google, but havn't been successful yet. One page suggested editing /etc/hosts.allow.

They're both running Ubuntu Edgy Desktop, so they're probably very secure. x_x

---

### Post by koenn on 2006-11-14
post #8 is a good one and should do the trick.
rsync uses ssh, i tyhink, so you need to be able to connect to port 22.
find out where the "connection refused" comes from. 

Is that router also acting as a firewall ?
can you ping from one machine to the other ?
do you have ssh (package: openssh, i think) on both machines ?
you may also have to allow incoming ssh on the machine your trying to rsync with - but i'd need to look up how to check/configure that

as an alternative :
can you use samba file sharing ?

---

### Post by koenn on 2006-11-14
> One page suggested editing /etc/hosts.allow.

sounds right, this is where you'd allow incomming (ssh) connections from an other computer.

---

### Post by LenzM on 2006-11-14
> **highneko said:**
> Thank you for your help, unfortunately I'm still unable to connect. The problem is port 22 I think. Do I need sshd? I don't have this sshd thing running. There is no package "sshd".

telnet: Unable to connect to remote host: Connection refused
ssh: connect to host 192.168.0.X port 22: Connection refused
rsync gives me many different errors, I don't wanna paste them all.

I tried google, but havn't been successful yet. One page suggested editing /etc/hosts.allow.

They're both running Ubuntu Edgy Desktop, so they're probably very secure. x_x

You need the package 'openssh-server'

---

### Post by highneko on 2006-11-15
It's working, thank god! The problem was either my routers firewall(I knew I had one but hate configuring it) or I had to install openssh-server. Thank you all so much.

The first thing I did was transfer some music, and my firefox bookmarks.

sftp $USERNAME@$HOSTNAME #worked for me
scp -r $USERNAME@$HOSTNAME:/file . #works good for recursive folders

---

### Post by tminuszero on 2006-11-15
Congratulations! 

I saw that you edited your post - I was going to tell you about scp.

I usually use "scp -prC "

p - Preserves modification times, access times, and modes from the original file.

r - recursive

C - enables compression, which can help with large transfers

With -prC the timestamps are preserved, so you know the last time you edited a file was 2 years ago rather than the day that you transferred the files.

rsync can do the same and more. Most importantly it can "continue" in case your transfer gets interrupted.

Congrats again!

---

