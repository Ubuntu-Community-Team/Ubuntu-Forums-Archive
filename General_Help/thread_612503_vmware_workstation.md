---
title: "vmware workstation"
date: 2007-11-14
forum: General Help
---

### Post by anemptygun on 2007-11-14
I managed to get ahold of a copy of vmware workstation 6. Now I'm not quite sure how to install it. There is a script file in the installer folder that I tried to run, but it seemed to not do anything. I have included a pic of my files.

---

### Post by Prospero2006 on 2007-11-14
VirtualBox is a great emulator that works just like vmware. 
I used to use vmware extensively, but I've found that VirtualBox is much easier.

Pros

---

### Post by toupeiro on 2007-11-14
I am a VMWare workstation 6 user.

first.  you have to run that vmware-install.pl perl script as root.  But, before you do, make sure you have the kernel source downloaded for your currently running kernel, because it will ask for it as I remember.  No need to do NAT'ing in most cases, but answer the questions based on your setup.

It helps if you change the GID of the hardware devices you want rwx access to through your guest machine to your GID.  This may not be as big of a factor with later Linux kernels, but I happen to run a 2.4 kernel at work so this greatly eases some of the administrative overhead.

btw.. vmware workstation 6 is not free :)  you will need a license to start your virtual machine.

---

### Post by nnamdi on 2007-11-14
i have used both and i think virtual box is better consume less resources and easy to configure simply use your synaptic and u will get it

---

### Post by anemptygun on 2007-11-14
Well I will try out VirtualBox first then and see how that works out, and I'll get back to you guys!:KS

---

### Post by anemptygun on 2007-11-14
Sorry, I must be missing it. I cannot find VirtualBox in the add/remove programs or synaptic.

---

### Post by anemptygun on 2007-11-17
anybody out there...

---

### Post by veloce on 2007-11-17
> **anemptygun said:**
> anybody out there...

I suspect that the virtual box people aren't reading "vmware workstation" threads.

There are **many** sets of instructions for setting up virtual box. Seek and ye shall find.

I use vmware server.  To install this in Gutsy:

1. download shell installation script from [www.vmware.com](www.vmware.com) and get a license key (both are free)

2. install dependencies:  sudo apt-get install build-essential xinetd

3. run downloaded install script - default answers for all questions should be fine.

---

### Post by zvacet on 2007-11-18
[https://help.ubuntu.com/community/VMware/Workstation]("https://help.ubuntu.com/community/VMware/Workstation")

---

### Post by cytg on 2007-11-19
You all seem to be praising virtualbox alot .. i've used it too, and i can crash it almost on command with winxp .. just do a little intensive debugging and memory reads and it'll fall flat within the minute (for me anyway) .. so im giving vmware a try.. that is if i can get it installed !!

---

### Post by fjgaude on 2007-11-19
> **cytg said:**
> You all seem to be praising virtualbox alot .. i've used it too, and i can crash it almost on command with winxp .. just do a little intensive debugging and memory reads and it'll fall flat within the minute (for me anyway) .. so im giving vmware a try.. that is if i can get it installed !!

I've been using vmware server and virtualbox for months and I must say that vmware is better if you need all of its features.

To install is a snap, just follow velcoe's suggestions. Works every time. I've used my same license over and over on different machines and it works. I've reused vmx build for 32-bit and they work in 64-bit, etc. All seems mature, at least to me.

---

### Post by anemptygun on 2007-11-20
i was really just looking for something to use to play cs:s in, which would accomplish that better?

---

### Post by veloce on 2007-11-20
> **anemptygun said:**
> i was really just looking for something to use to play cs:s in, which would accomplish that better?

if that's a game requiring 3d graphics then vmware server will NOT do the job.  Only vmware workstation (non-free) does 3d.

I have no knowledge of virtualbox' abilities.

---

### Post by anemptygun on 2007-11-22
> **veloce said:**
> ...vmware server will NOT do the job...
I was aware of this. I was just curious about the differences between virtualbox and vmware workstation.

---

### Post by anemptygun on 2007-11-24
never mind I see that virtualbox has no 3d acceleration support.

---

### Post by anemptygun on 2007-11-24
Btw i found out how i needed to install vmware workstation.  I needed to run the perl script inside the terminal as a super user. Here is how I installed it if anyone wants to know.

[http://www.vmware.com/support/ws5/doc/ws_install_linux.html](http://www.vmware.com/support/ws5/doc/ws_install_linux.html)

(I used the tar method)


p.s. I will post any problems here.

---

