---
title: "Nessus"
date: 2004-11-04
forum: General Help
---

### Post by chet on 2004-11-04
Hi all first post so go easy on me please
I have downloaded nesses on a clean install of ubuntu and tried to install it with the following command  sh nessus-installer.sh, I get the error The script needs uudecode(1) to run properly, could someone help me out please as to what I need to do to get this program installed

Regards

Chet

---

### Post by lincoln on 2004-11-04
Hi Chet,

Yah, I've just started with Ubuntu, and I'm a linux n00b too...

The easy way to get nessus is at a shell -- sudo apt-get install nessusd
and sudo apt-get install nessus.

Unfortunately, whenever I try to use nessus-update-plugins (either with sudo or as root) it won't work :(.

Good luck!

Lincoln

---

### Post by mercurus on 2004-11-04
[QUOTE=lincoln]The easy way to get nessus is at a shell -- sudo apt-get install nessusd and sudo apt-get install nessus.[/QUOTE]

The Easy Way is to use Synaptic to install nessus :), but apt-get is just as effective.

[QUOTE=lincoln]Unfortunately, whenever I try to use nessus-update-plugins (either with sudo or as root) it won't work :(.[/QUOTE]

What's the problem there ? Can you tell us what the error message is ? or what symptoms of failure nessus-update exhibits ?

Cheers
mercurus

---

### Post by chet on 2004-11-04
Thanks for the replies, I have a few packages to install and wondering if I'm going to run into this probles again, the packages are 

IPSEND
Nmap
Airsnort

oh I'm not a hacker I'm doing router tests at work

Chet

---

### Post by chet on 2004-11-04
Hi all I have run apt-get and down loaded a few updates, then I have ran Synaptic to install Nmap, Airsnort, nessus and a few others, how do I put icons on the desktop to run the programs that I have installed.

Cheers all

Chet

---

### Post by chet on 2004-11-05
Oh dear was it such a stupid question

---

### Post by disposable on 2004-11-05
> oh I'm not a hacker I'm doing router tests at work

Well, keep working at it and someday you may become a great hacker, like Richard M. Stallman or Linus Torvalds.

---

### Post by chet on 2004-11-05
Strange answer, I do not want to be an hacker, I just want to run the said programs

---

### Post by chet on 2004-11-05
I have got nessus working, well in a fashion because I have to start nessusd everytime,  where would I put the line /usr/sbin/nessusd so it will start up when I boot my laptop

Thanks

---

