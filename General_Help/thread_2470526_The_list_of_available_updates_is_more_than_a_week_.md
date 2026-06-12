---
title: "The list of available updates is more than a week old."
date: 2022-01-02
forum: General Help
---

### Post by kentaylor2525 on 2022-01-02
I have two Intel NUC computers running Ubuntu Mate 20.04 which I access with ssh or vnc. Each time I access one over ssh I get a message such as ```
[ken@taylor20 ~]$ ssh t29
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-90-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 updates can be applied immediately.

The list of available updates is more than a week old.
To check for new updates run: sudo apt update
```My question is why is the list of updates out of date if I run sudo apt update and then connect again? This has only started happening in the past few days. Here is the result of the update```
ken@t29:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal InRelease                                  
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease                          
Hit:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease                        
Hit:5 https://brave-browser-apt-release.s3.brave.com stable InRelease
Reading package lists... Done                                        
Building dependency tree      
Reading state information... Done
All packages are up to date.
```I even did that Windows thing and rebooted one of the computers Same thing.

For what it is worth, I have several Linux Mint Mate 20.2 virtual machines running. They are usually very aggressive about updating things. I get the update icon message sometimes several times a day. I have noticed that they have been silent recently regarding available updates. Could it be that the maintainers are taking some well deserved time off at the holidays? or do I have some other problem with the Ubuntu machines?

TIA,

Ken

---

### Post by schragge on 2022-01-03
> **kentaylor2525 said:**
> Could it be that the maintainers are taking some well deserved time off at the holidays?
Looks like that. See also [thread=2470484]Ubuntu package server not modified[/thread].

---

### Post by kentaylor2525 on 2022-01-03
Thanks schragge!

---

### Post by kentaylor2525 on 2022-01-04
The maintainers are back and the updates are flowing!

---

### Post by deadflowr on 2022-01-04
So I had to dig back a little as I remember a similar thread which has the same Message of updates being available,
when in fact the system has been updated.
Here: [https://ubuntuforums.org/showthread.php?t=2466505]("https://ubuntuforums.org/showthread.php?t=2466505")
See if that gives any help or a better understanding of what's happening.
As far as that goes.

---

