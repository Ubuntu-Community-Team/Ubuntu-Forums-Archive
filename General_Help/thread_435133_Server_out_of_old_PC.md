---
title: "Server out of old PC?"
date: 2007-05-06
forum: General Help
---

### Post by Znupi on 2007-05-06
I have an old PC, with these specs:
AMD K6/2 266Mhz CPU
About 96MB of RAM
Ati Rage Pro 3D 8MB video card (I think, it may be 4MB, and not sure about model, either :-k)

And I want to make this a server (mainly HTTP, but will have to have ssh and samba). At the same time, I don't want to go with the Server Edition, because I want a graphical interface so I can set it up (I'm pretty much a noob and I'm not able to operate command-line only). Would Ubuntu work on this machine? Can I somehow 'close' the graphical interface after setting it up, so it doesn't consume CPU and RAM? What version of Ubuntu should I try? Should I try Ubuntu, or maybe there's a distribution more suitable for what I'm trying?

---

### Post by denzilla on 2007-05-06
Not sure about what others will suggest, but I've been toying with ClarkConnect and its pretty cool. You login to the GUI from another PC (like a router) and configure things there. It has FTP, HTTP, Samba,  and a whole lot more. Registration is required, but still free for home use.

[http://www.clarkconnect.com/index.php](http://www.clarkconnect.com/index.php)

I had FTP and Samba setup in short order. Web GUI will work fine on those specs.

The login IP for when you get it setup  is [https://192.168.X.XXX:81/admin/](https://192.168.X.XXX:81/admin/)

---

### Post by jfinkels on 2007-05-06
You're gonna have a hard time setting up ANY GUI on 96MB RAM...better start learning how to use the command line :D

---

### Post by Talon2 on 2007-05-06
> **Znupi said:**
> I have an old PC, with these specs:
AMD K6/2 266Mhz CPU
About 96MB of RAM
Ati Rage Pro 3D 8MB video card (I think, it may be 4MB, and not sure about model, either :-k)

And I want to make this a server (mainly HTTP, but will have to have ssh and samba). At the same time, I don't want to go with the Server Edition, because I want a graphical interface so I can set it up (I'm pretty much a noob and I'm not able to operate command-line only). Would Ubuntu work on this machine? Can I somehow 'close' the graphical interface after setting it up, so it doesn't consume CPU and RAM? What version of Ubuntu should I try? Should I try Ubuntu, or maybe there's a distribution more suitable for what I'm trying?

I think what you are looking for is the Alternate Install CD of:

[http://www.xubuntu.org/](http://www.xubuntu.org/)

Good luck.

---

### Post by Znupi on 2007-05-06
ClarkConnect sounds nice but I already have a rooter and I don't know how the two would get along...

I'm going to try xubuntu, sounds promising :) Thanks!

---

### Post by afoglia on 2007-05-06
If you really want the GUI, you're going to need more RAM, even with Xubuntu.  Expect it to be very slow on the machine.  As for shutting it down, once you boot up, press Ctrl-Alt-F2 to get to a pure text terminal, login, and then type
```
sudo /etc/init.d/gdm stop
```
to kill the GUI login prompt.  If you want to keep the GUI from starting automatically, use the command sysv-rc-conf to unset gdm from starting automatically.

---

### Post by denzilla on 2007-05-06
> **Znupi said:**
> ClarkConnect sounds nice but I already have a rooter and I don't know how the two would get along...

I'm going to try xubuntu, sounds promising :) Thanks!


No, no no, you don't have to install the routing/firewall functions. You select the modules you want to install during setup. I only use the FTP, HTTPS and Samba :)

---

### Post by regomodo on 2007-05-06
I wouldn't suggest any form of Ubuntu for a server. 96mb, as others say, is too little for thse distros.

Try freeNAS or just use Damn Small Linux

---

### Post by tgalati4 on 2007-05-06
RAM is cheap.  You can bump up to 128 MB as a minimum and add a generous swap drive.  That will get you a gui with Xubuntu.  Add 256 MB and you will have a usable(but dreadfully slow) gnome desktop with all of the gui configuration tools.  You can learn Ubuntu and set up servers as needed.  When things are running properly, you can turn off the xserver as explained above to improve server performance, but depending on what you are doing, you may not notice any improvement.  The xserver will use about 10% of the cpu cycles on that class of machine.

Damn Small Linux will run well on that machine and it has some simple ssh, ftp, and http servers built in.  Give it a shot first, as it loads quickly and you can set it up in an hour if you know what you are doing.  The DSL forums are helpful, but not quite as responsive as Ubuntu.  You do need to read the DSL wiki's and how-tos to set things up.

Good luck.

---

### Post by reckless2k2 on 2007-05-06
Considering that makeup of that machine, RAM is not cheap. He'd be lucky if he's got PC100 and even still he may be at max now with RAM. The idea is basically to use what he has to get what he wants. Unfortunately, you are not going to find it with any Ubuntu version except the Server edition. You could install it and then install webmin for a GUI to log into but webmin is not very easy to navigate. 

As suggested previously, Damn Small Linux would be a GOOD selection unless you want to mess around with the Ubuntu server edition and webmin.

---

### Post by denzilla on 2007-05-06
I hate to keep plugging CC, but it ran on 96meg/400Mhz cpu fine and the web GUI is very well laid out.

---

### Post by Znupi on 2007-05-07
Where can I find this webmin? Sounds interesting :). I want to go with Ubuntu because it has very good support and because I'm used to it :).

---

### Post by nexusus on 2007-05-08
Webmin... [http://www.webmin.com/download.html](http://www.webmin.com/download.html)

This is good tutorial
[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

To install webmin... some files you'll need only the CD and other times(mostly) internet connection...download directly.

Command line#...
sudo su 
apt-get update 
apt-get install libnet-ssleay-perl 
apt-get install smbfs 
cd /usr/local 
mkdir webmin 
cd webmin 
wget [http://prdownloads.sourceforge.net/webadmin/webmin-1.34.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.34.tar.gz) 
That its...for that part...


Need to install ssh shell so you can connect from outside into the Server (Windows workstation to Ubuntu Server)... need internet access to download these programs and some will be on the Ubuntu Server CD.

sudo apt-get install ssh openssh-server 
or 
apt-get install ssh openssh-server 

Once have installed webmin and ssh you can access it from external workstation.

 [https://yourmachinename:10000/](https://yourmachinename:10000/)

---

### Post by Znupi on 2007-05-28
Ok, so I'm installing Xubuntu... it's been 3 or 4 hours from when the instalation process started. Is this normal? Installing Windows XP took like an hour and a half on the same machine :|.

---

