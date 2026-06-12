---
title: "apache questions"
date: 2008-06-01
forum: General Help
---

### Post by sandclock on 2008-06-01
Hey 
I have few questions about Apache 2 on ununtu
i want to install it on my lan and use it as dev platform for php
1. Do i need ubuntu server edition for this or can i install on 7.10 desktop edition
2. is there any way i can install and access on lan with automatic IP address?
thanks and regards
Nik

---

### Post by NikoC on 2008-06-01
Apache2 is definitely available from the repositories for all ubuntu users (server/regular). I installed it via:
sudo apt-get install apache2

To start up apache:
sudo /etc/init.d/apache2 start

To stop:
sudo /etc/init.d/apache2 stop

Same goes for php and mysql...

I hope this answers your first question...
The second one I'll leave for somebody else, cause I have no clue :lolflag:

---

### Post by latna on 2008-06-01
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

The wiki has a lot of tutorials for stuff like this.
[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

---

### Post by sandclock on 2008-06-01
hey guys thanks for reply but when i run command
```
sudo tasksel install lamp-server
```
in terminal i get installing packages 0% please wait. I tried other solutions like selecting best server in administration--> softaware sources but doesnt make any difference
any idea?
thanks and regards
Nik

---

### Post by latna on 2008-06-01
Can you install any packages? Try just apache2.

```
sudo apt-get install apache2
```

---

### Post by sandclock on 2008-06-01
hey guys thanks for help i was able to install apache with apt-get but now i have another problem
[http://127.0.0.1/](http://127.0.0.1/) --> works fine
but 
[http://localhost/](http://localhost/) doesnt work the browsuer says connecting [www.localhost.com](www.localhost.com) and then connection time out]
any ideas?
Regards
Nik

---

### Post by latna on 2008-06-01
Check /etc/hosts. Do you have a line that looks like this:

```
127.0.0.1       localhost
```

That's about the only idea that I've got.

---

### Post by sandclock on 2008-06-02
Hi guys
this is help. I have managed to get most of the part working but i am stuck at one point. Here is my situation.
1. I am trying to setup a local server on my lan for PHP development
2. I have managed to get it working as i can access [http://xxx.xxx.x.xx/(local](http://xxx.xxx.x.xx/(local) IP) from my lan.
3. i can also access [http://xxx.xxx.x.xx/svn](http://xxx.xxx.x.xx/svn)
4. I am using eclipse and have installed it on all my boxes. Now i am stuck here i dont know how all my devs can work on the server [http://xxx.xxx.x.xx/](http://xxx.xxx.x.xx/) which i have setup and use svn
Thanks and regards
Nik

---

### Post by sandclock on 2008-06-02
Hi i am attaching pdf of what i want to do 
may be this will clear up my requirements i hope some one can help me here
Regards
nik

---

### Post by sandclock on 2008-06-02
Bump anyone?

---

### Post by babylon2233 on 2008-06-02
I think it is about your router. Check the settings.

---

### Post by sandclock on 2008-06-02
> **babylon2233 said:**
> I think it is about your router. Check the settings.

Hi
I have solved other problems now i am trying to set up my server as a development server for all my developers in lan. any idea how to do this?
thanks

---

### Post by Master Chief on 2008-07-08
> **sandclock said:**
> Hi guys
this is help. I have managed to get most of the part working but i am stuck at one point. Here is my situation.

<snip />

4. I am using eclipse and have installed it on all my boxes. Now i am stuck here i dont know how all my devs can work on the server [http://xxx.xxx.x.xx/](http://xxx.xxx.x.xx/) which i have setup and use svn


You need to add the IP# of your Apache/PHP5 computer (the host) in the hosts file on the clients (your devs) and possibly add allow them in Firestarter (in case you have this firewall GUI installed on the host).

```
sudo gedit /etc/hosts
```

This is what I did:
192.168.1.100 [www.myserver.org](www.myserver.org)

Set the ServerName to [www.myserver.org](www.myserver.org)

Start my browser and enter: [www.myserver.org](www.myserver.org)

This might not be what *you* want, but most people seem to like this.

---

