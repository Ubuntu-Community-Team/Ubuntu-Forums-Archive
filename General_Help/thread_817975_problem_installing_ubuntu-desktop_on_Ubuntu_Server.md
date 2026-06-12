---
title: "problem installing ubuntu-desktop on Ubuntu Server"
date: 2008-06-04
forum: General Help
---

### Post by blindmancries on 2008-06-04
I have problem while im installing ubuntu Server 8.04 LTS. I just istalled Ubuntu server and I want to have GUI for it. When I write sude apt-get update everything is ok but when I try to install it then on the end I have a some updates which cannot be updated. There are 42 updates which I cannot download. I have error like this:

Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.1.1-5_i386.deb](http://mk.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.1.1-5_i386.deb) 403 Forbiden [IP: 91.189.88.45 80]

it gives me 42 diferrent fails for each package which I cannot install it. Please help me I need it immediately.

---

### Post by zvacet on 2008-06-04
Do you have these lines in your source list

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

If you do and you still can not install desktop swich to main server by removing **mk** in front of archive.ubuntu.com in every line.

Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by blindmancries on 2008-06-05
First thanks that you are helping me, but im new on it. can you tell me how to do it plese. i just want to see this server just like in windows. with GUI there.

---

### Post by zvacet on 2008-06-05
After login type

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Then run this command

```
sudo nano /etc/apt/sources.list
```

Check that you have all lines which I posted to you in your source list.If some of them missing add it.Ctrl+x to exit and confirm(you will be asked for that) wit y and you should be out.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install ubuntu-desktop
```

If still no luck remove mk in front of archive.ubuntu.com in every line,so source list should look like one I posted to you.If I understend you correctly you are new in linux,not just in Ubuntu.If that is a case better solution for you was to install desktop version.But now when you allready have server let try to install desktop on top of it.

---

### Post by blindmancries on 2008-06-09
My friend, it seems that my problem is on Graphic card. cannot install it driver for it therefore doesnt allow me to install GNOME. 

My VGA is on-board, Intel 82845G/GL.

---

### Post by zvacet on 2008-06-09
I can be wrong,so anybody feel free to correct me,but I don´t think that graphic card have anything to do with installation of GNOME.It is possible that you can not use GNOME because you don´t have proper driver,but I don´t think that have anything with installation.Do you get any kind of errors which will indicate that you can not install GNOME because of your graphic card?

---

### Post by blindmancries on 2008-06-10
Maybe I'm wrong I dont know. Im new in Linux therefore I decided to be here and ask for help. Im trying to install GNOME but I get the same error. It doesnt download all packages of GNOME therefore I cannot start it. I tryed with KDE also but still the same, forbidden by server. When I try to start X I get error like this:

X: Cannot stat etc/X11/X (No such file or directory) aborting
xinit: Server error.

This is comming perhaps from not full installation of GNOME or KDE.

Anybody have idea what to do?? How should I fix this problem????
I need it very much and that very imeddiately.

---

### Post by blindmancries on 2008-06-10
One more think. Can I download GNOME using wget command, I think it can. Can someone please tell me from where to get.

---

### Post by zvacet on 2008-06-10
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by blindmancries on 2008-06-11
I just solve the problem. As I have mension before I had some faills and searching through internet with a command:

[HTML]sudo apt-get -y --force-yes install ubuntu-desktop[/HTML]  

I successeded to install it.

Anyway thanks for helping, now I have to go back there and try to fix Postfix and test it. Integretion to MS etc.

thanks again.

---

