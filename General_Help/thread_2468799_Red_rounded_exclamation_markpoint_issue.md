---
title: "Red rounded exclamation mark/point issue"
date: 2021-11-10
forum: General Help
---

### Post by Kova78 on 2021-11-10
Hi,

an annoying exclamation marks is displayed at every boot (see file attached).
All repositories (Main server) are updated and no errors are reported:

```

:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Hit:2 [http://ppa.launchpad.net/c.falco/mame/ubuntu](http://ppa.launchpad.net/c.falco/mame/ubuntu) focal InRelease                                  
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                                           
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease                 
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]
Fetched 214 kB in 1s (260 kB/s)    
Reading package lists... Done

:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal

:~$ uname -r
5.4.0-90-generic

```

Any help to get that exclamation point disappear? 
Thank you in advance

---

### Post by ActionParsnip on 2021-11-10
If you run
```

sudo apt update
sudo fullupgrade

```
Does this clear OK?

---

### Post by Kova78 on 2021-11-10
Exclamation point still there :(

```

~$ sudo apt update 
Hit:1 http://archive.canonical.com/ubuntu focal InRelease
Hit:2 http://ppa.launchpad.net/c.falco/mame/ubuntu focal InRelease                                                                             
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease                                                                                         
Get:4 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:5 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Get:6 http://archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Fetched 214 kB in 1s (199 kB/s)                                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

~$ sudo apt full-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> **ActionParsnip said:**
> If you run
```

sudo apt update
sudo fullupgrade

```
Does this clear OK?

---

### Post by Bashing-om on 2021-11-10
Kova78; Hello 

This one: [http://ppa.launchpad.net/c.falco/mame/ubuntu](http://ppa.launchpad.net/c.falco/mame/ubuntu)
Is no longer maintained - per:
[http://ppa.launchpad.net/c.falco/mame/ubuntu/dists/](http://ppa.launchpad.net/c.falco/mame/ubuntu/dists/)

I do suggest that you disable this PPA.

What now shows:
```

sudo apt update
sudo apt full-upgrade

```

[INDENT]Maybe Yes[/INDENT]

---

### Post by Kova78 on 2021-11-10
Hi, thanks for the reply.
I disabled the PPA and I ran:

```
:~$ sudo apt update 
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease                 
Hit:3 http://archive.canonical.com/ubuntu focal InRelease                      
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

:~$ sudo apt full-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So far no exclamation mark has been shown!
I think that was the issue.

Thanks a lot!

---

### Post by Bashing-om on 2021-11-10
Kova78; 

Good deal :D

If the issue now has resolution -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away[/INDENT][/INDENT]

---

### Post by Kova78 on 2021-11-11
Hi,

unfortunately the icon shown up again (see image attached)

```

:~$ sudo apt update 
Hit:1 http://archive.canonical.com/ubuntu focal InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]      
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease                         
Get:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1,344 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [562 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal-updates/main Translation-en [276 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [647 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [875 kB]
Fetched 4,032 kB in 2s (1,961 kB/s)                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

:~$ sudo apt full-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> **Bashing-om said:**
> Kova78; 

Good deal :D

If the issue now has resolution -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[INDENT][INDENT]up up and away[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2021-11-11
Kova78;

Well foooey -

Let's dig deeper - post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

see if the story lies in these.

[INDENT][INDENT]we can do that :D
[/INDENT][/INDENT]

---

### Post by Kova78 on 2021-11-12
LOL, okay

```

:~$ cat -n /etc/apt/sources.list
     1    
     2    
     3    
     4    
     5    deb http://archive.canonical.com/ubuntu focal partner
     6    deb-src http://archive.canonical.com/ubuntu focal partner
     7    deb http://archive.ubuntu.com/ubuntu focal multiverse restricted universe main
     8    deb http://security.ubuntu.com/ubuntu/ focal-security main multiverse universe restricted
     9    deb http://archive.ubuntu.com/ubuntu focal-updates main multiverse universe restricted
    10    deb http://archive.ubuntu.com/ubuntu focal-backports main multiverse universe restricted

:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/c_falco-ubuntu-mame-focal.list <==
# deb http://ppa.launchpad.net/c.falco/mame/ubuntu focal main
# deb-src http://ppa.launchpad.net/c.falco/mame/ubuntu focal main

==> /etc/apt/sources.list.d/c_falco-ubuntu-mame-focal.list.save <==
deb http://ppa.launchpad.net/c.falco/mame/ubuntu focal main
# deb-src http://ppa.launchpad.net/c.falco/mame/ubuntu focal main

```

> **Bashing-om said:**
> Kova78;

Well foooey -

Let's dig deeper - post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

see if the story lies in these.
[INDENT][INDENT]we can do that :D
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2021-11-12
Kova78; Ouch 


I see no fault with your sources.

Does the package manager have any hints ?
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT]sometimes I do wonder
[INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by Kova78 on 2021-11-13
I truly believe it's a bug.
This machine has been turned off for 6 months. After the updates, the exclamation mark started to display.

```

:~$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Hit:2 http://archive.canonical.com/ubuntu focal InRelease                      
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease                         
Get:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [562 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1,344 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [875 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [647 kB]
Fetched 3,757 kB in 2s (2,057 kB/s)                      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:~$ sudo dpkg -C
:~$ 

```

> **Bashing-om said:**
> Kova78; Ouch 


I see no fault with your sources.

Does the package manager have any hints ?
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```[INDENT]sometimes I do wonder[INDENT][INDENT]other times I just do not know
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2021-11-13
Kova78; Hummm ...

No issues seen with packages - 
Is above my skill set to advise on Why the GUI sees a fault :(

[INDENT]Just don't know
[/INDENT]

---

### Post by Kova78 on 2022-05-13
Hi,

I updated to 22.04 (from 20.04.03) and I still have the same issue:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290444&stc=1[/IMG]

Any other idea where the issue might be? :(
Thanks

---

### Post by Bashing-om on 2022-05-13
Kova78; Hey

> 
 idea where the issue might be?


Maybe we can generate some ideas :D

Post back the results of terminal commands:
```

sudo apt update
sudo apt upgrade

```

see here if a tale gets told.

---

### Post by Kova78 on 2022-05-14
Hi,

Thank you for your help.
if you scroll the thread we already tried to check the repositories. It's not the issue.
I do believe it's a bug.

Anyway, here is the output:
```
:~$ sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Thank you

---

