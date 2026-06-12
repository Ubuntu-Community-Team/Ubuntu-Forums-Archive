---
title: "I can't install updates"
date: 2008-06-07
forum: General Help
---

### Post by Shoek on 2008-06-07
That's it. I am notified for new updates. I say ok, but then the window goes all half-white. Nothing happens. Forever.

[img]http://img176.imageshack.us/img176/8922/28393544nm4.png[/img]

What do I do?

---

### Post by rampageoberon on 2008-06-07
Try the following code in terminal and see if that updates.

```

sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

```

This is assuming you are using hardy (the earlier versions might just need upgrade and dist-upgrade respectively)

Hope that helps

---

### Post by Shoek on 2008-06-07
Ok, I pasted your lines and it sure did something. So it installed the updates now? By the way why do I get that error message "unable to resolve host hjemmeserver"? And how can I install the file sharing support? It won't let me install that as well.

```
hjemmeserver@hjemmeserver:~$ sudo aptitude update
sudo: unable to resolve host hjemmeserver
[sudo] password for hjemmeserver: 
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy Release.gpg
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy Release 
Get:2 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates Release [58.5kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                   
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/main Packages                    
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/universe Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Get:3 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main Packages [90.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Get:4 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/restricted Packages [6156B]
Get:5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main Sources [21.6kB]
Get:6 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/restricted Sources [906B]
Get:7 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/universe Packages [36.9kB]
Get:8 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/universe Sources [6560B]
Get:9 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/multiverse Packages [7821B]
Get:10 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/multiverse Sources [1234B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources    
Fetched 231kB in 1s (228kB/s)                                       
Reading package lists... Done
hjemmeserver@hjemmeserver:~$ sudo aptitude safe-upgrade
sudo: unable to resolve host hjemmeserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be upgraded:
  dpkg evolution evolution-common evolution-data-server 
  evolution-data-server-common evolution-plugins libcamel1.2-11 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libgdata-google1.2-1 libgdata1.2-1 libgnomeui-0 
  libgnomeui-common libgtk-vnc-1.0-0 libnautilus-extension1 nautilus 
  nautilus-data rhythmbox 
24 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.8MB of archives. After unpacking 242kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main dpkg 1.14.16.6ubuntu4 [2296kB]
Get:2 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main evolution-data-server 2.22.2-0ubuntu1 [418kB]
Get:3 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main evolution-data-server-common 2.22.2-0ubuntu1 [74.3kB]
Get:4 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libedataserver1.2-9 2.22.2-0ubuntu1 [113kB]
Get:5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libcamel1.2-11 2.22.2-0ubuntu1 [304kB]
Get:6 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libebook1.2-9 2.22.2-0ubuntu1 [79.6kB]
Get:7 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libecal1.2-7 2.22.2-0ubuntu1 [242kB]
Get:8 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libedata-book1.2-2 2.22.2-0ubuntu1 [47.6kB]
Get:9 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libedata-cal1.2-6 2.22.2-0ubuntu1 [57.1kB]
Get:10 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libegroupwise1.2-13 2.22.2-0ubuntu1 [107kB]
Get:11 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libgdata1.2-1 2.22.2-0ubuntu1 [60.0kB]
Get:12 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libgdata-google1.2-1 2.22.2-0ubuntu1 [12.7kB]
Get:13 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main evolution 2.22.2-0ubuntu1.2 [2603kB]
Get:14 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main evolution-common 2.22.2-0ubuntu1.2 [15.7MB]
Get:15 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libedataserverui1.2-8 2.22.2-0ubuntu1 [77.3kB]
Get:16 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libexchange-storage1.2-3 2.22.2-0ubuntu1 [119kB]
Get:17 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libgnomeui-common 2.22.1.0-0ubuntu2 [22.2kB]
Get:18 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libgnomeui-0 2.22.1.0-0ubuntu2 [247kB]
Get:19 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main evolution-plugins 2.22.2-0ubuntu1.2 [161kB]
Get:20 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libgtk-vnc-1.0-0 0.3.4-0ubuntu2 [41.3kB]
Get:21 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main libnautilus-extension1 1:2.22.3-0ubuntu2 [52.9kB]
Get:22 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main nautilus-data 1:2.22.3-0ubuntu2 [901kB]
Get:23 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main nautilus 1:2.22.3-0ubuntu2 [838kB]
Get:24 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) hardy-updates/main rhythmbox 0.11.5-0ubuntu7 [3208kB]
Fetched 27.8MB in 14s (1869kB/s)                                                
(Reading database ... 114587 files and directories currently installed.)
Preparing to replace dpkg 1.14.16.6ubuntu3 (using .../dpkg_1.14.16.6ubuntu4_i386.deb) ...
Unpacking replacement dpkg ...
Setting up dpkg (1.14.16.6ubuntu4) ...

(Reading database ... 114587 files and directories currently installed.)
Preparing to replace evolution-data-server 2.22.1.1-0ubuntu3 (using .../evolution-data-server_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement evolution-data-server ...
Preparing to replace evolution-data-server-common 2.22.1.1-0ubuntu3 (using .../evolution-data-server-common_2.22.2-0ubuntu1_all.deb) ...
Unpacking replacement evolution-data-server-common ...
Preparing to replace libedataserver1.2-9 2.22.1.1-0ubuntu3 (using .../libedataserver1.2-9_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libedataserver1.2-9 ...
Preparing to replace libcamel1.2-11 2.22.1.1-0ubuntu3 (using .../libcamel1.2-11_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libcamel1.2-11 ...
Preparing to replace libebook1.2-9 2.22.1.1-0ubuntu3 (using .../libebook1.2-9_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libebook1.2-9 ...
Preparing to replace libecal1.2-7 2.22.1.1-0ubuntu3 (using .../libecal1.2-7_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libecal1.2-7 ...
Preparing to replace libedata-book1.2-2 2.22.1.1-0ubuntu3 (using .../libedata-book1.2-2_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libedata-book1.2-2 ...
Preparing to replace libedata-cal1.2-6 2.22.1.1-0ubuntu3 (using .../libedata-cal1.2-6_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libedata-cal1.2-6 ...
Preparing to replace libegroupwise1.2-13 2.22.1.1-0ubuntu3 (using .../libegroupwise1.2-13_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libegroupwise1.2-13 ...
Preparing to replace libgdata1.2-1 2.22.1.1-0ubuntu3 (using .../libgdata1.2-1_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libgdata1.2-1 ...
Preparing to replace libgdata-google1.2-1 2.22.1.1-0ubuntu3 (using .../libgdata-google1.2-1_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libgdata-google1.2-1 ...
Preparing to replace evolution 2.22.1.1-0ubuntu3 (using .../evolution_2.22.2-0ubuntu1.2_i386.deb) ...
Unpacking replacement evolution ...
Preparing to replace evolution-common 2.22.1.1-0ubuntu3 (using .../evolution-common_2.22.2-0ubuntu1.2_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace libedataserverui1.2-8 2.22.1.1-0ubuntu3 (using .../libedataserverui1.2-8_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libedataserverui1.2-8 ...
Preparing to replace libexchange-storage1.2-3 2.22.1.1-0ubuntu3 (using .../libexchange-storage1.2-3_2.22.2-0ubuntu1_i386.deb) ...
Unpacking replacement libexchange-storage1.2-3 ...
Preparing to replace libgnomeui-common 2.22.1.0-0ubuntu1 (using .../libgnomeui-common_2.22.1.0-0ubuntu2_all.deb) ...
Unpacking replacement libgnomeui-common ...
Preparing to replace libgnomeui-0 2.22.1.0-0ubuntu1 (using .../libgnomeui-0_2.22.1.0-0ubuntu2_i386.deb) ...
Unpacking replacement libgnomeui-0 ...
Preparing to replace evolution-plugins 2.22.1.1-0ubuntu3 (using .../evolution-plugins_2.22.2-0ubuntu1.2_i386.deb) ...
Unpacking replacement evolution-plugins ...
Preparing to replace libgtk-vnc-1.0-0 0.3.4-0ubuntu1 (using .../libgtk-vnc-1.0-0_0.3.4-0ubuntu2_i386.deb) ...
Unpacking replacement libgtk-vnc-1.0-0 ...
Preparing to replace libnautilus-extension1 1:2.22.2-0ubuntu6 (using .../libnautilus-extension1_1%3a2.22.3-0ubuntu2_i386.deb) ...
Unpacking replacement libnautilus-extension1 ...
Preparing to replace nautilus-data 1:2.22.2-0ubuntu6 (using .../nautilus-data_1%3a2.22.3-0ubuntu2_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:2.22.2-0ubuntu6 (using .../nautilus_1%3a2.22.3-0ubuntu2_i386.deb) ...
Unpacking replacement nautilus ...
Preparing to replace rhythmbox 0.11.5-0ubuntu6 (using .../rhythmbox_0.11.5-0ubuntu7_i386.deb) ...
Unpacking replacement rhythmbox ...
Setting up evolution-data-server-common (2.22.2-0ubuntu1) ...
Setting up libedataserver1.2-9 (2.22.2-0ubuntu1) ...

Setting up libcamel1.2-11 (2.22.2-0ubuntu1) ...

Setting up libebook1.2-9 (2.22.2-0ubuntu1) ...

Setting up libecal1.2-7 (2.22.2-0ubuntu1) ...

Setting up libedata-book1.2-2 (2.22.2-0ubuntu1) ...

Setting up libedata-cal1.2-6 (2.22.2-0ubuntu1) ...

Setting up libegroupwise1.2-13 (2.22.2-0ubuntu1) ...

Setting up libgdata1.2-1 (2.22.2-0ubuntu1) ...

Setting up libgdata-google1.2-1 (2.22.2-0ubuntu1) ...

Setting up evolution-data-server (2.22.2-0ubuntu1) ...
Setting up evolution-common (2.22.2-0ubuntu1.2) ...

Setting up libedataserverui1.2-8 (2.22.2-0ubuntu1) ...

Setting up libexchange-storage1.2-3 (2.22.2-0ubuntu1) ...

Setting up libgnomeui-common (2.22.1.0-0ubuntu2) ...
Setting up libgnomeui-0 (2.22.1.0-0ubuntu2) ...

Setting up evolution (2.22.2-0ubuntu1.2) ...

Setting up evolution-plugins (2.22.2-0ubuntu1.2) ...
Setting up libgtk-vnc-1.0-0 (0.3.4-0ubuntu2) ...

Setting up libnautilus-extension1 (1:2.22.3-0ubuntu2) ...

Setting up nautilus-data (1:2.22.3-0ubuntu2) ...

Setting up nautilus (1:2.22.3-0ubuntu2) ...

Setting up rhythmbox (0.11.5-0ubuntu7) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
hjemmeserver@hjemmeserver:~$ sudo aptitude full-upgrade
sudo: unable to resolve host hjemmeserver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
hjemmeserver@hjemmeserver:~$ 

```

---

### Post by rampageoberon on 2008-06-07
Okay it looks like it updated your system fine. I always find it much easier doing these tasks from terminal rather than the gui.

I'm not too sure why it couldn't resolve the hostname of your pc. (this was the error you got)

For filesharing support you want to use samba? Or some other P2P applications?

If it is samba you want to use there are several guides.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jocko on 2008-06-07
> **rampageoberon said:**
> Try the following code in terminal and see if that updates.

```

sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

```This is assuming you are using hardy (the earlier versions might just need upgrade and dist-upgrade respectively)

Hope that helps

I would say use apt-get instead of aptitude. aptitude may sometimes be very overzelous and remove packages that you want to keep, without asking. So I would use:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Edit: Ok, I was too late, and apparently it worked, so you can disregard this post...

---

### Post by rampageoberon on 2008-06-07
Also you might find you want to run the commands below to remove the downloaded .deb files from cache

```
sudo aptitude clean
```

or

```
sudo apt-get clean
```

And jocko has a point about aptitude removing packages without asking. I use aptitude from preference, it is upto you what you want to use.

To clean up unused dependencies i think it is (Only if you are using apt-get)

```
sudo apt-get autoremove
```

---

### Post by Shoek on 2008-06-11
I don't really care what I use. I just want the graphical thing that is in Ubuntu to work. I want Ubuntu generally to work. Why do I have to keep copying and pasting to the terminal to get my updates? Why can't I start up the login window prefferences, when it gives me no error message? When will the updates be fixed?

---

