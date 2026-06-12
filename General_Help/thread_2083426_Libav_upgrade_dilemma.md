---
title: "Libav upgrade dilemma"
date: 2012-11-12
forum: General Help
---

### Post by PC_load_letter on 2012-11-12
Using 12.04 64bit, I just saw that several Libav components are up for a security update in the Update Manager but the boxes next to them are greyed out.
 
Through Synaptic, it seems that either **upgrading** or **removing** these Libav components will also remove DVDRip, ffmpeg, K9Copy and other stuff, what gives?!!! How could this happen and how do you think it can be fixed? 

Thanks.

---

### Post by cwsnyder on 2012-11-12
DVDRip, ffmpeg, K9Copy and your other applications are dependent on libav, and will have to be updated to the new release of libav _before_ you can get the libav upgrade, unless you want to break those applications.  That is what it is trying to tell you.

---

### Post by JMB74 on 2012-11-12
run in a terminal 
[B]
sudo apt-get install -suV libav-tools[/B]

What result do your get from that?

That given me a clean upgrade. But then I have the medibuntu repo enabled, so you may get something different?

---

### Post by PC_load_letter on 2012-11-12
> **cwsnyder said:**
> DVDRip, ffmpeg, K9Copy and your other applications are dependent on libav, and will have to be updated to the new release of libav _before_ you can get the libav upgrade, unless you want to break those applications.  That is what it is trying to tell you.

I know that, so now what, I upgrade the Libav, which will remove the aforementioned apps, THEN, I re-install the apps again?

---

### Post by PaulW2U on 2012-11-12
> **PC_load_letter said:**
> I know that, so now what, I upgrade the Libav, which will remove the aforementioned apps, THEN, I re-install the apps again?

No, that won't work.

I have the same problem in Ubuntu 12.04 and Lubuntu 12.10. Best just to leave it and wait for further updates to arrive.

---

### Post by PC_load_letter on 2012-11-12
> **JMB74 said:**
> run in a terminal 
[B]
sudo apt-get install -suV libav-tools[/B]

What result do your get from that?

That given me a clean upgrade. But then I have the medibuntu repo enabled, so you may get something different?

I have the Medibuntu repos added to my software sources. When I run the command you suggested, this is what I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libav-tools : Depends: libavcodec53 (>= 4:0.8.4-0ubuntu0.12.04.1) but it is not going to be installed or
                        libavcodec-extra-53 (>= 4:0.8.4) but 4:0.8.3ubuntu0.12.04.1+medibuntu1 is to be installed
               Depends: libavdevice53 (>= 4:0.8.4-0ubuntu0.12.04.1) but 4:0.8.3-0ubuntu0.12.04.1 is to be installed or
                        libavdevice-extra-53 (>= 4:0.8.4) but it is not going to be installed
               Depends: libavfilter2 (>= 4:0.8.4-0ubuntu0.12.04.1) but 4:0.8.3-0ubuntu0.12.04.1 is to be installed or
                        libavfilter-extra-2 (>= 4:0.8.4) but it is not going to be installed
               Depends: libavformat53 (>= 4:0.8.4-0ubuntu0.12.04.1) but 4:0.8.3-0ubuntu0.12.04.1 is to be installed or
                        libavformat-extra-53 (>= 4:0.8.4) but it is not going to be installed
               Depends: libavutil51 (>= 4:0.8.4-0ubuntu0.12.04.1) but it is not going to be installed or
                        libavutil-extra-51 (>= 4:0.8.4) but 4:0.8.3ubuntu0.12.04.1+medibuntu1 is to be installed
               Depends: libpostproc52 (>= 4:0.8.4-0ubuntu0.12.04.1) but 4:0.8.3-0ubuntu0.12.04.1 is to be installed or
                        libpostproc-extra-52 (>= 4:0.8.4) but it is not going to be installed
               Depends: libswscale2 (>= 4:0.8.4-0ubuntu0.12.04.1) but 4:0.8.3-0ubuntu0.12.04.1 is to be installed or
                        libswscale-extra-2 (>= 4:0.8.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```


> **PaulW2U said:**
> No, that won't work.

I have the same problem in Ubuntu 12.04 and Lubuntu 12.10. Best just to leave it and wait for further updates to arrive.

That was my thinking initially.

---

### Post by JMB74 on 2012-11-12
Well, I get this. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
   libavcodec53 (0.8.4-0ubuntu0.12.10.1)
   libavdevice53 (0.8.4-0ubuntu0.12.10.1)
   libavfilter2 (0.8.4-0ubuntu0.12.10.1)
   libavformat53 (0.8.4-0ubuntu0.12.10.1)
   libavutil51 (0.8.4-0ubuntu0.12.10.1)
   libpostproc52 (0.8.4-0ubuntu0.12.10.1)
   libswscale2 (0.8.4-0ubuntu0.12.10.1)
The following packages will be REMOVED
   libavcodec-extra-53 (0.8.3.6ubuntu1+medibuntu1)
   libavdevice-extra-53 (0.8.3.6ubuntu1+medibuntu1)
   libavfilter-extra-2 (0.8.3.6ubuntu1+medibuntu1)
   libavformat-extra-53 (0.8.3.6ubuntu1+medibuntu1)
   libavutil-extra-51 (0.8.3.6ubuntu1+medibuntu1)
   libpostproc-extra-52 (0.8.3.6ubuntu1+medibuntu1)
   libswscale-extra-2 (0.8.3.6ubuntu1+medibuntu1)
The following NEW packages will be installed
   libavcodec53 (0.8.4-0ubuntu0.12.10.1)
   libavdevice53 (0.8.4-0ubuntu0.12.10.1)
   libavfilter2 (0.8.4-0ubuntu0.12.10.1)
   libavformat53 (0.8.4-0ubuntu0.12.10.1)
   libavutil51 (0.8.4-0ubuntu0.12.10.1)
   libpostproc52 (0.8.4-0ubuntu0.12.10.1)
   libswscale2 (0.8.4-0ubuntu0.12.10.1)
The following packages will be upgraded:
   libav-tools (0.8.3-6ubuntu2 => 0.8.4-0ubuntu0.12.10.1)
1 upgraded, 7 newly installed, 7 to remove and 1 not upgraded.
```

Not going to do the upgrade now, as I want to keep the mediuntu package with the extra codecs enabled.

Hopefully the medibuntu team will repackage this newer version for their repos in the coming days.

---

### Post by PaulW2U on 2012-11-13
As expected, further updates were released a couple of hours ago that allowed the three that were held back to be installed.

I'm now fully updated on Ubuntu 12.04 and Lubuntu 12.10.

---

### Post by PC_load_letter on 2012-11-13
Yep, updating right now, thread marked as solved!

---

