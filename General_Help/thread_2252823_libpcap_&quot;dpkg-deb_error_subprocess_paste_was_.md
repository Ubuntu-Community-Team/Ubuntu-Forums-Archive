---
title: "libpcap: &quot;dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)&quot;"
date: 2014-11-14
forum: General Help
---

### Post by arico2 on 2014-11-14
I'm having problems with libpcap, similar to this thread:

[http://ubuntuforums.org/showthread.php?t=2244011&page=3](http://ubuntuforums.org/showthread.php?t=2244011&page=3)

unfortunately, after reading through it and trying to match up my machine's complaints with the posted solutions, I remain unable to resolve the issue.  this is my first post, and I accordingly apologize in advance for any errors or gauche oversights in requesting aid.

I tried to follow this tutorial:
[http://securit.se/2012/03/kompilera-reaver-ubuntu-12-04/](http://securit.se/2012/03/kompilera-reaver-ubuntu-12-04/)

and now when I try to run 
sudo apt-get update && sudo apt-get upgrade

it updates the sources fine, but then complains with this:

You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libpcap0.8 : Breaks: libpcap0.8:i386 (!= 1.4.0-2) but 1.5.3-2 is installed
 libpcap0.8:i386 : Breaks: libpcap0.8 (!= 1.5.3-2) but 1.4.0-2 is installed
 libpcap0.8-dev : Depends: libpcap0.8 (= 1.5.3-2) but 1.4.0-2 is installed

***

so I run 

bacon@ativ9:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.13.0-38-generic linux-image-extra-3.13.0-38-generic
  linux-signed-image-3.13.0-38-generic python-support
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpcap0.8
The following packages will be upgraded:
  libpcap0.8
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0 B/110 kB of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 266251 files and directories currently installed.)
Preparing to unpack .../libpcap0.8_1.5.3-2_amd64.deb ...
Unpacking libpcap0.8:amd64 (1.5.3-2) over (1.4.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libpcap0.8_1.5.3-2_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/man/man7/pcap-filter.7.gz', which is different from other instances of package libpcap0.8:amd64
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libpcap0.8_1.5.3-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bacon@ativ9:~$ 




Please advise me on how to resolve these issues!

Thank you in advance

---

### Post by mörgæs on 2014-11-16
Hi, welcome to the fora.

Does

> **arico2 said:**
> 

I tried to follow this tutorial [,,,]



mean that you compiled libpcap from source? If so, why?

---

### Post by matt_symes on 2014-11-16
Hi

Are you using Ubuntu 12.04 ? Is this an upgrade to 14.04 from 12.04 ?

How did you install libpcap ?

Kind regards

---

### Post by arico2 on 2014-11-18
Thanks for the response!

Yes, I believe I did try to compile it from source.  Honestly though, when complications or other errors arise I tend to deviate from guides (because it then appears that the guide is dealing with a different hw/sw setup, otherwise it would have foreseen my warning/error, right?)   So I apologize for a lack of clarity, my googling and attempts to resolve this have been decidedly non-linear.  

I've been using ubuntu almost exclusively since 2006, and have become increasingly comfortable with it, but still (obviously) have a lot to learn.  I personally learn best by actually doing things, trying things out, making mistakes, and figuring out where I went wrong.  Does that address the "why" aspect?

---

### Post by arico2 on 2014-11-18
Hi there.  I'm using 14.04, on a full install (wiped windows 8.1 and installed 14.04).  I believe libpcap was installed initially, but I screwed it up trying to follow the guide I linked to.  In trying to fix/restore the break, I googled my way to this thread:  
[http://ubuntuforums.org/showthread.php?t=2244011](http://ubuntuforums.org/showthread.php?t=2244011)
and followed ediblestarling's posts in hopes of a similar success story.  (Alas).

Is there a simple enough way to restore that particular component?

Thank you

---

### Post by mörgæs on 2014-11-18
I mean, why did you compile when the package is already in the repositories?

---

### Post by arico2 on 2014-11-18
mörgæs: I'm probably misunderstanding your response, because I fail to see how your question helps to resolve my issue.  As I said, I am trying to learn, and thought I made clear that it was not my intent to cause my system any problems.  Is my motivation or lack of expertise somehow relevant to the solution?   

In any case, I revisited the methods used in the other thread, and got closer to the solution.  Ultimately, I figured it out, using the methods in that thread to purge some of the whiny programs (e.g. tcpdump) and then using synaptic to purge two broken packages and marking libpcap0.8 for upgrade.  

I'm sorry to have taken up your time, thank you for your responses acknowledging my question.

I will mark this solved.

---

