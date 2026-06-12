---
title: "Burning files from network drive"
date: 2008-06-12
forum: General Help
---

### Post by pavanmaverick on 2008-06-12
First off, I have to admit that I am a total Linux/Ubuntu nOOb. That being said, I am trying to burn a DVD from some data I have on a Network share.
1. When I try the CD/DVD creator (on Nautilus), dragging and dropping the files from the network drive to the DVD gives me the following error: Operation not supported by backend.

2. Then I tried Brasero. Brasero adds the files/folders from the network drive to the DVD project, but when I click on "Burn," it says to wait while it completes some operation. Which it never does.

3. Finally I tried GnomeBaker. Again, cannot add the files and folders from the network drive.

So, my question is whether its possible, at all, to directly burn files from the network drive, or do I HAVE to copy them over locally before burning them?
Thanks.

---

### Post by prince_niceguy on 2008-06-12
Use k3b. You can install it from the repos. It is kde program but by far I feel that it is best. 

BTW how have you mounted your network drivers? samba or nfs?

---

### Post by pavanmaverick on 2008-06-12
Thanks. I will try k3b.

The network drive was mounted with samba.

---

### Post by pavanmaverick on 2008-06-16
Okay, tried k3b as well. Same result. k3b says that the files are non-local, and are not supported. Any way to do this?

---

### Post by prince_niceguy on 2008-06-16
is the network drive based on linux?  I have a NAS and I am able to burn from it without issue. I have it mounted using nfs though. Can you put your fstab for reference.

---

### Post by pavanmaverick on 2008-06-16
Will post the fstab when I reboot into Ubuntu. The way I am connecting to the NAS is by clicking on the "Places > Connect to server"
There, I choose Windows as the type and enter my username and password when prompted.

---

### Post by cariboo on 2008-06-16
I used to use an application call WebCDWriter there are instructions on how to install it on Hardy here:

[COLOR="Yellow"]
[http://joerghaeger.de/webCDwriter/ubuntu-8.04.html](http://joerghaeger.de/webCDwriter/ubuntu-8.04.html)[/COLOR]

Jim

---

### Post by prince_niceguy on 2008-06-16
OK.. so you are manually connecting every time... I would recommend mounting it as smbfs in fstab and then you see it as one of your folders as if local and then burn using any application that you prefer.

---

### Post by eftifz on 2008-09-27
Hi, locate your network share in /home/yourusername/.gvfs/ and drag files to any burning app ^_^

---

