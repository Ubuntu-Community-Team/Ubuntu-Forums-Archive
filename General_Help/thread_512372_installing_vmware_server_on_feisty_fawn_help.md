---
title: "installing vmware server on feisty fawn help"
date: 2007-07-29
forum: General Help
---

### Post by sarahsilverman on 2007-07-29
im stuck on tar -xzf /Path/To/VMware-server-1.0.3-xxx.tar.gz, i try to enter the path to it but i don't get it. i do file system/home/jonathan/desktop/vmware-server-1.0.3-44365, and everything in between. i don't know whats wrong, i don't know how to correctly write the path. you see i just switched from windows to ubuntu.

the tutorials site i am following is [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

thank you thank you thank you soo much any help is greatly appreciated:popcorn:

i wish there was like something on this site that i could reward the person with, like ubuntu forum gold or cash.

*********************************************************************SOLVED**************************************************

---

### Post by forestpixie on 2007-07-29
to use the file you've downloaded - where has it downloaded to?

if its on your desktop - then  the path would have to have Desktop (with uppercase D) in it

try to 
```

cd Desktop
``` 

at your home prompt and then run the tar command from there

if you've just arrived from windows a lesson I learnt early is that Linux is case sensitive  

desktop is different than Desktop

x11 is not the same as X11 - that caused me problems :)

 it helps if you post the actual errors you get from terminal

---

### Post by sarahsilverman on 2007-07-29
oh thank you thank you thank you, but now i am having trouble running the installer. "sudo vmware-install.pl" , the output is "sudo: vmware-install.pl: command not found"

thank you so much :popcorn:

---

### Post by breuerp on 2007-07-29
Try:
```
sudo ./vmware-install.pl
```

---

### Post by sarahsilverman on 2007-07-29
this is the output :
 "A previous installation of VMware software has been detected.

Failure

Execution aborted."

i think what it detected is the vmware player in ubuntu, it only plays virtual machines. i uninstalled it, i don't know what its talking about. can you guys help me on this? this is a screenshot :[http://img409.imageshack.us/my.php?image=screenshotei9.png](http://img409.imageshack.us/my.php?image=screenshotei9.png)

do i need to uninstall this in order for it to work?

thank you i really appreciate this help:popcorn:

right on popcorn:KS

---

### Post by forestpixie on 2007-07-29
you might need to purge vmware-player (if that's what you had installed)

in synaptic if you click status - are there any residual configurations

if there are uninstall those and try again 

the command to purge would be - for vmware-player

```
sudo apt-get remove --purge vmware-player
```

---

### Post by sarahsilverman on 2007-07-29
i think i might have to restart, im going to check in after. thank you.

this is what i mean jelly bean:KS

:popcorn:

---

### Post by sarahsilverman on 2007-07-29
the same error message occured

A previous installation of VMware software has been detected.

Failure

Execution aborted.

is there any possible way i can force ubuntu to install vmware. i really need this and i don't want to go back to windows. thank you i really appreciate you guys staying with me.:popcorn:

---

### Post by forestpixie on 2007-07-29
try running this is terminal

```
cd /etc/vmware
```

if you get a hit - you need to get rid of it apparently


[http://ubuntuforums.org/showthread.php?t=445571](http://ubuntuforums.org/showthread.php?t=445571)

---

### Post by sarahsilverman on 2007-07-29
> **forestpixie said:**
> try running this is terminal

```
cd /etc/vmware
```

if you get a hit - you need to get rid of it apparently


[http://ubuntuforums.org/showthread.php?t=445571](http://ubuntuforums.org/showthread.php?t=445571)
ooh how do i remove the folder? thank you, i have a good feeling this is the problem.:guitar:

---

### Post by sarahsilverman on 2007-07-29
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 

this is the output, where do i install the binary files?

---

### Post by forestpixie on 2007-07-29
in terminal this will remove the /etc/vmware directory and files

sudo rm -r /etc/vmware

---

### Post by forestpixie on 2007-07-29
> **sarahsilverman said:**
> Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 

this is the output, where do i install the binary files?

 I am not at all sure - I was under the impression it was in the repositories - that would be a whole lot easier to install

> **veloce said:**
> vmware-server is now in the Feisty repositories - the commercial one.  Easiest way to install - sorts the kernel modules for you.

---

### Post by sarahsilverman on 2007-07-29
:KSTHANK YOU I LOVE YOU ALL I SUCCESSFULLY DID IT WITH A LOT OF YOUR GUYS HELP AND INSTRUCTION :KS

:popcorn::guitar::guitar::popcorn:

---

### Post by AllenGG on 2007-07-29
Watching this with great interest. Note to Sarahsilverman, go to Synaptic, use the "search" feature, under "name" type [COLOR=Red]vmware  [COLOR=Black]you'll get a lot of useful output.

Now, the catch is : what to install ?
in a terminal window type: uname -a  this will give you the 'kernel version' (you're running)

start there, please keep us posted, 
Allen
[/COLOR][/COLOR]

---

### Post by forestpixie on 2007-07-29
excellent - well done and enjoy :D

Edit - go to your first post - thread tools and mark it as solved for other people :)

---

### Post by AllenGG on 2007-07-29
wow, fast, tell all the steps and use please..............

---

### Post by breuerp on 2007-07-29
This site is definitely the easiest way to install VMWare:

[HTML]http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html[/HTML]

I've tested it with VMWare Server 1.0.3 using Feisty.

Cheers

---

### Post by dorath on 2007-08-23
> **forestpixie said:**
> in terminal this will remove the /etc/vmware directory and files

sudo rm -r /etc/vmware

You are my hero.

---

### Post by nqsonk9 on 2007-08-26
Guys, I'm totally new to VMware server. I've just installed it successfully in the sources way, but my VMware server cant play even one virtual machine !

It displayed the black screen for 5-6s then turn back to suspend state, what've i done wrong ? Pros, pls help :((

---

