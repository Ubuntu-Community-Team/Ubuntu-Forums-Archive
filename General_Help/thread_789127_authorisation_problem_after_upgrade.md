---
title: "authorisation problem after upgrade"
date: 2008-05-10
forum: General Help
---

### Post by achechen on 2008-05-10
just today i have upgraded to Ubuntu 8.04 LTS and everything seems to be ruined.

at first, a problem about my soundcard occured - i hear audio, but in a very distorted way. then, i wanted to solve this problem using a tutorial, i have failed to get administration privileges.

these are the error messages which i see:

```
alper@alper-laptop:~$ sudo modprobe snd-
sudo: unable to resolve host alper-laptop
alper@alper-laptop:~$ 
alper@alper-laptop:~$ sudo 
sudo: unable to resolve host alper-laptop
alper@alper-laptop:~$ su
Password: 
su: Authentication failure
alper@alper-laptop:~$ 

```

i have no idea what's going on, and im very very new to the linux, if you answer, consider this. thanks in advance.

---

### Post by achechen on 2008-05-10
any suggestions?

---

### Post by pointone on 2008-05-10
Pinned at the top of the forum: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

It's the first bug listed.

---

### Post by justborn on 2008-05-10
try dis in the terminal and paste the result
[PHP]cat /etc/hosts
cat /etc/hostname[/PHP]

---

### Post by ghost_ryder35 on 2008-05-10
> **pointone said:**
> Pinned at the top of the forum: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)
 
It's the first bug listed.
here is the excert from the sticky at the top of the forum
> **PmDematagoda said:**
> Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts
```
and edit it to make it look like this:-
```
127.0.0.1 localhost
**127.0.1.1 icarus-laptop**
 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```
save the file.
 
That should fix the problem.

---

### Post by achechen on 2008-05-10
thanks guys, it worked. but, in order to do this:

```
gksudo gedit /etc/hosts
```

or any kind of administrative processes, i have to try 2-3 times until it starts, otherwise it shows the process on the taskbar with a title "starting administrat....?" , waits 5-10 seconds and disappears and nothing happens. (even ubuntu does not ask for the root pass) this wasnt the case before upgrade. and also, when i right click on the network manager on the upright corner "connection information" is greyed out and i cannot click on it.

---

### Post by ghost_ryder35 on 2008-05-10
> **achechen said:**
> thanks guys, it worked. but, in order to do this:
 
```
gksudo gedit /etc/hosts
```
 
or any kind of administrative processes, i have to try 2-3 times until it starts, otherwise it shows the process on the taskbar with a title "starting administrat....?" , waits 5-10 seconds and disappears and nothing happens. (even ubuntu does not ask for the root pass) this wasnt the case before upgrade. and also, when i right click on the network manager on the upright corner "connection information" is greyed out and i cannot click on it.
is it waiting for you to enter a password in the auth box?
Now that you have fixed sudo does 
```

sudo gedit /etc/hosts

```
do the same thing?

---

### Post by achechen on 2008-05-10
it happens whenever i try to reach options which are accessable by root password. normally it should show a window asking the root password, it does not do it, just waits, and ends process. after 5-6 tries im able to write down the password and do the thing.

---

