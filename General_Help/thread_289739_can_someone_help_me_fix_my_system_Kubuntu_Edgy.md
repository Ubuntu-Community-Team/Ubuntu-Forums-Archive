---
title: "can someone help me fix my system? Kubuntu Edgy"
date: 2006-10-31
forum: General Help
---

### Post by maddbaron on 2006-10-31
I am using Kubuntu Edgy.

Currently adept says I have7 updates/upgrades. 

1. When I try to start them after a few seconds it cancels and says broken and in details it says broken dependencies. 

2. I installed mplayer and it wont work. it will start and give me an error for whatever file I use. 

3.I can't use java even though its installed and swiftfox, firefox, opera, konquerer all say I am missing the plugin.

4. I try to install a program like Kompile from adept and it says broken and won't install.

5. I run sudo apt-get update and get this as reply
> W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I also run this command and get this as result
> maddbaron@baronworks:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

> maddbaron@baronworks:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process



I changed all changed all my repo's to edgy and even removed some but nothing works. Does anyone know what I can do to fix these problems and get my programs to install/upgrade and work?

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by vixenk on 2006-10-31
Don't worry, it's not as bad as you think. :)

Basically the first batch of errors mean that those repositories need a gpg public key, and gpg can't find them. So, what we need to do is get those keys back. :)

Enter these commands in terminal:
> wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
Press Enter.
> wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -
Press Enter.
> wget [http://mrpouit.tuxfamily.org/12B83718.gpg](http://mrpouit.tuxfamily.org/12B83718.gpg) -O- | sudo apt-key add -
Press Enter.

The second error you described just means that you were trying to run more than one instance of Apt (you may have had Synaptic or Adept open, or may have had an Apt process running that didn't get killed). Killing the offending program or process will fix this. I have also came across a few instances in which the lock file simply didn't get removed. In these cases, rebooting or entering this command in terminal will fix it:
> sudo rm /var/lib/dpkg/lock

---

### Post by turkenator on 2006-10-31
also just incase u have broken/unmet dependencies run

```
sudo apt-get upgrade build-dep
```

---

### Post by maddbaron on 2006-10-31
> **vixenk said:**
> Don't worry, it's not as bad as you think. :)

Basically the first batch of errors mean that those repositories need a gpg public key, and gpg can't find them. So, what we need to do is get those keys back. :)

Enter these commands in terminal:

Press Enter.

Press Enter.

Press Enter.

The second error you described just means that you were trying to run more than one instance of Apt (you may have had Synaptic or Adept open, or may have had an Apt process running that didn't get killed). Killing the offending program or process will fix this. I have also came across a few instances in which the lock file simply didn't get removed. In these cases, rebooting or entering this command in terminal will fix it:

> maddbaron@baronworks:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--10:32:31--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.1'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

10:32:31 (58.92 MB/s) - `key.gpg.asc.1' saved [1730/1730]

maddbaron@baronworks:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ld                                                              t4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

> maddbaron@baronworks:~$ wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -
--10:47:18--  [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg)
           => `-'
Resolving 3v1n0.tuxfamily.org... 212.85.158.4
Connecting to 3v1n0.tuxfamily.org|212.85.158.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,374 (2.3K) [text/plain]

100%[====================================>] 2,374         --.--K/s

10:47:18 (195.43 KB/s) - `-' saved [2374/2374]

OK


> maddbaron@baronworks:~$ wget [http://mrpouit.tuxfamily.org/12B83718.gpg](http://mrpouit.tuxfamily.org/12B83718.gpg) -O- | sudo apt-key add -
--10:48:25--  [http://mrpouit.tuxfamily.org/12B83718.gpg](http://mrpouit.tuxfamily.org/12B83718.gpg)
           => `-'
Resolving mrpouit.tuxfamily.org... 212.85.158.4
Connecting to mrpouit.tuxfamily.org|212.85.158.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,120 (2.1K) [text/plain]

100%[====================================>] 2,120         --.--K/s

10:48:25 (196.26 KB/s) - `-' saved [2120/2120]

OK



[quote]
maddbaron@baronworks:~$ sudo apt-get update

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
[quote]


I'm so confused now...

---

### Post by maddbaron on 2006-10-31
> 
maddbaron@baronworks:~$ sudo apt-get upgrade build-dep
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  avidemux kdebluetooth mencoder mplayer qobex wpasupplicant
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/2604kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.


:(  my system doesnt like me very much

---

### Post by maddbaron on 2006-10-31
i think i need to uninstall swiftfox, mplayer and firefox and java then reinstall them.

does anyone know how to do that in terminal since adept keeps messing up on me.

---

### Post by maddbaron on 2006-10-31
this is strange, firefox plays java but swiftfox doesnt and i cant seem to remove swiftfox thru adept/ i tried removing mplayer through adept and it wanted to remove my acidrip and dvd video maker...my system is all messed up...

---

### Post by vixenk on 2006-10-31
> **maddbaron said:**
> > 
maddbaron@baronworks:~$ sudo apt-get update

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
[quote]


I'm so confused now...

> **maddbaron said:**
> :(  my system doesnt like me very much

Hmm... that is strange.

Try double checking your sources.list:
[quote]sudo gedit /etc/apt/sources.list

this is what the Automatix repo entry should look like:
> #automatix
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

And this is what the tuxfamily repo entry should look like:
> # Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn

If they don't match that, change them and save the file, then repeat the steps given in my last reply.

BTW, did you update to Edgy from Dapper via the repositories or is Edgy a clean install?

---

### Post by maddbaron on 2006-10-31
clean install and i will check my repo's now thank you,

---

### Post by maddbaron on 2006-10-31
do i replace the tux family above by taking this out or adding the one above to these?


> deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0 
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0 

---

### Post by maddbaron on 2006-10-31
> W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9


one error to go

---

### Post by vixenk on 2006-11-01
> **maddbaron said:**
> do i replace the tux family above by taking this out or adding the one above to these?
Taking that out and adding the one above in their place.

---

### Post by maddbaron on 2006-11-01
same problem remains....  :(

---

### Post by vixenk on 2006-11-01
Wow.

Ok, replace the repo I gave you:
>  # Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn

with the old one:
> deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0[/quote}

and type this in terminal one more time:
[quote]sudo wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -

The most I can think of is that something has to be going on with that repo working with its own public key.

As for everything else... 

Go to Synaptic and hit the refresh button. Then try reinstalling the troublesome applications (even the ones that are already installed). You may or may not get errors this time around. If you do, post them back here.

Also, it may help at this point to see a copy of your sources.list. :) You may have disabled repos in it that can make up for the missing tuxfamily repo.

---

