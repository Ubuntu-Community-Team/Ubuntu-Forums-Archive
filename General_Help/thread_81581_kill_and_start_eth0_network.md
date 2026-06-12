---
title: "kill and start eth0 network"
date: 2005-10-24
forum: General Help
---

### Post by stoeptegel on 2005-10-24
I would like to be able to shutdown my internet from the computer instead of having to walk to my modem and shut the power off it, and also start it up again when i want it.

Is there a proper command that i can use for killing and starting my internet connection?

---

### Post by burningbed on 2005-10-24
I think
sudo /sbin/ifconfig eth0 down 
will do what you want.
To get the network back up run:
sudo /sbin/ifconfig eth0 up

---

### Post by stoeptegel on 2005-10-24
Just found it:  ifup and ifdown, it sounds cleaner, lol :)

---

### Post by gare on 2008-04-21
I had better luck with this command to reboot my networking:

```
 sudo /etc/init.d/networking restart

```

was getting errors when trying to use ifup & ifdown on Hardy: 

> ifdown: interface ethO not configured



hth someone.

---

### Post by sujoy on 2008-04-21
> ifdown: interface ethO not configured

looks like you miss typed the 0 (zero) as O (the alphabet)

---

### Post by cha0s_unity on 2008-07-02
i've tried the "sudo /etc/init.d/networking restart" and this command works, however it will not give me a different ipaddress.
i did ifconfig before and after the restart and the same ip is presented.
 i know normally i will be assigned the same ip but i am switching wired networks going from a NAT private network to a v-lan class B network. i'm trying to find a way to reload my ip and gateway so I don't have to restart my computer.

---

