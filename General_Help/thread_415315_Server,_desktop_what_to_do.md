---
title: "Server, desktop what to do"
date: 2007-04-20
forum: General Help
---

### Post by borahshadow on 2007-04-20
Ok I was not sure where to post this so sorry if it is in the wrong spot.
I don't know weather to use the server the desktop or the alternate install. here are my circumstances

I just built a new computer it has an ECS GeForce6100Sm-M mother board(I don't know why they named the mother board after the integrated graphics chipset)and an AMD 64 X2 3600+ with 1 GB DDR2 Ram 2 250Gb SATA harddrives and a dvdburner. The two harddrives will be on a RAID 1

The Goal of this Computer in to be a fileserver for my house which at any time would have less than 5 users using it (i know overkill but it was a steal). But I also do some webdesign and I like to have a local webserver that serves my home network so this will also function as that. It will be serving a printer on the network also. and I plan on using it to serve vm(s) from vmware server.

So as you can see this is a pretty multi purpose machine but it actually does not completely stop there it will need a GUI because it will serve Vm(s) to the network but my mom will actually beusing it as a workstation.
Before people start yelling and saying do not mix workstations and servers this is the deal it is serving <5 users my mom does not use the computer superfrequently and most of her programs will be on a vm she might use linux for the Gimp or openoffice and even then she won't use it frequently

Ok now that I have  provided background about my setup or wanted setup here is my question.  I asked my friend who is pretty good with linux and maintains a bunch of servers and he said he would install the desktop and then manually install LAMP (webserver) components rather then the server install which will install a LAMP server for you but then you have to install GUI, GIMP, open office, firefox, utilities etc. and i agreed.  But from what I read and from experimenting with the livecd you need the alternate installer for RAID setup not the desktop or server unless you installed and then RAIDED it. 

I was also wondering which version of ubuntu to use 6.06 LTS 6.10 or the new feisty 7.04 I was leaning to 7.04
ps Why does 6.06 have Long term support why did they decide to do that?
pps. Where do the version #s come from why is one 6.06 and the next 6.10 and the next 7.04?

I was reading about the new features of Feisty and it said > Ubuntu 7.04 Server Edition adds support for hardware facilities that speed up the use of virtual machines as well as other improved hardware support, making it an excellent choice as a web, database, mail, file and print server, the fastest growing area of Linux server use. 
From what That says it sounds like only the server edition has that support but I thought they were all about the same
But then
> Kernel
Virtualization support: KVM (the Kernel-based Virtual Machine) is included in Ubuntu 7.04, which takes advantage of the virtualization capabilities of recent Intel and AMD processors. Each virtual machine has private virtualized hardware: a network card, disk, graphics adapter, and so on. 

The 7.04 kernel is also VMI enabled, for improved performance when running on VMware hypervisors. VMI paravirtualization can be enabled in VMware Workstation 6.0 beta. 

That sounds like it is in all the editions (in the kernel) but will only help with Vmware Workstation I will be using VMware Server 
ps. My CPU does have Support for the virtualization Technology support

I don't know much about the alternate  does it install a GUI and desktop programs like the desktop does can it setup a LAMP server? is it the only one with RAID support during the install? etc.

from what I can read it sounds like I need the Alternate but I don't know

sorry for any mistakes with my english I tried to make it easy to read and understand

Thanks in advance I want to start configuring this and hopefully have it mostely installed and running by tonight (my mostely Imean raid working core installed and GUI with al the programs installed and hopefully Vmware and then Ican configure things like Samba Shares tomorrow

---

### Post by zvacet on 2007-04-20
Desktop and server are available in Live and alternate version.If you want to use your comp as server then install server and after that you can install GUI with command 

```
sudo aptitude install ubuntu-desktop
```

If you want GNOME or

```
sudo aptitude install kubuntu-desktop
```

If you are for KDE

Of course it is possible to install desktop and after that to install LAMP.First option looks more elegant,but that doesn´t mean second one is bad or wrong.

---

### Post by trailrunner13 on 2007-04-21
I installed unbuntu-7.04-server-amd64.iso on my machine (AMD Athlon 64 X2 4200+). Planning to stand-up an Asterisk server and a Mediawiki instance. But I also wanted a GUI. I've looked around using Aptitude and don't see any GNOME files. After seeing this post, I went ahead did a ```
sudo aptitude install ubuntu-desktop
```, but of course no packages were found. Are the desktop packages part of the 64 bit server build I downloaded / installed? Thanks in advance for any advice.
:confused:

---

### Post by trailrunner13 on 2007-04-21
Okay, so after further digging (and some useful prompts from Debuan @ the CLI), I realized I needed to edit [FONT=Lucida Console]/etc/apt/sources.list to enable the Universe repositories. However, my [/FONT][FONT=Lucida Console]/etc/apt/sources.list doesn't have anyting to edit: ```
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
```[/FONT]
Nothing there to edit per the advice in [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/extra-repositories.html). Can I just vi that file, add in the lines showing at this link or what?

---

### Post by zvacet on 2007-04-21
Do exactly as server guide told you to do.Edit /etc/apt/sources.list and add lines in the bottom of the page.After that you can run
```
sudo aptitude update 
```

to refresh your source list.When you are done with that install ubuntu desktop.

---

### Post by trailrunner13 on 2007-04-21
Well... I made the changes to sources.list. Tried with both
```
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

```
and
```
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse

```
Aptitude clearly updates its package list for both configs. When I go into the Aptitude GUI, I can see "New Packages" and can find a whole stack of GNOME stuff in it. But when I execute
```
sudo aptitude install ubuntu-desktop
```
I get an output that says
```
Couldn't find any package whose name or description matched "ubuntu-desktop"
```
I have also gone in through Aptitude UI and flagged the whole GNOME list and Aptitude says that 460 packages are broken due to dependencies. Clearly, I'm still doing something incorrectly.

---

### Post by mhansen on 2007-04-21
> **borahshadow said:**
>   I asked my friend who is pretty good with linux and maintains a bunch of servers and he said he would install the desktop and then manually install LAMP (webserver) components 

I'd have your friend do this.  Really, 5 people is nothing, relatively speaking.  


Regards,
Mike

---

### Post by trailrunner13 on 2007-04-25
So, I finally gave up on trying to pull in GNOME from the text version of Aptitude or via apt-get on the CLI.  I reformatted the HDD partition where I had installed Ubuntu Server, then installed Ubuntu Desktop on that partition instead.  Getting it installed was a bit of a nightmare, but OT for this thread.  Thanks anyway for trying to sort me out.

---

### Post by JoxBG on 2007-05-12
> **trailrunner13 said:**
> Well... I made the changes to sources.list. Tried with both
```
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

```
and
```
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse

```
Aptitude clearly updates its package list for both configs. When I go into the Aptitude GUI, I can see "New Packages" and can find a whole stack of GNOME stuff in it. But when I execute
```
sudo aptitude install ubuntu-desktop
```
I get an output that says
```
Couldn't find any package whose name or description matched "ubuntu-desktop"
```
I have also gone in through Aptitude UI and flagged the whole GNOME list and Aptitude says that 460 packages are broken due to dependencies. Clearly, I'm still doing something incorrectly.

Why are you mixing your versions. Feisty is 7.04, Dapper is 6.06. Remove the dapper lines from your sources.list.

---

