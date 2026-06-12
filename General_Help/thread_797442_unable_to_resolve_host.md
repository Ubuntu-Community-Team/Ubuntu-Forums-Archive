---
title: "unable to resolve host"
date: 2008-05-17
forum: General Help
---

### Post by kiwi-pete on 2008-05-17
Hello all.
Why do I get this strange text when I type a command in Terminal?

kiwipete@Ubuntu-laptop:~$ sudo apt-get update
sudo:**_ unable to resolve host Ubuntu-laptop_**

PS, sorry if this question has been posted before.

---

### Post by Irony on 2008-05-17
I imagine this is something to do with your hostname of Ubuntu-laptop.

The file is /etc/hosts - a google search for that may solve it, i.e. a name change.

---

### Post by kiwi-pete on 2008-05-17
> **Irony said:**
> I imagine this is something to do with your hostname of Ubuntu-laptop.

The file is /etc/hosts - a google search for that may solve it, i.e. a name change.
Hmmm that's odd, I don't seem to have an /etc/hosts file............

---

### Post by bodhi.zazen on 2008-05-17
Can you post the output of these commands :

```
hostname

sudo grep `hostname` /etc/hosts
```

Note those are back tics ` (on my keyboard by the number 1) not single quotes '

---

### Post by kiwi-pete on 2008-05-17
Here are the two examples you asked for, thanks.

kiwipete@Ubuntu-laptop:~$ hostname
Ubuntu-laptop
kiwipete@Ubuntu-laptop:~$ 

kiwipete@Ubuntu-laptop:~$ sudo grep `hostname` /etc/hosts
sudo: unable to resolve host Ubuntu-laptop
[sudo] password for kiwipete: 
127.0.1.1 Ubuntu-laptop.Kiwipetes Wireless Network
kiwipete@Ubuntu-laptop:~$

---

### Post by bodhi.zazen on 2008-05-17
Wow, you have lost /etc/hosts alright.

Lets make one then :)

```
gksu gedit /etc/hosts
```Enter these lines :

> 127.0.0.1     localhost
127.0.1.1     Ubuntu-laptop

Should restore things to more normal functioning.

If you can not gksu, you may need to boot to recovery mode and use nano.

nano /etc/hosts

---

### Post by kiwi-pete on 2008-05-17
Cheers for the help. Here is what it displayed;
127.0.0.1 localhost
127.0.1.1 Ubuntu-laptop.Kiwipetes Wireless Network

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

So I just deleted the .Kiwipetes Wireless Network and re-saved it.

I now get this in Terminal;
kiwipete@Ubuntu-laptop:~$ hostname
Ubuntu-laptop
kiwipete@Ubuntu-laptop:~$ sudo grep `hostname` /etc/hosts
127.0.1.1 Ubuntu-laptop
kiwipete@Ubuntu-laptop:~$

---

### Post by dwith on 2008-05-18
> **kiwi-pete said:**
> Cheers for the help. Here is what it displayed;
127.0.0.1 localhost
127.0.1.1 Ubuntu-laptop.Kiwipetes Wireless Network

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

So I just deleted the .Kiwipetes Wireless Network and re-saved it.

I now get this in Terminal;
kiwipete@Ubuntu-laptop:~$ hostname
Ubuntu-laptop
kiwipete@Ubuntu-laptop:~$ sudo grep `hostname` /etc/hosts
127.0.1.1 Ubuntu-laptop
kiwipete@Ubuntu-laptop:~$

-----------------------------------------------
Just as a matter of interest--the problem resolved above via editing the second line in /etc/hosts (deleting "Kiwipetes Wireless Network") can be accomplished through gui menus.

(Ubuntu 8.04 LTS running gnome--gnome panel) System>Administration>Network>Hosts (This is a tab). Unlock button (sudo privilege equivalent). Highlight the 127.0.1.1 address. Select Properties. Make sure the hostname is written correctly. Close the Network Settings gui by using the close button.

Hope this helps someone. People who use the "vboxmanager clonevdi" in VirtualBox will have to perform one of the above hostname modifications. The cloned vdi's hostname will obviously be the same as the original.

---

### Post by kiwi-pete on 2008-05-18
Thanks for that, its a much easier way to edit it.

It seems as much as I try to get my Wireless network to connect properly, it seems to ad the "Kiwipetes Wireless Network" to the host name.
I have had to resort to using a Ethernet cable in the mean time.

---

