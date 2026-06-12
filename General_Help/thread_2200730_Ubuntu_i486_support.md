---
title: "Ubuntu i486 support"
date: 2014-01-20
forum: General Help
---

### Post by h.hittini on 2014-01-20
Hello everyone,

I have an old machine and it has an i486 processor
I struggled a lot with the old versions of Ubuntu, so, I decided to use a newer version
After doing some research I found that Ubuntu 10.10 is the last version supporting i486 architecture
My question is: Is it possible to run a recent version of Ubuntu (12.04 i.e.) if I installed an old kernel (2.6.34 i.e.)

Thanks in advance

---

### Post by tgalati4 on 2014-01-20
It is possible, but it would require a lot of effort on your part.  Try Tiny Core linux and see if that runs.  [http://tinycorelinux.net/welcome.html](http://tinycorelinux.net/welcome.html)

An alternative is to install 10.10 server on it and play around with some web services.  Although 10.10 is not supported anymore, you can probably get some use out of the machine for internal use--not facing the web.

---

### Post by mastablasta on 2014-01-21
it would be better to use 10.04 then since it still has support for some packages (but not desktop) until 2015. Server is still supported.

i would go with other distributions such as DSL (also has issue since kernel is no longer pathced or is patched irregulary), older Red hat (CentOS) might also work. or perhaps Slitaz has 486 support (hard to say). 

the biggest issue will be the CPU power. it might be used as server. or to play old DOS games :-D

---

### Post by jeanjd63 on 2014-01-21
Hello

You can try this [version non-pae]("http://people.canonical.com/~diwic/12.04-nonpae/ubuntu-12.04-desktop-i386-nonpae.iso") 12.04.

Bye

---

### Post by h.hittini on 2014-01-21
> **tgalati4 said:**
> It is possible, but it would require a lot of effort on your part.  Try Tiny Core linux and see if that runs.  [http://tinycorelinux.net/welcome.html](http://tinycorelinux.net/welcome.html)

An alternative is to install 10.10 server on it and play around with some web services.  Although 10.10 is not supported anymore, you can probably get some use out of the machine for internal use--not facing the web.

Thank you, I need to use Ubuntu or Xubuntu. So, I will try Ubuntu Server 10.04, apparently it's supported until April 2015
But in case that didn't work well with my system, I don't mind putting some effort
How can I use a recent version of Ubuntu on my machine?

---

### Post by h.hittini on 2014-01-21
> **mastablasta said:**
> it would be better to use 10.04 then since it still has support for some packages (but not desktop) until 2015. Server is still supported.

i would go with other distributions such as DSL (also has issue since kernel is no longer pathced or is patched irregulary), older Red hat (CentOS) might also work. or perhaps Slitaz has 486 support (hard to say). 

the biggest issue will be the CPU power. it might be used as server. or to play old DOS games :-D

Thank you
But I need to run Ubuntu or Debian and I guess the CPU will run okay; I'm using the machine for research
I'm gonna be removing the VGA card, using the command line, removing unwanted software and disabling unnecessary services

---

### Post by h.hittini on 2014-01-21
> **jeanjd63 said:**
> Hello

You can try this [version non-pae]("http://people.canonical.com/~diwic/12.04-nonpae/ubuntu-12.04-desktop-i386-nonpae.iso") 12.04.

Bye
Oh this is an interesting version
I'm gonna try it soon
Thank you

---

### Post by mastablasta on 2014-01-21
it means you do not want to have desktop installed. in which case server or mini.iso (net install). kernel needs to support you CPU among others. anb anythign modern might run really slow on 486...

---

### Post by h.hittini on 2014-01-21
> **mastablasta said:**
> it means you do not want to have desktop installed. in which case server or mini.iso (net install). kernel needs to support you CPU among others. anb anythign modern might run really slow on 486...

Is there a difference between minimal installation and server installation?

---

### Post by mastablasta on 2014-01-22
yes - Ubuntu minimal doesnt' have any services preinstalled. it's just a barebones system. you can then install whatever services you wan't on it:
a quick guide: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
another guide: [URL="http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html"]http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html
[/URL]
server on the other hand is out of thebox server CLI install. it will have all the stuff you ever wanted for a server (server packages) and it will preinstall it.

---

### Post by h.hittini on 2014-01-22
Thank you all :)

---

### Post by jeanjd63 on 2014-01-22
For information, what where the solution ?

---

### Post by h.hittini on 2014-01-22
I actually installed Ubuntu Server 10.04 LTS using VMWare and when I tried to boot using the old machine I get a blank screen after bios, it stays for three seconds and then the machine reboots
I guess this is the same problem I posted here [http://ubuntuforums.org/showthread.php?t=2200814](http://ubuntuforums.org/showthread.php?t=2200814)
but still no reply :(

---

### Post by h.hittini on 2014-01-22
UPDATE!
I installed this kernel [http://www.roboard.com/Files/RB-100/linux-image-2.6.34.10-vortex86-sg_1.2_i386.zip](http://www.roboard.com/Files/RB-100/linux-image-2.6.34.10-vortex86-sg_1.2_i386.zip)
And then the machine (RB-110) booted successfully; I got some error messages but I'll deal with them later
The ethernet didn't work at the beginning but I edited "/etc/network/interfaces" and replaced eth0 by eth1 according to this guide [http://ubuntuforums.org/showthread.php?t=1770659](http://ubuntuforums.org/showthread.php?t=1770659)
and it works now
Please note that the kernel came on the server be default was 2.6.32-38-generic-pae
Thank you folks

---

### Post by h.hittini on 2014-02-03
A complete guide [http://ubuntuforums.org/showthread.php?t=2203395](http://ubuntuforums.org/showthread.php?t=2203395)

---

