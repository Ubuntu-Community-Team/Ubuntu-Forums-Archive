---
title: "SimpleScreenRecorder not installing."
date: 2014-11-22
forum: General Help
---

### Post by ENunn on 2014-11-22
I reinstalled Ubuntu on my USB and tried to install SimpleScreenRecorder. Here is what I get.

```


ubuntu@ubuntu:~$ sudo apt-get install simplescreenrecorder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simplescreenrecorder : Depends: libavcodec54 (>= 6:9.1-1) but it is not installable or
                                 libavcodec-extra-54 (>= 6:9.16) but it is not installable
                        Depends: libavformat54 (>= 6:9.1-1) but it is not installable
                        Depends: libavutil52 (>= 6:9.1-1) but it is not installable
                        Depends: libswscale2 (>= 6:9.1-1) but it is not installable
                        Recommends: simplescreenrecorder-lib but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Can someone please help me?

Running Ubuntu 14.04 32-bit.

---

### Post by mc4man on 2014-11-22
Are you running a live session? 
"ubuntu@ubuntu:~$" is typical of that

Edit: assuming a live session & for others - 
Not all of the Ubuntu repos are enabled in a live session
Go to "Software & Updates" > make sure 1st. 4 sources are enabled, disable the cdrom option > scr1
Also while there go to Updates tab & make sure 1st 2 are enabled > scr. 2
Then reload sources or go sudo apt-get update

---

