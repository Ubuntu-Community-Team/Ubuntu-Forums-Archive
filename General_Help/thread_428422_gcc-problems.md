---
title: "gcc-problems"
date: 2007-04-30
forum: General Help
---

### Post by deejay_wonder on 2007-04-30
Hi folks. 

I don't know if I chose the right area for this post. I have now installed ubuntu (I used to use gentoo) but it seems like I have some problems with gcc. When I am trying to compile something I get this error:
/usr/src/linux-headers-2.6.20-15-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.20-15-386/scripts/gcc-version.sh: line 12: gcc: command not found

make[1]: gcc: command not found

I have tried everything but without succes.

---

### Post by taurus on 2007-04-30
You need the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by deejay_wonder on 2007-04-30
it is still the same

```
Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Making module
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/home/wonder/vpnclient modules
/usr/src/linux-headers-2.6.20-15-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.20-15-386/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: gcc: Kommando ikke fundet
make[1]: Går til katalog '/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /home/wonder/vpnclient/linuxcniapi.o
/bin/sh: gcc: not found
make[2]: *** [/home/wonder/vpnclient/linuxcniapi.o] Fejl 127
make[1]: *** [_module_/home/wonder/vpnclient] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.20-15-386'
make: *** [default] Fejl 2
Failed to make module "cisco_ipsec.ko".

```

---

### Post by taurus on 2007-04-30
What's the output of this command from a terminal?

```
gcc -v
```

---

### Post by deejay_wonder on 2007-04-30
```
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: gcc: command not found

```

---

### Post by taurus on 2007-04-30
Did you install the build-essential package as I described in my previous post?

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by deejay_wonder on 2007-04-30
yes I did :(

---

### Post by taurus on 2007-04-30
Did you see a message on the screen after you entered "sudo aptitude install build-essential" from a terminal saying that it would install gcc and a bunch of other files?

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by deejay_wonder on 2007-04-30
```
  GNU nano 2.0.2          File: /etc/apt/sources.list                           

deb http://quozl.netrek.org/pptp/pptpconfig ./
deb http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ dapper universe

```

When I type sudo aptitude install build-essential it is just saying that no packages will be installed or deleted. I have tried sudo apt-get remove build-essential and then sudo aptitude install build-essential

---

### Post by taurus on 2007-04-30
This is not good at all.  You cannot mix one release with another one in your /etc/apt/sources.list (feisty and dapper).  It will break your machine so you need to delete everything in /etc/apt/sources.list and create a new list.

```
gksudo gedit /etc/apt/sources.list
```
Here's your new list for feisty.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```
Save the new list and then run

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by deejay_wonder on 2007-04-30
I did what you said and it does not solve the problem. :(

---

### Post by taurus on 2007-04-30
Can you please be a little more specific especially the error message?  Can't really help you if you keep saying that it doesn't solve your problem?  What is the message when you ran those commands?  And can you post your /etc/apt/sources.list agai?

```
cat /etc/apt/sources.list
```

---

### Post by kingpoiuy on 2007-04-30
I'm not that guy but I am having the same problem I think....  It says I have GCC in Syaptic but look at this!


```

Reading package lists... Done
kingpoiuy@aashbyctest:~/xine-lib-1.1.6$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
kingpoiuy@aashbyctest:~/xine-lib-1.1.6$ gcc -v
bash: gcc: command not found
kingpoiuy@aashbyctest:~/xine-lib-1.1.6$

```

---

### Post by taurus on 2007-04-30
> **kingpoiuy said:**
> I'm not that guy but I am having the same problem I think....  It says I have GCC in Syaptic but look at this!


```

Reading package lists... Done
kingpoiuy@aashbyctest:~/xine-lib-1.1.6$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
kingpoiuy@aashbyctest:~/xine-lib-1.1.6$ gcc -v
bash: gcc: command not found
kingpoiuy@aashbyctest:~/xine-lib-1.1.6$

```

You can post your /etc/apt/sources.list here too.

```
cat /etc/apt/sources.list
```

---

### Post by deejay_wonder on 2007-04-30
sorry for not being specific. I did what you told me again and now it is working. Thanks a lot.

---

### Post by kingpoiuy on 2007-04-30
```

kingpoiuy@aashbyctest:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
kingpoiuy@aashbyctest:~$

```

---

### Post by kingpoiuy on 2007-05-01
Ok, I have it figured out.  I have set up the proxy but it seems it has only partially worked.  Some of the sources will still fail to connect and therefore I can not get GCC here at work.  I did it at home last night and it worked well.  

Thank you for the help!:)

---

