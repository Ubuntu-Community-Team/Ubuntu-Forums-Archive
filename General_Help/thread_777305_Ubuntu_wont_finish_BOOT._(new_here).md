---
title: "Ubuntu wont finish BOOT. (new here)"
date: 2008-05-01
forum: General Help
---

### Post by decarlo on 2008-05-01
Sorry if this thread is in the wrong spot.. About two weeks ago i install Ubuntu (8.04) doing a dual boot with XP. Everything is been working fine and im loving this Linux stuff. Last night i was using the add/remove program to install something to burn DVD's. While it was downloading my labtop locked up. so i did a hard reboot. In the boot its stoping when it gets to the mounting securtfys.. the last thing it says is confining network interfaces [ok]  

If anyone can help me out it would be thankful.. 

Ps sorry about my english..

---

### Post by decarlo on 2008-05-01
also i tried to use the recover boot option and it still stops at the same place..   help anyone??

---

### Post by decarlo on 2008-05-01
up

---

### Post by joshsmith on 2008-05-01
thats odd.

do you get left with a terminal prompt? if you do try running
```

sudo /etc/init.d/gdm start

```
(or press ctrl+alt+f2, login and run that)
hope it works, or post the output


also try
```

sudo apt-get upgrade

```
and post any errors, and run any commands it suggests to you

btw, the recover option doesnt load up the normal graphics of your desktop. that is the idea.

make sure at some point you also try pressing ctrl+alt+f7

reinstalling also wouldnt be too difficult

---

### Post by decarlo on 2008-05-01
It just stops after this:

Mounting Local FileSystems
activating swapfile swap
mounting securityfs on /sys/kernel/security :done
loading appArmor profiles : Done
checking minman space in /tmp
skipping firewall: ufw (not enabled)
configuring network interfaces
setting up console front and kepmap......

then it just sits there.. I tried pressing ctr alt f2 and nothing happens...  any thoughts?

---

### Post by Ayuthia on 2008-05-01
Can you post the make (HP, Dell, ...) and model (dv6000, Inspiron 5150, ...) of your laptop.  Also can you tell us if you are using the 32 or 64 bit version.

---

### Post by decarlo on 2008-05-01
yes, sorry.. Im using a Dell Inspiron 6000.. Ubuntu 8.04 64 bit

---

### Post by decarlo on 2008-05-01
also when i press alt f1 it shows me this:

loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/5..............
kinit: trying to resume from " " " " " ".....
kinit:no resume image, doing normal boot.. 


i dont know if this means anything..

---

### Post by joshsmith on 2008-05-01
reinstalling would probably be the quickest bet.

but if you are interested in learning,
you need to get to a command prompt somehow
either by pressing ctrl+alt+f(something, 1 to 6)
or by starting in safe mode and getting to a prompt that way, and running the commands i said
that is the only way to start troubleshooting

but reinstall if you cant be bothered
quick fix to all problems

"loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/5..............
kinit: trying to resume from " " " " " ".....
kinit:no resume image, doing normal boot..
"
this means you havent just started up the computer from hibernate

---

### Post by Ayuthia on 2008-05-01
> **decarlo said:**
> yes, sorry.. Im using a Dell Inspiron 6000.. Ubuntu 8.04 64 bit
Does it have an AMD chip with an Nvidia graphics card?  If so, there is a chance that you might need to add noapic to your boot parameters.  Most likely, your USB devices might stop working.  If so, you will most likely need to find another parameter to add to your boot parameters (like noirqdebug).

In case you don't know what I am talking about, you will need to edit your /boot/grub/menu.lst file as root.  You will need to go to the line that looks like:
```
kernel         /boot/vmlinuz-2.6.24-14-generic root=UUID=721ae177-c6b1-4c5e-847f-42f16f88e95e ro quiet splash
```
You will need to add noapic before the word splash.

---

### Post by decarlo on 2008-05-02
> **joshsmith said:**
> reinstalling would probably be the quickest bet.

but if you are interested in learning,
you need to get to a command prompt somehow
either by pressing ctrl+alt+f(something, 1 to 6)
or by starting in safe mode and getting to a prompt that way, and running the commands i said
that is the only way to start troubleshooting

but reinstall if you cant be bothered
quick fix to all problems

"loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/5..............
kinit: trying to resume from " " " " " ".....
kinit:no resume image, doing normal boot..
"
this means you havent just started up the computer from hibernate

I tried pressing ctr alt F2 to F8 but it just goes to a blank screen and i cant type anything.. Also it wont start in safemode.. I used my live Cd to try somethings like stoping the network from booting up but that didnt help b/c it still stop around the same spot.. I think im just going to re install. it sucks b/c im going to lose all my settings and cool desktop effects. lol

---

### Post by decarlo on 2008-05-02
> **Ayuthia said:**
> Does it have an AMD chip with an Nvidia graphics card?  If so, there is a chance that you might need to add noapic to your boot parameters.  Most likely, your USB devices might stop working.  If so, you will most likely need to find another parameter to add to your boot parameters (like noirqdebug).

In case you don't know what I am talking about, you will need to edit your /boot/grub/menu.lst file as root.  You will need to go to the line that looks like:
```
kernel         /boot/vmlinuz-2.6.24-14-generic root=UUID=721ae177-c6b1-4c5e-847f-42f16f88e95e ro quiet splash
```
You will need to add noapic before the word splash.

I have an Intel chip and im not using Nvidia.. It was all working before for about a few weeks but when i was using the add and remove program it locked up on me so i had to do a hard reboot and thats when this problem started.. i think im just going to reinstall it..

---

