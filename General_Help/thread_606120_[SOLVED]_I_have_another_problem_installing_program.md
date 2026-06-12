---
title: "[SOLVED] I have another problem installing programs..."
date: 2007-11-07
forum: General Help
---

### Post by some_los3r on 2007-11-07
So this is my third day using Ubuntu and I'm loving it so far. I've only had one problem with it so far. I'm just a noob and it was easy to fix(thanks to someone on this site.) I just tried to download LimeWire, And well This is what happened...
[IMG]http://i83.photobucket.com/albums/j310/some_los3r/Screenshot.png[/IMG]
There's everything going normal...
[IMG]http://i83.photobucket.com/albums/j310/some_los3r/Screenshot-1.png[/IMG]
It's downloaded normally, and then I clicked "Install Package"
[IMG]http://i83.photobucket.com/albums/j310/some_los3r/Screenshot-2.png[/IMG]
And then Uh oh..
It says "Only one software management tool is allowed to run at the same time"
What?! 
That's the only one I have open!
Ok, whatever. I could live without LimeWire. 
So I tried to install a package by going to System-->Administration-->Synaptic Package Manager. 
And this is what happened...
[IMG]http://i83.photobucket.com/albums/j310/some_los3r/Screenshot-3.png[/IMG]
:mad:
I have no idea what to do. I'm still an Ubuntu noob, so sorry.
Thanks for any help!

---

### Post by Maestro23 on 2007-11-07
Close everything down.  Open a terminal (Apps>>Accessories>> Terminal) and run the following commands:

> sudo dpkg --configure -a

sudo apt-get update


Post back your results.

*Links for future reference: Installing Software
nstalling Anything: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Psychocats Page: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by some_los3r on 2007-11-07
Thanks for the quick reply. Here ya go...

nick@tMac:~$ sudo dpkg --configure -a
[sudo] password for nick:
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
nick@tMac:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Fetched 1B in 0s (1B/s)  
Reading package lists... Done

---

### Post by Maestro23 on 2007-11-07
> **some_los3r said:**
> Thanks for the quick reply. Here ya go...

nick@tMac:~$ sudo dpkg --configure -a
[sudo] password for nick:
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
nick@tMac:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Fetched 1B in 0s (1B/s)  
Reading package lists... Done

Post your **/etc/apt/sources.list**

> cat /etc/apt/sources.list

Copy/Paste the file here.

---

### Post by some_los3r on 2007-11-07
How do I get that? Sorry. 
And a second ago, I tried to run Synaptic again, and this came up...
[IMG]http://i83.photobucket.com/albums/j310/some_los3r/Screenshot-4.png[/IMG]
I looked under the "Broken" filter, and nothing came up.

---

### Post by Maestro23 on 2007-11-07
For the commands to get your sources.list, you need to open a terminal. Apps>> Accessories>> Terminal

For the Broken packages. In Synaptic, there is "Fix Broken Packages" option under Edit.  If that doesn't work, the "Broken Filter" option is found under "Settings>>Filter"

---

### Post by some_los3r on 2007-11-07
Ah, thank you. After I did that, I was able to download LimeWire and its working. So thanks for all of your help! :)

---

### Post by Maestro23 on 2007-11-07
> **some_los3r said:**
> Ah, thank you. After I did that, I was able to download LimeWire and its working. So thanks for all of your help! :)

Good deal man. :)

---

