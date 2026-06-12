---
title: "Nvidia Driver Can Not be Found?"
date: 2019-04-02
forum: General Help
---

### Post by loubar on 2019-04-02
Hello,

I am new to ubuntu and linux in general and I was having some issues trying to install some drivers. I found the version I need (have a gtx 1080), but it says the package could not be found?

message issue here:
loubar@Lou-desktop-mainframe:~$ sudo apt-get install nvidia-driver-418.56
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-driver-418.56
E: Couldn't find any package by glob 'nvidia-driver-418.56'
E: Couldn't find any package by regex 'nvidia-driver-418.56'
loubar@Lou-desktop-mainframe:~$ 

any help with this would be greatly appreciated!
Thanks,
loubar

---

### Post by shag00 on 2019-04-02
Do you have this is software sources?
[http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

---

### Post by loubar on 2019-04-02
I don't think I understand you question.
As I said earlier, I'm new to this (comming from windows 10) and I have had a fresh install
with auto drivers installs I believe
but when I check to see what driver version I have it says 390.
I don't know if that would be helpful or not, I did read something about using an nvidia-x server settings, but was reading about issues with 18.04lts
of which, is my current version.

---

### Post by loubar on 2019-04-03
nevermind, I got it to work.
just said 418 instead of 418.56.

---

