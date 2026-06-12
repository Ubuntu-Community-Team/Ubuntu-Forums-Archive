---
title: "iBus problem: words scrambled when CPU is at 100% usage"
date: 2014-06-20
forum: General Help
---

### Post by fprietog on 2014-06-20
Hello, this is my first post :)

First of all I'm not really new at Unix/Linux world but my last try to use it was almost eighteen years ago, when I was a student, studing Unix with a distribution called AIX in an IBM RISC6000 machine. I tried to use it at home with a linux distribution called slackware, with a very rudimentary X-Window system... And I ended using MS Windows...

Now I have returned to linux because of Windows XP's end of support (as many others, I guess) and having a quite old computer. I checked the options for my computer and I ended choosing lubuntu. And I don't regret at all, very good and robust operative system, and really easy to use and maintain.

I'm re-learning about shell-scripts, C and that kind of things and I even wrote several little programs to automate tasks. Nowadays it's very easy to re-learn since there are lots of good and indexed info in the net.

Well, after the introduction, my problem. I found a way to solve it but I want to know if it can be solved in a better way.

It's related with iBus input method (the default input method in lubuntu 14.04 LTS x86_64 distribution I'm using). Sometimes when my computer is at 100% of CPU usage, everything that I wrote using the keyboard is sent to the screen scrambled. For instance, if I wrote ROUTER the screen shows RUOTRE, scrambled (it's not me, I swear). The curious thing is that no letter is lost, but the order shown is not the correct...

It only happens when the CPU is at 100%.

I "solved" it changing the input method to another, SCIM, that works just as expected even at 100% of CPU. But I wonder if it's just a matter of changing a configuration parameter of iBus to give more buffer or something like this... I really prefer to use the default method instead of an alternative because of support. I really only use it with a simple spanish mapped PS2 keyboard.


Thanks and best regards.

---

### Post by bapoumba on 2014-06-20
ibus has several bugs lying around on lubuntu.
One of them I am following because it prevents text input in Chromium : 
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)

I also had this when I first installed and was stuck with a US keyboard :
[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635)

I have not looked at every one of them, but may be fill another bug report ?
[https://bugs.launchpad.net/ubuntu/+source/ibus](https://bugs.launchpad.net/ubuntu/+source/ibus)

---

### Post by fprietog on 2014-06-20
Thanks for the links. I'll check that bug tracker in order to know if my problem is posted.

---

### Post by bapoumba on 2014-06-24
Please check this bug again, and in particular the last post. Will test it later on.
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648/comments/21](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648/comments/21)

---

### Post by fprietog on 2014-06-27
I've checked that bug but I'm afraid it's not the same I described. But I've try to test it too installing the chromium version from the repo, but it's an old version (?), so the testing  isn't valid.

---

### Post by bapoumba on 2014-06-27
Which Ubuntu version are you using and which Chromium version ?

---

### Post by fprietog on 2014-06-29
lubuntu 14.04 LTS x86_64
chromium 34.0.1847.116 (from ubuntu repo) 

There is a comment in the bug stating that it's fixed in newer chromium versions (from non official ubuntu repo):
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648/comments/17](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648/comments/17)

---

