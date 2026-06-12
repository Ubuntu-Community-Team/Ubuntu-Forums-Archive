---
title: "Mayhem of errors. Ubuntu 14.04"
date: 2015-08-17
forum: General Help
---

### Post by arthur24 on 2015-08-17
I hope I'm not going to bring to others a massive headache, I got one myself at the moment. I am new to Ubuntu and over the last 1-2 weeks I accumulated some system errors. I tried to remedy the problems by looking online. But many solutions in my case lead to even more errors. 
So far the problems haven't yet lead to my system being inoperable. 
But it did lead to problems such as

-Software center being completely broken, it doesnt popup a window, just the loading circle.
-Can't install any packages whatsoever.
-My mouse and keyboard don't operate and I have to boot into recovery mode via Grub to operate the mouse and keyboard.

I got a total of 4 errors. It's likely somehow self induced by adding faulty software, but I can't remember what that might be unfortunately and I don't know how to check.

Error 1:    > 
update-apt-xapian-index crashed with SIGSEGV in pkgCacheGenerator::pkgCacheGenerator()



Error 2:    > do-release-upgrade crashed with SystemError in open(): E:Type 'new' is not known on line 59 in source list /etc/apt/sources.list



Error 3:    > E:Type 'new' is not known on line 57 in source list /etc/apt/sources.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.


Error 4: 
   > 'unknown error: '<class 'system error'>' (E:Type 'new' is not known on line 57 in source list /etc/apt/sources.list)'

---

### Post by howefield on 2015-08-17
First on the to do list is to clean up your sources.list.

Can you run 

```
cat /etc/apt/sources.list
```

in a terminal, and post the output back here (between code tags) ?

---

### Post by arthur24 on 2015-08-17
**Voila**

```
# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

# deb cdrom:[Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ vivid main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ trusty universe
deb http://nl.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
new line of text


```

---

### Post by howefield on 2015-08-17
OK.

If you are comfortable with editing the file in terminal., make a backup of the file ..

```
sudo cp /etc/apt/sources.list ~/
```

then edit the file with

```
sudo nano /etc/apt/sources.list
```

and cursor down to the last line starting with "new" and remove it.

Ctrl + o (to write out)
Press the enter key 
Ctrl + x (to quit)

---

### Post by arthur24 on 2015-08-17
I've done what you said, and all the errors are gone. Can't believe it was this simple in the end.
No more errors, keyboard and mouse work fine at login.
I'm not sure if I can install anything yet but I'll try.

One problem that hasn't been fixed thus far is the fact that the Software Center is still not functioning. The Interface window does pop up this time instead of just showing the loading circle. But it immediately closes.

---

### Post by howefield on 2015-08-17
Cool.

I have never used Software Centre (bar a short period when it was new) for a whole number of reasons, I'd recommend apt-get in the terminal or synaptic. That is neither here nor there because Software Centre should work and your issue should be resolvable so if you are intent on using it, start a new thread with the relevant info including any error information that you can.

---

### Post by arthur24 on 2015-08-17
I myself haven't installed the majority through software center either. It also doesn't offer all the available software so I agree with you that it has it's drawbacks. I have used it regularly and I will first search for a fix myself before I open a new thread. Maybe I to end up discarding Software center alltogether. As a newcomer to Ubuntu it's quite handy with familiarizing all "available" software so I find it has some uses for me. 

Anyway, thanks for helping.

---

### Post by kansasnoob on 2015-08-17
> **arthur24 said:**
> I hope I'm not going to bring to others a massive headache, I got one myself at the moment. I am new to Ubuntu and over the last 1-2 weeks I accumulated some system errors. I tried to remedy the problems by looking online. But many solutions in my case lead to even more errors. 
So far the problems haven't yet lead to my system being inoperable. 
But it did lead to problems such as

-Software center being completely broken, it doesnt popup a window, just the loading circle.
-Can't install any packages whatsoever.
-My mouse and keyboard don't operate and I have to boot into recovery mode via Grub to operate the mouse and keyboard.

I got a total of 4 errors. It's likely somehow self induced by adding faulty software, but I can't remember what that might be unfortunately and I don't know how to check.

Error 1:    

Error 2:    

Error 3:    

Error 4:

I see you have this at least partially straightened out but I'm curious why you tried to run "do-release-upgrade" as shown in your error #2 ?????

Trusty is supported until 2019 and currently the only upgrade path from Trusty would be to Utopic which is already EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

