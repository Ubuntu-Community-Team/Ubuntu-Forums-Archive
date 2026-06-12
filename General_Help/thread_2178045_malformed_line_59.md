---
title: "malformed line 59"
date: 2013-10-01
forum: General Help
---

### Post by maryam2 on 2013-10-01
Hello 
I got this error when I add deb [http://dl.google.com/linux/talkplugin/deb/stable](http://dl.google.com/linux/talkplugin/deb/stable) main in soft center.
(   E: Malformed line 59 in source list /etc/apt/sources.list (dist parse) 
 E: The list of sources could not be read. )

Now I can't open my software center.
I added deb [http://dl.google.com/linux/talkplugin/deb/stable](http://dl.google.com/linux/talkplugin/deb/stable) main because when I did update before adding that I got some error and something not found.
please help me

---

### Post by Bashing-om on 2013-10-01
maryam2; Hi !

This thread is marked as "solved" . Did you resolve your predicament ?

Else: Show us the referenced file for advisement; do terminal code:
```

cat -n /etc/apt/sources.list

```
and place that out put between code tags;
tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]you can do this
[/INDENT][/INDENT]

---

### Post by maryam2 on 2013-10-01
No it isn't solve.
and
>      1    # deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted
     6    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted
    11    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal universe
    17    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal universe
    18    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates universe
    19    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal multiverse
    27    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal multiverse
    28    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates multiverse
    29    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports main restricted universe multiverse
    37    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports main restricted universe multiverse
    38    
    39    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted
    40    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted
    41    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security universe
    42    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security universe
    43    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security multiverse
    44    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
    57    deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) lucid main
    58    deb-src [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) lucid main
    59    deb [http://dl.google.com/linux/talkplugin/deb/stable](http://dl.google.com/linux/talkplugin/deb/stable) main
    60    deb-src [http://dl.google.com/linux/talkplugin/deb/stable](http://dl.google.com/linux/talkplugin/deb/stable) main
    61    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed restricted main multiverse universe

---

### Post by Bashing-om on 2013-10-01
maryam2;
Add a space :
> 
59 deb [http://dl.google.com/linux/talkplugin/deb/stable](http://dl.google.com/linux/talkplugin/deb/stable) main
60 deb-src [http://dl.google.com/linux/talkplugin/deb/stable](http://dl.google.com/linux/talkplugin/deb/stable) main

between "/deb/" and "stable" in both lines:
That space is a delimiter and needed to separate the fields.
Safety first, always remember to make a backup first, prior to editing any file.
and run:
```

sudo apt-get update
sudo apt-get upgrade

```
and advise on results.

[INDENT][INDENT]should workie great last long time[/INDENT][/INDENT]

---

### Post by maryam2 on 2013-10-01
Thank you very much.
Excuse me I have the other question please. I had 44o error about the repository that I added it because I need it for installing a new software. 
>    	 	 	 	   W: Failed to fetch [http://ppa.launchpad.net/otb/orfeotoolbox-stable-ubuntugis/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/otb/orfeotoolbox-stable-ubuntugis/ubuntu/dists/quantal/main/source/Sources)  404  Not Found 
  
 W: Failed to fetch [http://ppa.launchpad.net/otb/orfeotoolbox-stable-ubuntugis/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/otb/orfeotoolbox-stable-ubuntugis/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found 
  
it foeced me to untick and disable this repository from "other software" in my "software center" to eliminate the error.
But my question is if it will make ill the installation process of my software? I mean it will disturb the process of new software installation?
Thanks.

---

### Post by Bashing-om on 2013-10-01
maryam2;

Generally a "404" error from a PPA is as a result of the PPA no longer maintained or the server hosting the package is out of service.

Now if that PPA is no longer maintained, then yes disable the source and there will be no adverse effects to the system. That "source" will not be processed.

Post back to me the contents of the source file in question and I will make some investigations.

Now, is this the same question you have in an alternate thread (have not had time to look)??...we are going to get slapped on the wrist for duplicating threads/efforts and  I do not want my relationship with the admins to suffer and they take action.

Tell me then to meet you in the other thread.

[INDENT][INDENT]I will be there
[/INDENT][/INDENT]

---

### Post by maryam2 on 2013-10-02
Hi.
I don't want to bother you. yes that is my thresd. and I add this to my repository:

> sudo apt-add-repository ppa:ubuntugis/ubuntogis-unstable
sudo apt-add repository ppa:otb/orfeotoolbox-stable-ubuntugis
I want to install LUMASS software but before that I must install the other software like
QT
GDAL
VTK
ORFEOTOOLBOX
LP_SOLVE

THANKS

---

### Post by Bashing-om on 2013-10-02
maryam2; 
It can be "no bother" I volunteer myself and my time in order to help. To help in any capacity is the primary reason for the existence of this forum.
Policy: there are no dumb questions.

On topic: I have caught up on your alternate thread and looks as if you are in good company and are well taken care of.
I will continue to monitor THAT thread and consider this thread as a done deal and closed out.

[INDENT][INDENT]see you there
[/INDENT][/INDENT]

---

