---
title: "Blackboard Learning System"
date: 2008-02-15
forum: General Help
---

### Post by zorkerz on 2008-02-15
The Blackboard Learning System (formerly WecbCT) is used by my school to host class content including, discussions, articles, resources, email, schedule, and assignment hand in. Basically all class content information. 

It appears to be a pretty popular platform for schools. Does anyone else need to use it?

Blackboard requires java and thats where all my problems begin. I have posted a bit on this [here]("http://ubuntuforums.org/showthread.php?t=680856").

Basically the only why I have been able to access Blackboard is using firefox 2 without sun-java or icedtea java7 and all there plugins/dependencies installed. This worked fine for me untill hardy upgraded to firefox 3.0b3. Now I cannot access Blackboard in ubuntu. I have tried with sun-java or icedtea java7 installed and without to no avail.

Is anyone having a similar problem?
Has anyone solved this or have any ideas how to solve this?

I should add that I am using a 64 bit install of hardy upgraded from gutsy.

---

### Post by FuturePilot on 2008-02-15
Currently Java is broken in Hardy.
[http://ubuntuforums.org/showthread.php?t=621864]("http://ubuntuforums.org/showthread.php?t=621864")

---

### Post by zorkerz on 2008-02-15
Yep sun's java for linux is buggy and has security vulnerabilities as far as i have heard. That is why i would prefer to use icedtea. Unfortunately currently neither work. It just seems odd to me that what worked with firefox 2 does not now with 3.

---

### Post by zorkerz on 2008-02-16
I have a workaround for now. I downloaded firefox 2 from mozilla and extracted it in the /opt folder. When i need to use blackboard i run firefox2 with '/opt/firefox/firefox'.
Its dirty but gets the job done.

---

### Post by mrgnash on 2008-03-11
I am having the same problem with Epiphany (see screenshot below), but not Firefox 3 when run from the binary extracted from the tar.gz package. I don't have icedtea or java installed -- although I previously had icedtea installed, it didn't seem to make any difference.

[img]http://img256.imageshack.us/img256/4593/screenshothr9.png[/img]
Epiphany/Firefox 3 (installed from apt)

[img]http://img81.imageshack.us/img81/167/screenshot1nb5.png[/img]
Firefox 3 Beta 4 (installed from tarball)

---

### Post by zorkerz on 2008-03-12
for me:
The firefox 3b3 is still unable to use blackboard
I have installed a separate install of firefox2 and newly firefox3b4 With luck mine will work when 3b4 hits the hardy repos

---

### Post by mrgnash on 2008-03-12
> **zorkerz said:**
> for me:
The firefox 3b3 is still unable to use blackboard
I have installed a separate install of firefox2 and newly firefox3b4 With luck mine will work when 3b4 hits the hardy repos

Have you tried it with Epiphany?

---

### Post by zorkerz on 2008-03-12
never needed to

---

### Post by Whiffle on 2008-03-12
Huh thats really weird.  My school uses BB as well, but I have never had an issue with it under any browser.  I just tried in in Konqueror and "Minefield 3 Beta 4", both under Arch.  

Maybe try getting some non-ubuntu java versions and try those?

---

### Post by zorkerz on 2008-03-12
Im having java problems on a couple fronts. I have been waiting on a new release of jrisk that just came out but as of yet i have been unable to start it. This could easily just be me not knowing what im doing. 

I have had icedtea7, sun-java6, sun-java5, all from the repos and sun-java6 (32 and 64 bit) from sun installed. None have allowed me to access BB or jrisk. 

FF2 and FF3b4 seem to work for BB without any java installed only. This could just be because I have not set them as the default browser.

Do i need to use a 32bit browser. I people used to have to do that alot but I would really rather not.

---

### Post by peterroots on 2008-03-13
using Kubuntu7.10 and firefox2.0.0.12 with sun-java6 and sun-java6-pluggin seems to work fine for me (although occasionally a java based page in BB or other sites freezes, not often enough to be a problem though)

---

### Post by zorkerz on 2008-03-14
With the update to firefox 3b4 in hardy this problem is fixed for me! BB works both with and without icedtea-java7 (although without it does tell me i need to install it).
alright!
elias

---

