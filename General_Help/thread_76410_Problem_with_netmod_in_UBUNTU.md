---
title: "Problem with netmod in UBUNTU"
date: 2005-10-15
forum: General Help
---

### Post by Bad guy on 2005-10-15
Hi everyone! 
I'm using a new UBUNTU 5.10, but the os does not seem to connect to the internet.. I did the following (suggested by the majority of the ones i asked): 

I created the /dev/usb folder : sudo mkdir /dev/usb

I typed: sudo mknod /dev/usb/ttyACM0 c 166 0 (it is connected via USB in the first port, i am sure of that)

then tried the KPPP
, but while my modem responds and makes the call, the ppd deamon dies unexpectedly with a log message like the following: 
Oct 12 17:01:17 localhost pppd[8635]: The remote system is required to authenticate itself 
Oct 12 17:01:17 localhost pppd[8635]: but I couldn't find any suitable secret (password) for it to use to do so. 
Oct 12 17:01:17 localhost pppd[8635]: (None of the available passwords would let it use an IP address.) 

Anyone knowing what i should do? 
i have two screenshots of my modem onfiguration [http://users.ntua.gr/el02045/Screenshot-1.GIF](http://users.ntua.gr/el02045/Screenshot-1.GIF) and [http://users.ntua.gr/el02045/Screenshot-2.GIF](http://users.ntua.gr/el02045/Screenshot-2.GIF) 

It seems like my username/password is not correct but i have checked it and i cannot be mistaken..

---

### Post by blastus on 2005-10-24
I had the exact same problem. See this thread [wvdial and gppp work, kppp doesn't.](http://ubuntuforums.org/showthread.php?p=438882)

---

### Post by ikd69 on 2005-10-24
[QUOTE=Bad guy]Hi everyone! 
I'm using a new UBUNTU 5.10, but the os does not seem to connect to the internet.. I did the following (suggested by the majority of the ones i asked): 

I created the /dev/usb folder : sudo mkdir /dev/usb

I typed: sudo mknod /dev/usb/ttyACM0 c 166 0 (it is connected via USB in the first port, i am sure of that)
[/QUOTE]

Ahh, the perenial problem of hooking up a USB netmod to the Greek telephone system.  In all my attempts using various distros (including Mandrake and Mandriva, SUSE, Redhat and Fedora) I was not able to do that.  

Others say that if your netmod is serial rather than usb, you may be luckier.  In the end I upgraded my line to ADSL and solved the problem.

Cheers,

IKD:smile:

---

### Post by afonic on 2005-10-24
Yeh, I remember I had to use the Serial connection to get it work in Suse, but now I have ADSL, so I haven't tried in Ubuntu.

Have a look at HELLUG mailing lists, I found the solution there.

---

### Post by Claus7 on 2006-11-04
You might be interested in looking the following :
[http://ubuntuforums.org/showthread.php?t=128573&highlight=netmod](http://ubuntuforums.org/showthread.php?t=128573&highlight=netmod)

---

