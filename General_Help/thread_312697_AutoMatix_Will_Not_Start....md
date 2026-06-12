---
title: "AutoMatix Will Not Start..."
date: 2006-12-04
forum: General Help
---

### Post by JustDon on 2006-12-04
I downloaded and installed AutoMatix last week and have used it to download several nice applications. It has worked fine until yesterday. Synaptic alerted me to an update for AutoMatix which I prompted it to download and install. Every since that time AutoMatix will NOT start. I get this message: 

[COLOR="Blue"]**Sorry AutoMatix can not continue because some keys could not be downloaded, please try again later.**[/COLOR]

What would/could cause this and how might I repair it? Thanks in advance.

---

### Post by arnieboy on 2006-12-04
paste the results of the following command:
```
sudo apt-key list
```

---

### Post by JustDon on 2006-12-05
> **arnieboy said:**
> paste the results of the following command:
```
sudo apt-key list
```

/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/81836EBF 2006-06-26
uid                  Treviño (3v1n0) <trevi55@gmail.com>
sub   4096g/EDD1E155 2006-06-26

pub   1024D/521A9C7C 2006-06-04
uid                  Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>
sub   2048g/25D9D9E3 2006-06-04

---

### Post by arnieboy on 2006-12-05
do the following:
```
wget http://www.getautomatix.com/keys/jriddell.key
wget http://www.getautomatix.com/keys/quinn2.key
wget http://www.getautomatix.com/keys/quinn3.key
wget http://www.getautomatix.com/keys/sos.key
sudo apt-key add jriddell.key
sudo apt-key add quinn2.key
sudo apt-key add quinn3.key
sudo apt-key add sos.key
```
and then run AX2

---

### Post by JustDon on 2006-12-06
> **arnieboy said:**
> do the following:
```
wget http://www.getautomatix.com/keys/jriddell.key
wget http://www.getautomatix.com/keys/quinn2.key
wget http://www.getautomatix.com/keys/quinn3.key
wget http://www.getautomatix.com/keys/sos.key
sudo apt-key add jriddell.key
sudo apt-key add quinn2.key
sudo apt-key add quinn3.key
sudo apt-key add sos.key
```
and then run AX2

The first line gives me this: 

dhatcher2@dhatcher2-desktop:~$ wget [http://www.getautomatix.com/keys/jriddell.key](http://www.getautomatix.com/keys/jriddell.key)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.

---

### Post by arnieboy on 2006-12-06
[http://getautomatix.com/wiki/index.php?title=Proxy_configuration](http://getautomatix.com/wiki/index.php?title=Proxy_configuration)
[http://ubuntuforums.org/showthread.php?t=312867](http://ubuntuforums.org/showthread.php?t=312867)

---

### Post by JustDon on 2006-12-07
> **arnieboy said:**
> do the following:
```
wget http://www.getautomatix.com/keys/jriddell.key
wget http://www.getautomatix.com/keys/quinn2.key
wget http://www.getautomatix.com/keys/quinn3.key
wget http://www.getautomatix.com/keys/sos.key
sudo apt-key add jriddell.key
sudo apt-key add quinn2.key
sudo apt-key add quinn3.key
sudo apt-key add sos.key
```
and then run AX2

OK, I did the apt-get and wget configuration. I did not know my IP address so I used a website that "got it for me". When I run the first line above I get:

dhatcher2@dhatcher2-desktop:~$ wget [http://www.getautomatix.com/keys/jriddell.key](http://www.getautomatix.com/keys/jriddell.key)
--14:29:12--  [http://www.getautomatix.com/keys/jriddell.key](http://www.getautomatix.com/keys/jriddell.key)
           => `jriddell.key'
Connecting to 65.25.50.116:8080...

And it just sits and waits and waits. I also tried just running AutoMatix and it goes past where it first stopped but it sticks on "retrieving keys" and never fully loads....

I also tried to "declare proxy and ftp in $HOME/bashrc" as you specified in the other link that you posted but I don't see anything in that file about proxies and ftp's therein. I am somewhat of a novice with Ubuntu still, what exactly am I to do in the $HOME/bashrc file?

---

### Post by JustDon on 2006-12-11
Can someone tell me how to figure out what my "port" number is? I tried 8080 for setting up wget and apt-get but it did not work at all.

---

### Post by JustDon on 2006-12-14
OK, obviously there is no fix for this AutoMatix issue, is there any way to uninstall it completely and leave VLC Media player in place, I do like that application.

---

