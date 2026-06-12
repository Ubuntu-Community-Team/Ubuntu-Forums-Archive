---
title: "My audio/video programs cannot be reinstalled"
date: 2015-05-02
forum: General Help
---

### Post by matt174 on 2015-05-02
Hello. I posted [here]("http://ubuntuforums.org/showthread.php?t=2273287&p=13263010#post13263010"), and I can't fix the problem. This bad package installation occurred a while ago, and it wasn't done through the terminal. I'm not sure how to look up the old info. 

These are the programs I need to reinstall, along with the error messages apt-get spits back at me:

```
sudo apt-get install audacity
[sudo] password for matias: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacity : Depends: libavcodec54 (>= 6:9.1-1) but it is not going to be installed or
                     libavcodec-extra-54 (>= 6:9.13) but it is not going to be installed
            Depends: libavformat54 (>= 6:9.1-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

```
sudo apt-get install audacious
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacious : Depends: audacious-plugins (>= 3.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

```
sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mplayer : Depends: libavcodec54 (>= 6:9.1-1) but it is not going to be installed or
                    libavcodec-extra-54 (>= 6:9.11) but it is not going to be installed
           Depends: libavformat54 (>= 6:9.1-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Please let me know what I can do. I have a little experience with the terminal, but please keep the gloves on. 

Thanks very much
Matt

---

### Post by dino99 on 2015-05-02
That mean you are tying to install some packages (not trusted ones from third party) that are conflicting with the ubuntu version you are using.
A userfriendly package manager can be used : 'synaptic' to get details about packages

---

### Post by matt174 on 2015-05-02
When I try to Completely Remove audacity, this is what I get from Synaptic:

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory

---

### Post by matt174 on 2015-05-02
In synaptic, I try the Fix Broken Packages option, and this is what I get

[CODE]E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

[CODE/]

---

