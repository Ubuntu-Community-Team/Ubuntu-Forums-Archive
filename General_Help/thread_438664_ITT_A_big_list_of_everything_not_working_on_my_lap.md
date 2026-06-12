---
title: "ITT A big list of everything not working on my laptop"
date: 2007-05-09
forum: General Help
---

### Post by Priapus891 on 2007-05-09
1. My wireless card ( BCM4318 )

2. Every time I try and do something like install a package it tells me that I need an admin password, and from what I have read that is my password. It does not work for me.

3. When I use the sudo command it asks for a password and I try typing in my pass and the root pass and nothing happens.

4. Certain things like the network option, or the user.groups option under administration does not work. 

Halp plx?

BTW, I just did a fresh install of Ubuntu 7.04 on my laptop. I have it set to duel boot with windows XP pro.

---

### Post by spankymasterc on 2007-05-09
> **Priapus891 said:**
> 1. My wireless card ( BCM4318 )
3. When I use the sudo command it asks for a password and I try typing in my pass and the root pass and nothing happens.
o.

What do you mean nothing happens ?

like when your typing you cant see the cursor thing move?

well it doesnt look like its typing but it is if thats what you think not sure if i understand...

---

### Post by Priapus891 on 2007-05-10
This is what I get when I try to use sudo

```

adam@localhost:~$ sudo gksu network-admin
Password:
adam@localhost:~$ 

```

You can see that it just goes back to what I started with.
I know that when you type a pass that it doesn't show it, but when I do this then nothing shows up at all.

---

### Post by strabes on 2007-05-10
1) There are many how tos online about broadcom wireless cards.

2) Be more specific

3) When it asks you for your password just type it in and hit enter. It doesn't show any characters for security reasons. See this page for more information: [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

4) Be more specific

Regarding your second post, I'm not sure that "gksu" is even a command in gnome. Try "gksudo network-admin"

---

### Post by mdurham on 2007-05-10
> **Priapus891 said:**
> This is what I get when I try to use sudo

```

adam@localhost:~$ sudo gksu network-admin
Password:
adam@localhost:~$ 

```

You can see that it just goes back to what I started with.
I know that when you type a pass that it doesn't show it, but when I do this then nothing shows up at all.

 It looks like you are trying to run sudo twice.
seen man gksu: 'gksu - GTK+ frontend for su and sudo'
maybe it's that's the problem.

---

### Post by IgnorantGuru on 2007-05-10
Here are my notes for how I got the BCM4318 working in Edgy.  Edgy had a few bugs which required workarounds - not sure about Feisty.

```

Method using ndiswrapper
http://www.ubuntuforums.org/showthread.php?t=285809

#Disable kernel driver
pico /etc/modprobe.d/blacklist
	Add line:  blacklist bcm43xx

#ndiswrapper bug in Ubuntu
#https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983
#Solution:
#remove ndiswrapper-utils-1.1 (if present) and install ndiswrapper-utils-1.8

Adept: install knetworkmanager and ndiswrapper-utils-1.8

#Obtain bcmwl5.sys and .inf driver from Windows folder or elsewhere
ndiswrapper -i /data/tmp/bcmwl5.inf
ndiswrapper -l
	Should return driver and hardware present
pico /etc/modules
	Add line:  ndiswrapper
	#This causes kernel to load ndiswrapper automatically, otherwise use modprobe ndiswrapper

#If using knetworkmanager...
#Fix network manager to see wireless networks (edgy)
#bug: http://ubuntuforums.org/showthread.php?t=335140
#FIX: http://kubuntuforums.net/forums/index.php?topic=8845.0
#Comment out all line in /etc/network/interfaces after "# The primary network interface"
#Should only contain these lines:
	# The loopback network interface
	auto lo
	iface lo inet loopback
	address 127.0.0.1
	netmask 255.0.0.0


#Reboot - eth1 should now be present and working


```

---

### Post by dfreer on 2007-05-10
> **Priapus891 said:**
> 1. My wireless card ( BCM4318 )

2. Every time I try and do something like install a package it tells me that I need an admin password, and from what I have read that is my password. It does not work for me.

3. When I use the sudo command it asks for a password and I try typing in my pass and the root pass and nothing happens.

4. Certain things like the network option, or the user.groups option under administration does not work. 

Halp plx?

BTW, I just did a fresh install of Ubuntu 7.04 on my laptop. I have it set to duel boot with windows XP pro.

(1) check out ndiswrapper. look for a howto, specifically if there is one for your model.

(2) it should be your user password. the same password you login with

(3) it should go like this in terminal:
```
sudo ls -l
```
then it asks for your password like this:
```
Password:
```
when you type your password (the password you gave ubuntu when you installed it and the same password you use to login, it will show you nothing until you hit <Enter>. if successful, you should see a list of all the files in your current directory. if you type the wrong password it will ask again:
```
Password:
Sorry, try again.
Password:
```
What is the exact output when you try the above method?

(4) could you be more specific as to how they "don't work"?

yes. you should use sudo, or gksu not both.
```
sudo network-admin
```
```
gksu network-admin
```
of course if you are using a GUI you could launch it from System > Administration > Network

---

### Post by tact on 2007-05-10
> **Priapus891 said:**
> This is what I get when I try to use sudo

```

adam@localhost:~$ sudo gksu network-admin
Password:
adam@localhost:~$ 

```

You can see that it just goes back to what I started with.
I know that when you type a pass that it doesn't show it, but when I do this then nothing shows up at all.

Hi Priapus89,

Of course you could just use:
```

adam@localhost:~$ gksudo network-admin
Password:

```

I just tried both the above and what you used and it worked for me.  So I wonder if:
1.  Have you made any changes to your login?   i.e.  Are you using the same login ID and password that you created when first installing the system?  

2.  If you made any change, ie. are logging in as a different user to the initial user created, then possibly you need to add your new ID to the sudoer's list. (??)

---

### Post by yopnono on 2007-05-10
Make sure you are a member of the admin group.
Login as root and open the /etc/sudoers file and look for this: If you don't have it add it.
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by Priapus891 on 2007-05-10
Thanks for all the responses everyone. And sorry it's taking me a sec to respond. I just deleted Ubuntu 7.04 off of my computer and did a fresh install again. I guess I must have set up somehting wrong when I was setting it up because now everything works. Thanks for all the quick responses :D

---

