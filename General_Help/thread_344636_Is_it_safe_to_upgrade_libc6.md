---
title: "Is it safe to upgrade libc6"
date: 2007-01-23
forum: General Help
---

### Post by hectare on 2007-01-23
Version -> 6.06 dapper

As of today Jan 23 , when i update my system, it shows one pkg by the name of libc6.
Now i am no expert , but if this new libc6 is installed , won't it break some applications ,
 
Since this lib is required by most of the user level application , what are the chances of it breaking my system.

Also , can anyone else who is using 6.06 confirm , that this is a valid upgrade.

Thank you.

---

### Post by yopnono on 2007-01-23
> **hectare said:**
> Version -> 6.06 dapper

As of today Jan 23 , when i update my system, it shows one pkg by the name of libc6.
Now i am no expert , but if this new libc6 is installed , won't it break some applications ,
 
Since this lib is required by most of the user level application , what are the chances of it breaking my system.

Also , can anyone else who is using 6.06 confirm , that this is a valid upgrade.

Thank you.

Don't know about any problems with the lib. 
Anyhow I have updated 6.06 & 6.10 gnome desktop without any problems

---

### Post by konst88 on 2007-01-23
The package manager will worn you about any modification he will do.
Just read it carefuly, and see if any programs going to be removed.
If not, this means all the dependencies are satisfied, and the upgrade will be just fine.
PS: I also updated it today on edgy. All fine.

---

### Post by hectare on 2007-01-23
fair enough , before i press upgrade button can any one of you confirm that the result of the command :

**apt-cache show libc6 | grep "Version" **

mine shows :
Version: 2.3.6-0ubuntu20.2
Version: 2.3.6-0ubuntu20

yours should be 
Version: 2.3.6-0ubuntu20.2

or its just unnecessary paranoia

---

### Post by hectare on 2007-01-23
Can anyone confirm , that they have successfully updated the libc6 , if so please post the output of the above command from terminal .

This [http://ubuntuforums.org/showthread.php?t=344570](http://ubuntuforums.org/showthread.php?t=344570) thread also shows some problem with libc , may be this is an isolated to few users.

thank you.

---

### Post by yopnono on 2007-01-23
> **hectare said:**
> Can anyone confirm , that they have successfully updated the libc6 , if so please post the output of the above command from terminal .

This [http://ubuntuforums.org/showthread.php?t=344570](http://ubuntuforums.org/showthread.php?t=344570) thread also shows some problem with libc , may be this is an isolated to few users.

thank you.

Please did I not say that I did do a update?
mike@ubuntu:~/Desktop$ apt-cache show libc6 | grep "Version"
Version: 2.3.6-0ubuntu20.2
Version: 2.3.6-0ubuntu20

---

### Post by david_2001 on 2007-01-23
> david@darkstar:~$ apt-cache show libc6 | grep "Version"
Version: 2.4-1ubuntu12.2
Version: 2.4-1ubuntu12.1
Version: 2.4-1ubuntu12
david@darkstar:~$

Is there a problem?

---

### Post by neoflight on 2007-01-23
$ apt-cache show libc6 | grep "Version" 
Version: 2.4-1ubuntu12.2
Version: 2.4-1ubuntu12


is this a problem ??? why i have 2.4 and someone has 2.3 ???

---

### Post by david_2001 on 2007-01-23
If Synaptic / apt-get / whatever let you install the updated libc6 without complaining then you have no conflicts with other installed packages.  I happily ran Debian unstable for 18 months - from that perspective, an update to libc6 is a trivial change 8).

---

### Post by yopnono on 2007-01-23
> **neoflight said:**
> $ apt-cache show libc6 | grep "Version" 
Version: 2.4-1ubuntu12.2
Version: 2.4-1ubuntu12


is this a problem ??? why i have 2.4 and someone has 2.3 ???

I'm on dapper you have edgy.

---

### Post by ardchoille42 on 2007-01-23
I am on Dapper and have been upgrading daily.

[~ @ 13:59:57] apt-cache show libc6 | grep "Version"
Version: 2.3.6-0ubuntu20.2
Version: 2.3.6-0ubuntu20

I have seen no problems at all.

---

### Post by mdz on 2007-01-24
Some users have experienced a problem with a recent update to libc6 in Ubuntu 6.10 (Edgy).  We have not determined the root cause of the problem (it is related to the presence of some files not provided by Ubuntu), but a workaround is on its way within the next few hours.  [http://launchpad.net/bugs/81125](http://launchpad.net/bugs/81125)

---

