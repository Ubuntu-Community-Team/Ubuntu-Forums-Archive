---
title: "no connection???"
date: 2007-10-30
forum: General Help
---

### Post by magordoom on 2007-10-30
can someone help me out on this? i log into ubuntu, and before i upgraded to 7.10 it automatically found my internet connection. now that i have upgraded it cannot find one. i have tried using the help files, and searched for anetwork, and nothing shows up, yet when i connect to windows i have internet (obviously)[most of the time it shows no available connections and im still connected{windows}]. can someone help me fix this?:confused: (my internet connection is ethernet [charter])

(read my last post on the new problem)

---

### Post by magordoom on 2007-10-30
not moved to internet connection help.

---

### Post by AlexThomson_NZ on 2007-10-30
Ok magordoom, need some more info from you...

Open up a terminal and post the results from the following commands:
ifconfig -a
lspci | grep Eth
dmesg | grep eth

---

### Post by magordoom on 2007-10-31
ok i am terrible at things like command prompt :( how do i get to the second line to type more than one line?
i may have done it right, but it said command not found, so i doubt i did.

---

### Post by AlexThomson_NZ on 2007-10-31
Just type exactly what I have written...

lspci | grep Eth

And press return...

The first line is probably most useful though for now, what does that return?

---

### Post by magordoom on 2007-10-31
ok here it is x.x
#1
ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:19:21:57:78:27   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:21  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

#2
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)

#3
[   14.448000] sky2 eth0: addr 00:19:21:57:78:27

i hope this helps!

---

### Post by magordoom on 2007-10-31
BuMpAgE!

---

### Post by magordoom on 2007-10-31
NOT ANOTHER BuMp!

---

### Post by AlexThomson_NZ on 2007-10-31
Well this tells us that it sees your network card (#2), but can't start it up (no IP info in #1), unfortunately there are no clues as to why (#3)

Try restarting manually:
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

---

### Post by magordoom on 2007-11-01
ok i tryed doing your sudo commands, and it wanted me to enter my password. i try to type and nothing shows up. whats going on?:confused:

---

### Post by armware on 2007-11-01
when you type your password for sudo, the characters won't be displayed. type it in and press enter.

---

### Post by magordoom on 2007-11-01
bumpageness

---

### Post by magordoom on 2007-11-01
> **armware said:**
> when you type your password for sudo, the characters won't be displayed. type it in and press enter.

ok TYVM!

---

### Post by magordoom on 2007-11-01
ok heres the results of the stop start:
keith@ubuntu:~$ sudo /etc/init.d/networking stop 
[sudo] password for keith: 
 * Deconfiguring network interfaces...                                   [ OK ]  
keith@ubuntu:~$ sudo /etc/init.d/networking start 
 * Configuring network interfaces...                                            Ignoring unknown interface eth0=eth0. 
                                                                         [ OK ]

dont quite understand this

---

### Post by magordoom on 2007-11-01
man i dont wanna spam but, BUMP!:(

---

### Post by magordoom on 2007-11-02
ok i cot a suggestion to make a boot install cd, so i did, fixed all my problems but created a  huge new one. it over wrote my vista partition. i dont have any recovery cds, or a vista cd. WHAT DO I DO!? ](*,):frown:

---

