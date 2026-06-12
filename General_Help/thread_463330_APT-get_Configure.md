---
title: "APT-get Configure"
date: 2007-06-03
forum: General Help
---

### Post by waqaskool on 2007-06-03
after trying unsuccesfully setting up some wierd proxy progs i ended up getting this error 


waqas@Dixast:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxerces27
Use 'apt-get autoremove' to remove them.
Suggested packages:
  dhcp3-server
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 50 not upgraded.
Need to get 406kB of archives.
After unpacking 1966kB of additional disk space will be used.
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/universe firestarter 1.0.3-2ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-2ubuntu1_i386.deb](http://pk.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-2ubuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
waqas@Dixast:~$ 



what to do ppl !!!!!
is there any way to refresh all settings...!!!

---

### Post by waqaskool on 2007-06-03
is my problem COMPLEX !!!!

---

### Post by pseudonym on 2007-06-03
Looks like the Ubuntu server was down. Just retry and it should be OK (apt should work itself out). Also, with 50 packages 'not upgraded' it would be wise to update your system first before installing any non-default packages.

---

### Post by waqaskool on 2007-06-03
NO no NO NO .... u got it wrong look at these lines 


Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/...untu1_i386.deb](http://pk.archive.ubuntu.com/ubuntu/...untu1_i386.deb) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


it shouldnt be connecting to      localhost:4001 (127.0.0.1). - connect (111 Connection refused)

i messed up all ma settings thats it ......
and i dont know how to get em back 

synaptic gives out this error

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-2ubuntu1_i386.deb](http://pk.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/firestarter_1.0.3-2ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by pseudonym on 2007-06-03
My mistake. It sounds like your repositories aren't set up properly then. Did you edit the /etc/apt/sources.list file? If so, you can go [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") to see what the correct configuration should look like (along with a few little extras). The link contains all necessary instructions.

---

### Post by waqaskool on 2007-06-03
problem solved !!!
thankx

can u help me with this one too 
[http://ubuntuforums.org/showthread.php?t=463277](http://ubuntuforums.org/showthread.php?t=463277)

---

### Post by bapoumba on 2007-06-03
Please have a look to:
/etc/apt/apt.conf
/etc/environment
And see if there is any proxy defined there.

Run gnome-network-preferences --> is it set to direct ?
Look at Synaptic > Setting > Preferences > Network --> is it set to direct ?

---

### Post by airtonix on 2007-07-04
same problem, but 
>  /etc/apt/apt.conf
does not exist.

gnome-network-preferences & synaptic are set to "direct"

still wants to use the old proxy i specified prior to removing the nautilus and gnome-panel

---

