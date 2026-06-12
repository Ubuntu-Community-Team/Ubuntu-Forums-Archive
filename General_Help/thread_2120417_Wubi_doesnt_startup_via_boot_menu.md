---
title: "Wubi doesnt startup via boot menu"
date: 2013-02-26
forum: General Help
---

### Post by NegusK on 2013-02-26
Hello, i installed wubi and it worked the first time i launched it, but when i try to start it again from the boot menu it just goes into a purple screen and then a black screen, afterwards theres nothing i can do except of restarting the computer and experiencing the same problem..

Is there anyway i can launch ubuntu in a way which it wont fail to startup ? 

thanks

---

### Post by bcbc on 2013-02-26
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it]("http://askubuntu.com/q/162075/14916")

Wubi specific part (first boot): [http://askubuntu.com/a/257917/14916](http://askubuntu.com/a/257917/14916)

---

### Post by NegusK on 2013-02-26
> **bcbc said:**
> [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it]("http://askubuntu.com/q/162075/14916")

Wubi specific part (first boot): [http://askubuntu.com/a/257917/14916](http://askubuntu.com/a/257917/14916)

I dont think they're talking about the same problem i have.
I **can** start up my computer, but not ubuntu, only windows

---

### Post by bcbc on 2013-02-26
> **NegusK said:**
> I dont think they're talking about the same problem i have.
I **can** start up my computer, but not ubuntu, only windows
The problem I linked to refers to problems starting Ubuntu. The symptoms can be any of: black screen, purple screen, frozen, corrupted display, successful login but laggy and sometimes icons/launchbar not present.

These are all the result of graphics drivers that do not have open source drivers (and therefore are not included by default). Booting with nomodeset gets you booted in a low graphics mode, and then you can look in "additional-drivers" and install the required closed source driver.

So I believe the link does apply to you.

---

