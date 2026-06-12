---
title: "I need help to connect to the internet."
date: 2007-03-26
forum: General Help
---

### Post by Red Dragon on 2007-03-26
it my first time that i use linux, so i cant understand how the hell i connect to the internet
i have DSL (pppoe) modem and i connecting to the internet only by password and username
so how i coneccting on the linux??


and 1 more problem i have drive whit 2gb  and i want to install it on this drive how do i do that??

---

### Post by mahy on 2007-03-26
How exactly is that modem connected to your computer? USB cable? Ethernet cable?

---

### Post by Red Dragon on 2007-03-26
i use the cable like the phone cable bat bigger

---

### Post by mahy on 2007-03-26
> **Red Dragon said:**
> i use the cable like the phone cable bat bigger

So it's an ethernet cable. :) That's good news!

Please post the output of 'ifconfig' command. (That's in the [Terminal]("http://www.psychocats.net/ubuntu/terminal"))

---

### Post by Red Dragon on 2007-03-26
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:99:4F:54  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:d3ff:fe99:4f54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1656 (1.6 KiB)  TX bytes:1924 (1.8 KiB)
          Interrupt:193 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

and the full and very long filw :
[http://rapidshare.com/files/22863807/Terminal.txt.html](http://rapidshare.com/files/22863807/Terminal.txt.html)

---

### Post by Red Dragon on 2007-03-26
sry for the dubel post delete this one (pressed enter twice)

---

### Post by Red Dragon on 2007-03-26
some1???
plz helppppppppp

---

### Post by Red Dragon on 2007-03-26
da** some1 gona help me??
i just wanted to connect to the internet and install that linux plzzz??

---

### Post by RedSquirrel on 2007-03-26
Have a look at this:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html)

---

### Post by s_h_a_d_o_w_s on 2007-03-26
Frigg opne the terminal and type:

sudo pppoeconf

Somewhere threw that enter ur username and password and accept all the defaults.

If that didn'tdo anything try

dhclient 

in terminal 

PATIENCE!

---

### Post by Red Dragon on 2007-03-27
10xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

---

### Post by BionicBigfoot on 2007-03-27
For DSL you need to go to Terminal t configure your pppoe
On the Application list look for accessories then click terminal.

Type in:

sudo pppoeconf

then type the password you made when you created your Ubuntu account. This is called your root password. The password is used often for security reasons so no body damages your computer

follow the prompts on the screen. You will have to put in your ISP DSL username and password. Your Internet Service Provider gave this to you when you signed up.

You will have an option to always connect when Ubuntu starts, so that you never have to do this again.

There is also a tutorial on the wiki page I believe

---

### Post by BionicBigfoot on 2007-03-27
Please let me know if this helped

---

### Post by Red Dragon on 2007-03-27
10xxxx all!!
now i typing from the ubntu.

now some1 can answer me how do i install it corectly and not dmg my windows??

---

### Post by rich.bradshaw on 2007-03-27
Read the wiki/tutorial whatever.

Basically your harddrive is split into partitions. By default Windows takes up the whole of a harddrive when it is installed, as computer makers don't assume that you are going to install more operating systems.

The easiest things is to install on a different drive to Windows if you have one.

You can't easily change the size of paritions without erasing them you see, so it's a bit tricky if you don't have anyway of backing up files.

If you have a second drive, then you can copy everything on it to some other drive, then reformat it (in Windows or using gparted) with different partitions.

Install Ubuntu, then move files back on to the windows partition again.

---

### Post by Red Dragon on 2007-03-27
nvm man finally installed almost deleted my windows and all what i have..
bat now all works
10x everyone who helped!!

---

### Post by s_h_a_d_o_w_s on 2007-03-27
10x?

wth?

---

