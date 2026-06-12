---
title: "Can't fetch packages"
date: 2007-05-16
forum: General Help
---

### Post by viergeame on 2007-05-16
For the past week or so I have been unable to install any packages.  Even updates will not work.  Every time I try to install something I get a message saying that the packages couldn't be fetched.  I'm not sure what would have caused this and I have no idea how to go about fixing it.  

Also, since I installed Feisty on both of my computers I have to insert the install CD before I can get any packages to install.  Does this happen for everyone?

---

### Post by taurus on 2007-05-17
If you want to remove the CDROM option from your repos, then edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the line (usually first or second line) that has cdrom in it to comment it out.

Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```
Post the complete error message if there is one when you run those two commands from a terminal.

---

### Post by viergeame on 2007-05-17
Here are the errors I get trying to update.

nikki@nikki:~$ sudo aptitude update
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done

---

### Post by taurus on 2007-05-17
Any chance you are behind a firewall or a proxy?

---

### Post by viergeame on 2007-05-17
I'm not aware of any firewall or proxy.  I haven't installed any and noone else uses this computer.

---

### Post by wormser on 2007-05-17
It could be a DNS issue.  I found this [pos]("http://www.nabble.com/package-prob-t3755939.html")t.

> That showed nothing as well. On the upside have got it going via another
person. Ended up adding some dns servers in the network section via
system->Administration->network->DNS
Now working fine 

4.2.2.2 and 4.2.2.1 are DNS servers you can use.

Good luck

I found another [post]("http://ubuntuforums.org/showthread.php?t=431362") with the same resolution.

> I've had the same prob as well with my laptop. After some searching and asking on other forums someone gave the the idea of adding the isp's dns's in System->Administration->Network->DNS
That seems to have fixed it my end and hopefully will do the same for you. If you don't know your isp's dns's you can always use the ones from opendns which are 208.67.222.222 and 208.67.220.220 respectively

---

### Post by viergeame on 2007-05-17
Adding the DNS severs seems to have fixed everything.  Thanks a lot for your help!

---

