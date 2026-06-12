---
title: "How to install Nokia Suite in Ubuntu 15.10"
date: 2015-11-24
forum: General Help
---

### Post by Manoj_Arun_Kumar on 2015-11-24
Hi ,

Can anyone please help me to install nokia suite for c2-00 in ubuntu system .

**sudo add-apt-repository ppa:upubuntu-com/mobile**
**sudo apt-get update**
[B]sudo apt-get install nokuntusp

I am tried above command, but when i go for update :

--------------------------------
Error : 
---------------------------------
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                                                                                                                                                                             
  404  Not Found [IP: 91.189.95.83 80]
W: Failed to fetch [http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found [IP: 91.189.95.83 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

# apt-get install nokuntusp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nokuntusp

---------------------------------------------------

can anyone please guide me to install nokia PC suite .
[/B]

---

### Post by Bucky Ball on 2015-11-24
*Thread moved to **General Help**.*

Welcome. ***Installations and Upgrades*** is for issues installing and upgrading the OS. :)

PS: Are you sure you actually need Nokia Suite? From a quick sniff about it seems users advise to plug it in with a USB and set the phone to 'Suite' mode and that's it. Have you researched the issue and whether you need this software at all?

---

### Post by Manoj_Arun_Kumar on 2015-11-25
Hi Bucky Ball,

I am not sure that I need nokia PC suite for ubuntu, 
but Nokia PC suite is requried for sending messages and access contacts which is achieved in windows .

So I need simillar kind of application for Ubuntu system .

I tried plug it in with a USB and set the phone to 'Suite' mode but only i can use my mobile as mobile broadband.

Thanks
MAK

---

### Post by grahammechanical on 2015-11-25
You are using 15.10 (wily). When we use the add-apt-repository command to add a PPA (Personal Package Archive) a URL is added to the list of software sources and the code name for our release is added as part of the URL because each release of Ubuntu has its own set of repositories.

There is not a PPA for upubuntu-com in the 15.10 (wily) repositories. The last PPA for this software was for Ubuntu 12.04. That is why you are getting the 404 Not found message for that URL and as the PPA is not in the 15.10 repositories apt-get cannot install nokuntusp and gives the message E: unable to locate package nokuntusp.

[https://launchpad.net/~upubuntu-com/+archive/ubuntu/mobile](https://launchpad.net/~upubuntu-com/+archive/ubuntu/mobile)

There is away around this. Go to System Settings>Software & Updates>Other Software tab and Edit the URL by changing the bit that reads 

> /ppa/ubuntu wily main

to

> /ppa/ubuntu precise main

And then updating/upgrading and try to install that package again. How well this work-around will work, I cannot say as that software is not being kept up to date with Ubuntu.

Regards.

---

### Post by Manoj_Arun_Kumar on 2015-11-26
Hi [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"),

I tried changing ppa as per your instruction .
apt-get Update was successful.

But when i try install i am getting following messages :
# apt-get install nokuntusp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nokuntusp : Depends: gambas2-runtime but it is not installable
             Depends: gambas2-gb-gui but it is not installable
             Depends: gambas2-gb-form but it is not installable
             Depends: gambas2-gb-pcre but it is not installable
             Depends: gambas2-gb-settings but it is not installable
             Depends: gambas2-gb-xml but it is not installable
E: Unable to correct problems, you have held broken packages.

#

Kindly help .


Thanks
MAK

---

### Post by Ricardo_Velasco on 2015-12-06
Greetings:

You are not should install the dependences. 
Is mixing incompatible bad idea for this distribution packages

> _I am researching but are not compatible with Ubuntu 15.10_
Sorry

But you can install and run Wine with an .exe file

If you try to install an earlier version to 15.10 .

A serious recommendation Actual Ubuntu 12.04 LTS or Ubuntu 14.04 LTS Current

---

