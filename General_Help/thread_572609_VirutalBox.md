---
title: "VirutalBox"
date: 2007-10-10
forum: General Help
---

### Post by jdm2 on 2007-10-10
I am trying to get virtaulbox working, but it is saying something about a kernel probelm.  I am running ubuntu dapper right now.  I will upload an image of the output and a text file that says what to look at.  Can you help me?  Thanks

---

### Post by Pumalite on 2007-10-10
Maye you need:

sudo apt-get install build-essential

---

### Post by jdm2 on 2007-10-10
Here is the output for that:  

jdm@jdm-desktop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jdm@jdm-desktop:~$

---

### Post by Pumalite on 2007-10-10
Check your kernel headers and make sure they coincide with your kernel version.
Kernel-headers you can check in Synaptic
Kernel version:
uname -r

---

### Post by jdm2 on 2007-10-10
I don't know where you are talking about, in a program called sysinfo it tells me that the kernel is:

2.6.15-29-386

The virtaul box is version 1.5.0-24069-1_Ubuntu_dapper

Does that help any?

---

### Post by Pumalite on 2007-10-10
To compile a kernel one needs a kernel-source or kernel-headers.
(it might be already installed through build-essential)

---

### Post by jdm2 on 2007-10-10
How do I check that and if it is already installed then what do I need to do?  Thanks for the help.

---

### Post by Pumalite on 2007-10-10
Have you installed a graphics driver successfully?

---

### Post by bodhi.zazen on 2007-10-10
LOL

I can't stand it any more, stop the torture :

```
sudo apt-get install linux-headers-`uname -r`
```

Note those are back tics ` by the number 1 and not single quotes '

---

### Post by Pumalite on 2007-10-10
Thank you. I learn everyday. I try to help, but I'm learning like the rest.

---

### Post by jdm2 on 2007-10-10
Here is the output for the terminal command  sudo apt-get install linux-headers-`uname -r`


jdm@jdm-desktop:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-29
The following NEW packages will be installed:
  linux-headers-2.6.15-29 linux-headers-2.6.15-29-386
0 upgraded, 2 newly installed, 0 to remove and 34 not upgraded.
Need to get 7763kB of archives.
After unpacking 79.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-29 2.6.15-29.60 [6908kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-29-386 2.6.15-29.60 [855kB]
Fetched 7763kB in 41s (185kB/s)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::SpacerItem', <> line 2 during global destruction.
Selecting previously deselected package linux-headers-2.6.15-29.
(Reading database ... 182924 files and directories currently installed.)
Unpacking linux-headers-2.6.15-29 (from .../linux-headers-2.6.15-29_2.6.15-29.60_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-29-386.
Unpacking linux-headers-2.6.15-29-386 (from .../linux-headers-2.6.15-29-386_2.6.15-29.60_i386.deb) ...
Setting up linux-headers-2.6.15-29 (2.6.15-29.60) ...

Setting up linux-headers-2.6.15-29-386 (2.6.15-29.60) ...

---

### Post by bodhi.zazen on 2007-10-10
> **Pumalite said:**
> Thank you. I learn everyday. I try to help, but I'm learning like the rest.

Aren't we all (learning that is ?)

No problem, no offense intended. Your time and help is appreciated.

---

### Post by jdm2 on 2007-10-10
It is working now, but it says I need to add myself to the vboxusers group.  How do I do this?  Thanks for the help.

---

### Post by nike984 on 2007-10-10
8 out 10, VirtualBox kernel problem can be solved by using these 3 command.

```
sudo aptitude install linux-headers-$(uname -r)
sudo dpkg-reconfigure virtualbox
sudo /etc/init.d/vboxdrv setup

```

To add vboxusesr to your account, go to 
System -> Administration -> Users and Groups. 
Click on **Manage Groups** button on the right. 
Scroll down until you see **vboxusers** in the list
Click on **Vboxusers** and click **Properties** button on the right. 
You’ll see a screen as shown below with the list of users. 
Check the users to whom you want to give access to Virtualbox. 
Click OK and close the boxes

That's all :)

---

### Post by jdm2 on 2007-10-10
Thank you for your help.  I got it to work.

---

### Post by Rohen on 2008-05-20
Man I've tried everything you guys have posted, used the terminal, re-installed and uninstalled... that kernel message keeps popping up :(

What am I doing wrong?  I use Hardy on my SONY VAIO.

Why is it that when I run:
[I]
sudo dpkg-reconfigure virtualbox[/I]

I get the message: "virtualbox not installed"

---

### Post by Rohen on 2008-05-20
Finally got it running... had to download and install it via terminal... seems like the repos version is broken or something.

BUT... I am now getting this weird message :(

Damn this. lol

---

