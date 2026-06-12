---
title: "HP Proliant DL320 G2 Fan Speed"
date: 2007-08-09
forum: General Help
---

### Post by phillips321 on 2007-08-09
[COLOR="DarkRed"]**This post is old, please don't use it. Instead, refer to the latest version [available here]("http://ubuntuforums.org/showthread.php?p=8920092#post8920092").**[/COLOR]

Hi guys,

I have the above server and i'm trying to install ubuntu on it, i have everything working perfectly other than the fan speed.

It seems like all fans are maxed out at 100%, what do i need to install to allow the fan speed to scale to the cpu/sys temp?

Cheers

P.s. I've googled this a fair bit but it's proving hard to find

                    *******************************
************** SOLVED **** READ BELOW **************
                    *******************************

After spending ages trying to sort this out i finally figured it out :)

I downloaded the [ProLiant Support Pack for Red Hat Enterprise Linux 4]("http://h18023.www1.hp.com/support/files/server/us/download/27022.html") file from HP

The problem was that this file was an RPM so i needed to extract the packages that we needed from inside this rpm. Using Alien i created the two *.deb packages called [hpasm_7.6.0-112_i386.deb]("http://phillips321.getmyip.com/HP_DL320_G2/hpasm_7.6.0-112_i386.deb") and [hpsmh_2.1.6-156_i386.deb]("http://phillips321.getmyip.com/HP_DL320_G2/hpsmh_2.1.6-156_i386.deb")

HOW-TO Install:

first of all this was tested on a fresh build of 6.06LTS so dont go crying if it dont work on your system.

install fakeroot and rcconf

```
sudo apt-get install fakeroot rcconf
```

Now download the 2 packages we need

```
wget http://phillips321.getmyip.com/HP_DL320_G2/hpasm_7.6.0-112_i386.deb
wget http://phillips321.getmyip.com/HP_DL320_G2/hpsmh_2.1.6-156_i386.deb
```

now install both of the packages

```
sudo dpkg -i hpasm_7.6.0-112_i386.deb
sudo dkpg -i hpsmh_2.1.6-156_i386.deb
```

once they have both installed go into rcconf and activate them so they start at boot

```
sudo rcconf
```

now reboot and you should be done

Problems....if hpsmh keeps looking for a user called hpsmh and a group calld hpsmh

Error message output is

```
chown: 'root:hpsmh' : invalid group
chown: 'hpsmh:hpsmh' : invalid user
```

then you need to add the user hpsmh
```
sudo useradd hpsmh
```

---

### Post by jake_l on 2007-08-10
Talk about a small world - Just today I started working on the same server, and having the exact same issue with the fans working at (what appears to be) 100%. If anyone has some input, I'm sure we'd both appreciate it. 

Thank you! 
  - Jacob

---

### Post by phillips321 on 2007-08-10
.

---

### Post by phillips321 on 2007-08-10
.

---

### Post by phillips321 on 2007-08-10
SOLVED, please see first post

---

### Post by jbeckford1 on 2007-09-19
Somewhat of a newb...

Just wanted to add that I installed the HPASM portion on my ML370 Proliant Server... Although I used RCCONF to add it to start up, it didn't work... 

First I located HPASM under /opt/compaq/hpasmd/bin then ran > ./hpasmd activate it seems no other switches would work like what was listed under man hpasm...

I rebooted the system and back to the full speed... Figured I needed a startup script, dug around and came up with /etc/rc.local ... Just edit the file and include  > /opt/compaq/hpasmd/bin/hpasmd activate before the line exit 0 ...

Now when I boot, the fan speed and noise lower considerably, about 1.5 sec after the login page appears...

Would like to get HPSMH working, but that is not to big a deal, I hope that has helped someone... 

Thanks to the original poster: phillips321

Lataz...

Errr... this was done on Ubuntu 6.10, 7.04 is having an issue during load...

---

### Post by Jester. on 2007-10-12
Hi phillips321,

thank you for your guide to silence the noise of that fans of my DL320. You can not imagine how deeply grateful I am!!

BTW: I executed all steps on ubuntu feisty 7.04. I got an error while installing hpsmh_2.1.6-156_i386.deb. here the errormessage:
```

/opt/hp/hpsmh/install/doinst.sh: 73: function: not found

```

Jester

---

### Post by Jester. on 2007-10-14
Hi again,

after a new installation of my system, I've been looking for a driver on the HP homepage. I saw, that HP now supports debian etch (and sarge, too). So they distribute the appropriate software packages on [http://h20293.www2.hp.com/portal/swdepot/displayProductsList.do?category=LINUX](http://h20293.www2.hp.com/portal/swdepot/displayProductsList.do?category=LINUX)
You can download the newest HP ProLiant Value Add Software for free. They also provide a good documentation for installing the packages.
Anywhere here are some pitfalls:
[list]
[*]first you have to install hpasm. But before you can install, you have to get some dependend packages:
```

apt-get install snmpd

```
and
```

apt-get install libstdc++2.10-glibc2.2

```
[*]if you get the message "Syntax error: Bad substitution", then have a look at the shell script which caused the message and change
```

#/bin/sh

```
to
```

#/bin/bash

```
[/list]
After that you can install hpsmh and/or all other packages you got from the link above.

Jester

---

### Post by jeangaud on 2007-12-21
Has anyone tried this on Ubuntu 7.10 ?

I tried different things... no success!

I have a DL380 G3


Thanks

Jean

---

### Post by jeangaud on 2007-12-21
Never mind this, I got it.

It's working.

Using Ubuntu Server 7.10

I followed the first instructions of Jester, for installing the first packages.

Downloaded the HPASM package from there:

[http://h20293.www2.hp.com/portal/swdepot/displayProductsList.do?category=LINUX](http://h20293.www2.hp.com/portal/swdepot/displayProductsList.do?category=LINUX)

installed that package:
Debian 3.1 (Sarge) - HP ProLiant Value-Add Software x86

sudo dpkg -i packagename.deb....

It was misssing some other packages, so I installed other dependent package with apt-get install....

then typed this:

cd /bin
sudo rm sh
sudo ln -s bash sh

sudo hpasm activate

And it worked.

---

### Post by davidpodhola on 2008-02-17
Great , thanks, working! :-\"

---

### Post by Gizzard21 on 2008-03-12
Thanks. Worked here to!

---

### Post by phillips321 on 2008-05-08
hi guys,

Just installed on 8.04 and after a few minor issues it's working fine.

needed to install the libstdc++2.10-glibc2.2_2.95.4-27_i386.deb package first.

I have mirrored everything needed on my server for you:
[http://phillips321.co.uk/HP_DL320/]("http://phillips321.co.uk/HP_DL320/")

the 3 packages u need are as follows (in order of installation)
[http://phillips321.co.uk/HP_DL320/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb]("http://phillips321.co.uk/HP_DL320/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb")
[http://phillips321.co.uk/HP_DL320/hpasm-7.7.0-115.sarge26.i386.deb]("http://phillips321.co.uk/HP_DL320/hpasm-7.7.0-115.sarge26.i386.deb")
[http://phillips321.co.uk/HP_DL320/hpsmh-2.1.7-167.i386.deb]("http://phillips321.co.uk/HP_DL320/hpsmh-2.1.7-167.i386.deb")

You will also need things like snmpd but you will need to install these through synaptic

---

### Post by Jester. on 2008-05-12
Hi there,

you can also install the libstdc++2.10-glibc2.2 manually from

[https://launchpad.net/ubuntu/gutsy/i386/libstdc++2.10-glibc2.2/1:2.95.4-24](https://launchpad.net/ubuntu/gutsy/i386/libstdc++2.10-glibc2.2/1:2.95.4-24)

The Gusty version also works for Hardy. You just have to execute

```

sudo dpkg -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

```

Rgds
Jester

---

### Post by stephenb on 2008-06-21
Has anyone had any success with the 64 bit debs? I followed the instructions here:
[http://h20392.www2.hp.com/catalog_content/product/install_page/T8569AAE.html](http://h20392.www2.hp.com/catalog_content/product/install_page/T8569AAE.html)

hpasm installed OK, as did cmanic and hpsmh. However, hprsm gave me this error:

```
The hprsm RPM installation failed!
Installation failure may be due to incomplete or missing
build environment or to absent hardware (RILOE/RILOE II,
iLo/iLo 2).  Please refer to the installation notes or to the
Linux Management HowTo available from http://www.hp.com/linux.
dpkg: error processing hprsm (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hprsm
```Also, hp-OpenIPMI gave me this:

```
Unpacking hp-openipmi (from hp-OpenIPMI-7.8.0-108.etch26.amd64.deb) ...
ERROR: Module ipmi_si does not exist in /proc/modules
Unable to remove module ipmi_si!
Please remove the installed 'ipmi' modules and disable
the initialization scripts.
dpkg: error processing hp-OpenIPMI-7.8.0-108.etch26.amd64.deb (--install):
 subprocess pre-installation script returned error exit status 1
The hp-OpenIPMI package has been removed from this system
```The remaining 3 packages on the HP site under Debian are for i386 and a force install is required. However, they need libstdc++2.10-glibc2.2_2.95.4-27_i386.deb. I tried to force install that, but got this error:

```
dpkg: error processing libstdc++2.10-glibc2.2_2.95.4-24_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
```Maybe I could extract the libs and copy them to /usr/lib. Has anyone any advice on what's best to do?


.

---

### Post by SuperJETT on 2008-06-22
> **phillips321 said:**
> hi guys,

Just installed on 8.04 and after a few minor issues it's working fine.

needed to install the libstdc++2.10-glibc2.2_2.95.4-27_i386.deb package first.

I have mirrored everything needed on my server for you:
[http://phillips321.co.uk/HP_DL320/]("http://phillips321.co.uk/HP_DL320/")

the 3 packages u need are as follows (in order of installation)
[http://phillips321.co.uk/HP_DL320/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb]("http://phillips321.co.uk/HP_DL320/libstdc++2.10-glibc2.2_2.95.4-27_i386.deb")
[http://phillips321.co.uk/HP_DL320/hpasm-7.7.0-115.sarge26.i386.deb]("http://phillips321.co.uk/HP_DL320/hpasm-7.7.0-115.sarge26.i386.deb")
[http://phillips321.co.uk/HP_DL320/hpsmh-2.1.7-167.i386.deb]("http://phillips321.co.uk/HP_DL320/hpsmh-2.1.7-167.i386.deb")

You will also need things like snmpd but you will need to install these through synaptic

Then what?  Do I then follow the OP or configure something in Preferences or ?  

I rebooted after successfully installing the above (plus snmpd) but they're still roaring.

Thanks for the help/effort/hosting.

---

### Post by SuperJETT on 2008-06-22
Got it for a second, had to sudo hpasm activate and rcconf to ensure it starts on boot, but after a reboot the fans went right back to high and stayed there.

Now, hpasm/hpasmd are not found at terminal.

???

---

### Post by Jibadee on 2008-07-10
Hello I have just rebuilt my DL320 and I am having problems installing libstdc++2.10-glibc2.2 to slow the fans down. :(

$ sudo apt-get install libstdc++2.10-glibc2.2   

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libstdc++2.10-glibc2.2

Any clues?

Many thanks

Andy

---

### Post by Jibadee on 2008-07-10
$ sudo dpkg -i hpasm-7.7.0-115.sarge26.i386.deb
(Reading database ... 94949 files and directories currently installed.)
Unpacking hpasm (from hpasm-7.7.0-115.sarge26.i386.deb) ...
===========================================================
NOTE: The storage agents that come packaged with the
      hpasm application you are installing, require
      the libstdc++2.10-glibc2.2 package in order for
      them to run successfully. Please use the apt-get
      utility to download the package.
      For example: apt-get install libstdc++2.10-glibc2.2
===========================================================
dpkg: error processing hpasm-7.7.0-115.sarge26.i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 hpasm-7.7.0-115.sarge26.i386.deb

---

### Post by jbeckford1 on 2008-07-18
Jibadee your answer is here... I assume you downloaded the file (somewhere), however the file is local and not in the repository, so you have navigate to the directory the file is in and then run the command Jester posted to install it... 

I just installed, but I was in the GUI not at the command prompt and used GDebi Package Installer (from right-click menu)...

> **Jester. said:**
> Hi there,

you can also install the libstdc++2.10-glibc2.2 manually from

[https://launchpad.net/ubuntu/gutsy/i386/libstdc++2.10-glibc2.2/1:2.95.4-24](https://launchpad.net/ubuntu/gutsy/i386/libstdc++2.10-glibc2.2/1:2.95.4-24)

The Gusty version also works for Hardy. You just have to execute

```

sudo dpkg -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

```

Rgds
Jester

Gotta go now, but after installation I ran:

```
sudo hpasm activate
```

---

