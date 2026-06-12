---
title: "Samba Share -- Inaccessible from Windows"
date: 2014-01-18
forum: General Help
---

### Post by amorphouskev on 2014-01-18
This is a 2 part question - any assistance is VERY appreciated.

I've setup Ubuntu on an old laptop with the hope that I could use it as a backup for files (movies & music) from my current laptop. The hope is I'd be able to leave it running most of the time, connect it to my home network (wireless), and use it to stream movies on my PS3. So I thought Samba Share might be the best solution to bridge the 2 systems. 

Question 1: Is this the best (easiest) way to do this? I've used PS3 Media Server in the past, but occasionally had problems with it playing videos without stopping abruptly.

Question 2: I've got Samba setup on the Ubuntu system. From Ubuntu I'm able to see/access/modify the files on the Windows 8 system. The issue comes in when I try to access the Ubuntu folder ("MyShare" from Windows. I hoped to basically just drag and drop the files from Windows to an accessible Ubuntu folder. Because I don't plan on physically touching the Ubuntu system much - tucking it out of sight etc...).

I even added a folder to my Ubuntu desktop and shared it via properties window. Again, I can see this folder on my Windows machine, but I don't have access to open it or the MyShare folder. How do I fix this?

Computers:
 -Windows: Kevs-HP
 -Ubuntu: Kevin-ubuntu

---

### Post by tfrue on 2014-01-18
I personally love Samba, it amazing! So I would recommend it for your project.What I would do, just for the sake of simplicity and making it work, is to disable any security for Samba and make it wide open. 

So I only know how to use Samba from the command line, so if you're using GUI, I can't help much. Sorry.

Closing the lid on the laptop might also disable Samba as closing the lid hibernates the PC.

So lets start configuring Samba.

First, lets make sure you have it installed properly, type:
```
sudo apt-get install samba
```

Now we can edit the smb.conf file that Samba uses. Type:
```
sudo vim /etc/samba/smb.conf
```

Scroll all the way to the bottom with the arrow keys in vim. Then type '*o*', to start a new line:
```
[Share]
comment= My Share
path= /share/chris (Just as an example)
guest ok= yes
browseable= yes
read only= no
```

[Share], is you defining a new share and is what Window's will see when you are trying to connect.
Path is the path to the directory that you are sharing. Ex. /share/chris would be the directory that Window's would use.
Comment is simply a comment.
Guest ok is saying it's ok for anyone to connect, on the same LAN.
Browseable is allowing that directory to be seen by Windows.
Read Only is telling Samba we either do/don't want that share to be read only.

We can make this more secure later if you want and I will help with that too!

Now we need to restart the services, so type:
```
sudo service smbd restart
and
sudo service nmbd restart
```

You should now be able to access the share from Windows!

Good luck,
Chris

---

### Post by amorphouskev on 2014-01-18
Thanks for the additional info!! I actually managed to get it all setup somehow, and was headed here to change the thread status. I'm now able to access from both machines. Now I'm just trying to figure out how to more easily share files between the 2, since ubuntu doesn't seem to recognize the Windows shortcuts.

---

