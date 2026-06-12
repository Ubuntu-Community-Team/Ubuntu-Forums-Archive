---
title: "[SOLVED] any idea when repositories are being opened for gutsy ???"
date: 2007-10-18
forum: General Help
---

### Post by adityakavoor on 2007-10-18
i have installed ubuntu 7.10 . cant install anything from synaptic 
when wil repos be opened for gutsy ?

---

### Post by Inxsible on 2007-10-18
I don't think the standard repos are ever "closed" unless the servers are down. Do you have an internet connection on that machine?

Did you do an upgrade or a fresh install ?

One other thing could be the amount of traffic hitting the repos since Gutsy just came out and everyone's trying to update at the same time increasing the load on the servers. In this case, you are out of luck. just give it some time and try again.

---

### Post by NilsE on 2007-10-18
> **adityakavoor said:**
> i have installed ubuntu 7.10 . cant install anything from synaptic 
when wil repos be opened for gutsy ?
If you just installed the release there is nothing new in the repos.  Should start seeing more within a few days when carry over bugs are fixed.

If you can't install anything additional then you may have a synaptic problem so try it from the command line.

---

### Post by adityakavoor on 2007-10-18
i do have internet connection  .. 
but sudo apt-get update results in 
```

aditya@ubuntu:~$ sudo apt-get update
[sudo] password for aditya:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done
aditya@ubuntu:~$ 

```

any  idea ????

---

### Post by adityakavoor on 2007-10-18
```
aditya@ubuntu:~$ sudo apt-get install ktorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ktorrent
aditya@ubuntu:~$ 

```

---

### Post by NilsE on 2007-10-18
Go into System/Administration/Software Sources and turn off the CD option on the main screen and see if that helps.

Also make sure all the repos are selected above the CD option and on the third party screen. Also check the options on the update screen.

---

### Post by adityakavoor on 2007-10-18
thanks mate ... working now

---

### Post by adityakavoor on 2007-10-18
another question : 

desktop effects was working fine with feisty
now it says desktop effects cannot be enabled 
i have an intel 965 mboard integrated grfics .. X3000 series

any idea ??

---

### Post by NilsE on 2007-10-18
Go into synaptic and make sure the xserver-xorg-video-intel video driver is installed.  Then look in your etc/X11/xorg.conf and make sure intel is selected as the driver.

If the answer to both is yes the re-install the intel driver.

---

### Post by adityakavoor on 2007-10-18
my answer to both questions is YEs

I reinstalled intel driver also

problem stil persists ... pls help

---

### Post by adityakavoor on 2007-10-18
i get this message ... please help
```

aditya@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:29a2' found 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by ezphilosophy on 2007-10-18
I'm in China and having the same problem (basically).  Possibly, other countries repositories are not up yet for gutsy?
To answer some of your questions:
When you run the update, it is only checking the cd-rom because it is the only thing enabled in your sources.list.  
Because of this, you also can't enable/download the driver and why xgl is "not present".
I just installed Gutsy and for some reason, the "install" decided to "#" all of the sources.  It said because the sources could not be verified (as they are down).

Hopefully, this will be fixed soon.

---

### Post by ezphilosophy on 2007-10-18
Seems others are having the same [problem]("http://ubuntuforums.org/showthread.php?t=579507&highlight=repositories"):

---

### Post by ezphilosophy on 2007-10-18
Hmm....  
I just removed the "cn" in all the "cn.archive.ubuntu.com" in my sources list and it still doesn't work.  Maybe the servers are overloaded?  
Clueless here in Shanghai.

---

### Post by adityakavoor on 2007-10-18
i got desktop effects to work .. see[ here]("http://ubuntuforums.org/showthread.php?t=579530")

---

### Post by ezphilosophy on 2007-10-18
Did you get your sources/repositories working yet?

---

### Post by adityakavoor on 2007-10-18
yeah .. after i enabled universe and multiverse .. i  get repo's to work

---

### Post by spliner on 2007-10-18
I have a fresh install.. same problem.. repositories don't respond.  My guess is that they are being slammed with traffic.

Gutsy still rocks!  I havn't had to touch the command line yet.. well other that to see why synaptic wasn't working well.

---

### Post by jusmurph on 2007-10-19
> **spliner said:**
> I have a fresh install.. same problem.. repositories don't respond.  My guess is that they are being slammed with traffic.

Thats certainly valid. Though you should always check your sources list.

---

### Post by adityakavoor on 2007-10-19
hmm yes .. servers seem to be jammed:(

---

### Post by adityakavoor on 2007-10-21
:popcorn:

everything is working fine now :)

---

