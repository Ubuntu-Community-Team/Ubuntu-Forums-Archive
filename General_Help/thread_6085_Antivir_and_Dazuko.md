---
title: "Antivir and Dazuko"
date: 2004-11-24
forum: General Help
---

### Post by uggeli on 2004-11-24
Could someone of you help me up that how can I istall Dazuko and antivir to my new ubuntu system (I'm newbie here)? I hava just downloaded Antivir for Linux workstations 2.1.2 from here:  [http://www.hbedv.com/en/products/antivir_workstation/?&no_cache=1](http://www.hbedv.com/en/products/antivir_workstation/?&no_cache=1)  and in readme file there is mentioned that Dazuko needs to be installed allso and link to Dazuko: [http://dazuko.org/howto-install.shtml](http://dazuko.org/howto-install.shtml)

It seems that Dazuko is very difficult to install since there was talking about compiling kernel and I haven't do anything like that ever. So if someone could give a step by step guide how to get those two ibstalled, or even give your opinion that is there any reason to install it. And maybe if you know some other free antivirus program with graphical user interface (yep there should be GUI in that antivir, atleast in one page there was mention about it) to linux?

---

### Post by jdong on 2004-11-24
IMO for Linux, a realtime AV scanner is largely unnecessary. Linux has few viruses written for it (if any). Doing periodical checks for rootkits is cool, if you want. For me, **f-prot** is a far superior (free/restricted license) on-demand scanner for Linux.

---

### Post by markw on 2004-11-24
In all the time I have used Linux I have never gotten a virus. Ok, so I haven't used Linux that much. But I have never heard of a Linux box getting a virus. What I would do is just wait till you get a virus to install antivirus software. You probably never will need it.

---

### Post by zenrox on 2004-11-25
what are you NUTS 
thare are like 5 virri for *nix and for them to be distructive to your sys thay need to be in the root 
but that ant going to happen :shock:

---

### Post by uggeli on 2004-11-25
Hmm so it really is unnecessary to install antivirus program to linux. But what if you want to be sure that you are not sending windows-viruses excample when forwarding e-mail jokes (not spamming just small group)? Windows-viruses do no harm to linux but shouldn't you think receiver allso? So afterall installing antivirus program isn't so bad idea isn't it?

Littlebit offtopic but there are just 2 or 3 worms (if I remember correctly) to Symbian Series 60 phones and even Series 60 Phones has Antivirus programs. And sure antivirusprogram in linux wouldn't take so much resources (prosentually) as in S60 phones.

Back in topic.. If I install F-prot, will it autoupdate itself? Clam or something like that has autoupdate opinion, but if I go to commandline scanner sure F-Prot would be nice for some reasons.. ;)

---

### Post by Joakim on 2004-11-27
Check out aegis antivrus scanner:
[B]
A virus scanner for Linux/Unix systems[/B]
Aegis is a virus scanner for Linux/Unix systems with a simple and intuitive
user interface.

Aegis supports scanning of subdirectories, hidden files and .zip and .tar
archive files, and drag-and-drop of files from the Nautilus file browser, or
your Gnome desktop. When a virus is detected you can choose to delete,
quarantine or rename the file.

sudo apt-get install aegis-antivirus-scanner


/Joakim


**PS!** To upgrade your AV definitions you must run the program as "root":
gksudo aegis-antivirus-scanner

---

### Post by jdong on 2004-11-27
[QUOTE=uggeli]
Back in topic.. If I install F-prot, will it autoupdate itself? Clam or something like that has autoupdate opinion, but if I go to commandline scanner sure F-Prot would be nice for some reasons.. ;)[/QUOTE]

The update script is /usr/lib/f-prot/update.pl or something along that line -- set a cron job to run it every hour/day/whatever.

---

### Post by uggeli on 2004-11-28
Thanks for aswers. I will use f-prot and do like jdong said, after I have solved one other problem, but that's in one other thread so no more about that now, but thanks again!

---

### Post by Marauder1 on 2004-11-28
I use a anti-virus just not to send 
Windows users anything, 
The one i use is Bitdefender.

[http://www.bitdefender.com/index.ph](http://www.bitdefender.com/index.ph)

It work on command line with 
free updates.

---

### Post by khristian on 2007-08-04
looks like everyone here failed to answer the question of the OP.
i'm trying to install avira antivir here, and ran into problems compiling dazuko.
many places suggested that using ```
m-a a-i dazuko
``` (modules-assistant) would install and compile it. But it complains saying >  checking if security module support is enabled... no                       
 error: security module support must be enabled in your kernel
 make[1]: ** [kdist_config] Erro 1
Which one in the kernel config is this security module support? I can't seem to find it =/

---

### Post by hazelkid on 2007-09-16
Ok, long time no answer. :)

Here is what I have done for it:

1. Download the 2.3.4-pre2 dazuko source code (starting with 2.3.4-pre1 you don't have to patch your kernel any more for this to work)
2. Download Avira AntiVir Classic (it is free)

! If you don't have your kernel headers installed go get them:

```
$ sudo apt-get install linux-headers-generic
```

Now the fun part:

Unpack the dazuko source to wherever you want. Open a terminal and go into your dazuko source code folder. 
Configure the sources:
```
$ ./configure
```

Now go and compile the sources by typing:
```
$ make
```
If you get some strange error with the /linux/version.h file you need to cast a spell on your command. Do it like this:
```
$ sudo make
```
Everything should work just fine now!

We're not just going to install this because, as the dazuko guys would we have to test dazuko first. So go on with this:
```
$ sudo insmod ./dazuko.ko
```
If you get a strange error about wrong parameters do this:
```

$ sudo rmmod capability
$ sudo insmod ./dazuko.ko
$ sudo modprobe capability

```
Hopefully this works because otherwise You have to check this out: [http://dazuko.de/faq.shtml]("http://dazuko.de/faq.shtml")

Ok. Now one more thing before installing. Test the loaded module. You need to compile and run a small test tool included in the dazuko sources. Just type: 
```

$ cd example_c
$ make
$ sudo example /home

```
If this works you should see some nice event behaviour and happy debug messages telling you that everything works correct. Just press Ctrl-C to get back to your terminal. If this doesn't work I would like you to visit the dazuko FAQ address.

If things are right there's one final step. The installation:
```

$ sudo make install

```

Now you don't need that source code anymore.

You have to make sure that the dazuko module properly loads every time you start your computer. So edit your /etc/modules file as root and add "dazuko" at the end of the list.  Because udev is playing smart and it shuffles the loading you have to make sure he does as we want. Create a new file called dazuko in /etc/modprobe.d:
```

sudo gedit /etc/modprobe.d/dazuko

```
Now copy and paste these lines there and save the file:
```

install dazuko modprobe -r capability;\
modprobe -i dazuko; \
modprobe -i capability

```

Now unpack the AntiVir archive and just run the install.sh in a terminal and answer all those annoying questions. No big deal with that. Tip: If you don't want to read the license agreement just press q and continue the installation. 

Now one more thing. After installing make sure to go to Users and Groups (in System -> Administration in Gnome) and in gorup management find "antivir" group and go to properties and select the desired users to be in the antivir group. You shoul at least select root :) (not that he needs it anyway)

Everything should work just fine now. You can start the admin tool running antivir-gui as root.


Tip: Feisty seems to be going mad. You can't just use "gksu antivir-gui" to start the admin tool. I don't know why. You have to open a terminal and run "sudo antivir-gui".

Enjoy

---

### Post by romyr on 2007-10-30
I tried to install dazuko, but  

> ./configure

stops with error.

> checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... ok (cc)
kernel source in /lib/modules/2.6.22-14-generic/source... no
kernel build source in /lib/modules/2.6.22-14-generic/build... yes
kernel source in /lib/modules/2.6.22-14-generic/build... yes
acquiring Linux kernel code configuration... error
error: unable to compile linux_conf utility
please see `linux_conf_make.out' for details


File "linux_conf_make.out" report this:

> linux_conf.c:10:19: error: stdio.h: Nessun file o directory
linux_conf.c: In function ‘main’:
linux_conf.c:72: warning: implicit declaration of function ‘printf’
linux_conf.c:72: warning: incompatible implicit declaration of built-in function ‘printf’

I am using Ubuntu Gutsy Gibbon.

Sorry for my poor english. I am italian.

Thanks

---

### Post by Elegorod on 2008-02-07
If you get such error:
> linux_conf.c:10:19: error: stdio.h: Nessun file o directory
linux_conf.c: In function &#8216;main&#8217;:
linux_conf.c:72: warning: implicit declaration of function &#8216;printf&#8217;
linux_conf.c:72: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

install the package ```
libc6-dev
```

In Gutsy, instead of
```

$ sudo rmmod capability
$ sudo insmod ./dazuko.ko
$ sudo modprobe capability

```
this works
```

$ sudo rmmod apparmor
$ sudo insmod ./dazuko.ko

```

---

### Post by bosesubhasis on 2008-03-09
helo everyone,
 
antivir gui not working in my ubuntu 7.04 64 bit. one thing i noticed while installing the gui feature not even prompted for configuration. the rest settings working well, even the avguard guard staus in real-time mode also working.
while typing "sudo antivir-gui" i get this "sudo: antivir-gui: command not found". but yesterday when i tried in my 7.10 32bit it worked well as well as the Gui mode and real time mode.
my java version:-
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

pls help me.

---

### Post by Belikov on 2008-05-31
After running ./configure, my output is

checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... ok (cc)
kernel source in /lib/modules/2.6.24-17-generic/source... no
kernel build source in /lib/modules/2.6.24-17-generic/build... yes
kernel source in /lib/modules/2.6.24-17-generic/build... yes
acquiring Linux kernel code configuration... ok
checking if Linux is RSBAC patched... no
checking if devfs is enabled... no
discovered host system... Linux (2.6.24)
checking if security module support is enabled... yes
verifying capabilities are not built-in... built-in : (
error: capabilities are built-in to the kernel:
       you will need to recompile a kernel with capabilities
       as a kernel module

What can I do now ? (I'm using Hardy, kernel 2.6.24-17-generic)

---

