---
title: "Packet Tracer 7.0"
date: 2016-11-04
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-11-04
Okay, I have this program from Cisco Network Academy called Packet Tracer and I need to install it.  In the folder it has a file called "install".  When I double click it it opens a text file, but I can't see anything on how to install it.  Can someone help me out here?

---

### Post by shane_faulkinbury2 on 2016-11-05
Can someone please help me?  All I am asking is how to run the install file!  Take a look at the pic.

---

### Post by #&amp;thj^% on 2016-11-05
> **shane_faulkinbury2 said:**
> Can someone please help me? All I am asking is how to run the install file! Take a look at the pic.

@shane_faulkinbury2 have you yet right clicked on that install script and checked if it is allowed to run as an executable? You will need to do this.

Open terminal and use the code below
```
cd /Downloads/PacketTracer70/  ###Or your path to PacketTracer
```

To Install use the command: ./install
```
./install
```
3. Accept the EULA....

Read the following End User License Agreement "EULA" carefully. You must accept the terms of this EULA to install and use Cisco Packet Tracer.
Press the Enter key to read the EULA.
This will take a little time to finish.
When finished it will show you: 
Cisco Packet Tracer 7.0 installed successfully

Now to launch cd to /usr/local/bin 

```
cd /usr/local/bin 

```
And issue this

```
packettracer

```
Now you will need to login with your Login Credentials or Token
Cheers

---

### Post by shane_faulkinbury2 on 2016-11-05
Okay, thanks for your help!  I got it installed, but it wanted to install the startup in another directory and stupid me didn't bother to look witch directory it installed to.  So I was going to remove it and reinstall to see what directory it was going in, but I'm not sure what it's called to remove it.  It's not Packettracer 70 because I've already tried that.

---

### Post by #&amp;thj^% on 2016-11-05
No! do not move it shane_faulkinbury2 it installs to "opt.pt"
The way to launch it is in the above post "cd /usr/local/bin"
and then "packettracer"
And you are Welcome...hope it works for you.
Regards

---

### Post by shane_faulkinbury2 on 2016-11-05
Like I said, it was moved while I was installing it.  That's why I need to reinstall it.

---

### Post by #&amp;thj^% on 2016-11-05
Ok...I understand now.;)

---

### Post by #&amp;thj^% on 2016-11-05
@shane_faulkinbury2
Try this for me:
```
cd /opt/pt/
```
Let's see if it there with:
```
ls
```
And if packettracer is shown there issue this next:
```
./packettracer
```
And now dose it start?

---

### Post by shane_faulkinbury2 on 2016-11-05
This is what I get when I reinstall it it.  So how do I start it?

---

### Post by #&amp;thj^% on 2016-11-05
See my above post#8

---

### Post by shane_faulkinbury2 on 2016-11-05
Thanks again!  Logged in and running!  :P

---

### Post by #&amp;thj^% on 2016-11-05
Cool... Good to hear. And Your Welcome!
Enjoy

---

### Post by shane_faulkinbury2 on 2016-12-25
I had to redo my computer and I'm trying to reinstall PacketTracer and now I'm getting permission denied.  What should I do now?

---

### Post by vasa1 on 2016-12-25
When you have information from a terminal that you wish to share, please copy the text and paste it here within code tags (the # icon) rather than as a screenshot.

---

### Post by shane_faulkinbury2 on 2016-12-25
Thanks!

```
bubba@bubba-110-194:~$ sudo su
[sudo] password for bubba: 
root@bubba-110-194:/home/bubba# cd Downloads
root@bubba-110-194:/home/bubba/Downloads# cd PacketTracer70
root@bubba-110-194:/home/bubba/Downloads/PacketTracer70# initInstall ()
> install
bash: syntax error near unexpected token `install'
root@bubba-110-194:/home/bubba/Downloads/PacketTracer70# initinstall
initinstall: command not found
root@bubba-110-194:/home/bubba/Downloads/PacketTracer70# ./install
bash: ./install: Permission denied
root@bubba-110-194:/home/bubba/Downloads/PacketTracer70# cd /opt/pt/
bash: cd: /opt/pt/: No such file or directory
root@bubba-110-194:/home/bubba/Downloads/PacketTracer70# ./packettracer
bash: ./packettracer: No such file or directory
root@bubba-110-194:/home/bubba/Downloads/PacketTracer70# ./install
bash: ./install: Permission denied
root@bubba-110-194:/home/bubba/Downloads/PacketTracer70# 

```

---

### Post by vasa1 on 2016-12-25
I forgot to mention that you can also mark the thread "Unsolved" if the problem has reappeared. See #4 here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by shane_faulkinbury2 on 2016-12-25
Thanks again!  I kind of wondered about that!  :o:rolleyes:

---

### Post by vasa1 on 2016-12-25
By the way, I don't know if this is related: [Installing CISCO Packet Tracer 7 on Ubuntu 16.10]("http://askubuntu.com/questions/864226/installing-cisco-packet-tracer-7-on-ubuntu-16-10").

---

### Post by shane_faulkinbury2 on 2016-12-25
Wow, your on it vasa!  This did the trick ```
sudo bash install
```

---

