---
title: "Trying to install VPython"
date: 2013-01-10
forum: General Help
---

### Post by jmoney47 on 2013-01-10
I am trying to install VPython on my machine (Ubuntu 12.10 64-bit), but it says I need gtkglextmm 1.2.  However, if I try to install it by typing "sudo apt-get install libgtkglextmm-x11-1.2-dev" I get an error saying

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtkglextmm-x11-1.2-dev : Depends: libgtkglext1-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

What can I do to fix this?

---

### Post by bogustrumper on 2013-01-10
You can try running apt-get with the -f flag. That'd be my first suggestion.

Though, it's worth pointing out that Ubuntu 10.10 is an old release which is no longer supported. That means that nobody is officially maintaining software for it, so you're kind of on your own. Most Ubuntu releases are supported for 18 months, and then every 2 years they make a "long term support" (LTS) release that they'll support for longer (3 years for the Desktop, 5 years for the server).

If I were in your shoes, this kind of problem would be the thing that would convince me to upgrade, at least to the next LTS version (which is 12.04). I'd recommend looking into that, since you'll likely run into more and more things which just won't install easily.

---

### Post by jmoney47 on 2013-01-10
My fault, I meant to write 12.10 haha.  I tried using the -f flag, but nothing different happened.  Is there a special way that I am supposed to use it?

---

### Post by bogustrumper on 2013-01-11
Hmm. Sometimes -f makes it "just work".

I was googling around for things, and came across this page. Probably worth a look:

[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)

Couple tips that they mention which could be relevant: make sure you've got the "restricted" and "universe" repositories enabled; make sure you're up to date (sudo apt-get update && sudo apt-get upgrade).

---

