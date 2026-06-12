---
title: "System slow boot &quot;1min 783ms upower.service"
date: 2017-01-23
forum: General Help
---

### Post by aviator1 on 2017-01-23
Many thanks to a forum member for help thus far.

About 3 weeks ago, my boot up time went from 30 seconds to 120 seconds. I  also noticed that my email program, Thunderbird looked different when I  opened it. the folders were a light green and the fonts were much  smaller. Almost like I had changed screen resolution. 

The issues seemed to resolve themselves.

Then I began getting an error during updates.

My internet connection is fine.

Our forum colleague had me run some things from terminal, but nothing helped.

Can anyone else shed any light on any of these issues.

Thanks for any assistance.

---

### Post by #&amp;thj^% on 2017-01-24
Good Day to you.:)
Well lets see if I can be more helpful here:
Post back the info from this:
```
systemctl status upower.service
```
No promise's but we will give it the "Old College Try"
And while we are at it...post this back also if you would:
```
systemd-analyze critical-chain upower.service
```

---

### Post by aviator1 on 2017-01-24
Good day to you, also.

Here is the info.

```
dave@dave-desktop:~$ systemctl status upower.service
&#9679; upower.service - Daemon for power management
   Loaded: loaded (/lib/systemd/system/upower.service; disabled; vendor preset: 
   Active: active (running) since Tue 2017-01-24 11:56:30 CST; 5min ago
     Docs: man:upowerd(8)
 Main PID: 1722 (upowerd)
   CGroup: /system.slice/upower.service
           &#9492;&#9472;1722 /usr/lib/upower/upowerd

Jan 24 11:55:29 dave-desktop systemd[1]: Starting Daemon for power management...
Jan 24 11:56:30 dave-desktop systemd[1]: Started Daemon for power management.
lines 1-10/10 (END)
```

```
dave@dave-desktop:~$ systemd-analyze critical-chain upower.service
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

upower.service +1min 1.012s
&#9492;&#9472;basic.target @912ms
  &#9492;&#9472;sockets.target @912ms
    &#9492;&#9472;snapd.socket @909ms +1ms
      &#9492;&#9472;sysinit.target @898ms
        &#9492;&#9472;swap.target @898ms
          &#9492;&#9472;dev-disk-by\x2duuid-80d61814\x2dfc43\x2d4c38\x2db772\x2dd32945f6b4a1
            &#9492;&#9472;dev-disk-by\x2duuid-80d61814\x2dfc43\x2d4c38\x2db772\x2dd32945f6b4
lines 1-11/11 (END)
```

Thanks for your assistance

---

### Post by #&amp;thj^% on 2017-01-24
Well I think we found the problem:
```
dev-disk-by\x2duuid-80d61814\x2dfc43\x2d4c38\x2db772\x2dd32945f6b4a1
dev-disk-by\x2duuid-80d61814\x2dfc43\x2d4c38\x2db772\x2dd32945f6b4
```
Now I have to find a solution for this... and this will take a little time here so bear with me.:)

---

### Post by aviator1 on 2017-01-24
Thanks. Take your time. I will be out for a while.

Regrds.

---

### Post by aviator1 on 2017-01-24
Part of the problem is fixed.

I had a thumb drive in one of the USB ports to transfer some files.

I removed the thumb drive and boot up is fine.

However, I am still having the updater problem.

```
dave@dave-desktop:~$ sudo apt update
[sudo] password for dave: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:3 http://archive.canonical.com xenial InRelease                            
Hit:4 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease    
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Ign:6 http://www.openprinting.org/download/printdriver/debian lsb3.2 InRelease 
Ign:7 http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial InRelease
Hit:8 http://www.openprinting.org/download/printdriver/debian lsb3.2 Release   
Hit:9 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:10 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial InRelease        
Err:12 http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release
  404  Not Found
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [457 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [449 kB]
Ign:15 http://dl.google.com/linux/chrome/deb stable InRelease
Get:16 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]
Get:17 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [384 kB]
Get:19 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,434 B]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [379 kB]
Reading package lists... Done                          
W: http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg: Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)
E: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
dave@dave-desktop:~$ 
```
I

---

### Post by aviator1 on 2017-01-24
I may have accidentally solved the issue. I was searching for similar problems and came across an instruction to check system/software & updates/other software. Not sure if is it correct.

I unchecked the following. 
**[http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu)** xenial

I can run sudo apt udate and get these results:

```
dave@dave-desktop:~$ sudo apt update
[sudo] password for dave: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release
Hit:3 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease
Hit:5 http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
dave@dave-desktop:~$ 
```

---

### Post by #&amp;thj^% on 2017-01-24
> **aviator1 said:**
> Part of the problem is fixed.

I had a thumb drive in one of the USB ports to transfer some files.

I removed the thumb drive and boot up is fine.



You know I was just about to ask if there was another Disk USB or thumb drive attached at boot time.
Great detective work and good job.:)
> **aviator1 said:**
> I may have accidentally solved the issue. I was searching for similar problems and came across an instruction to check system/software & updates/other software. Not sure if is it correct.

I unchecked the following. 
**[http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu)** xenial


Yep as suggested yesterday in your other thread.
Isn't it nice to self learn and fix small problems as they crop up..:)
Best Regards

---

### Post by aviator1 on 2017-01-24
I really, really appreciate the time you took to help me out.

I am a long time user, but still relatively unfamiliar with the actual software workings and commands.

Your instructions and suggestions were very good.

I hope you have a blessed day, and that our paths will cross again sometime.

Kind Regards.

(I will mark this as solved)

---

### Post by #&amp;thj^% on 2017-01-24
> **aviator1 said:**
> I really, really appreciate the time you took to help me out.

I am a long time user, but still relatively unfamiliar with the actual software workings and commands.

Your instructions and suggestions were very good.

I hope you have a blessed day, and that our paths will cross again sometime.

Kind Regards.

(I will mark this as solved)

Your Very Welcome! I'm sure we will see each other around here...Long Time member here (10Years Plus) Just a new user name.;)
Thanks for the very kind words.
Until Next Time;)

---

