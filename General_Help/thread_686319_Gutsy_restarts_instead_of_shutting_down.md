---
title: "Gutsy restarts instead of shutting down"
date: 2008-02-03
forum: General Help
---

### Post by bjh_bjh864 on 2008-02-03
Hi, I have been having this problem since I installed Gutsy and it's becoming quite the pain. I have found no way to shut down my computer when using Gutsy. The shutdown button, halt or shutdown in command line, none of it works. I have to either boot to something else, or manually shut it off.

I had Feisty before this and it never gave me problems, and I can still boot to it and it's fine.

A side note: The restart is different than a normal restart, normally nothing in my computer turns off, it just restarts. With Gutsy everything shuts off for a second or two before starting up again.

Information:
Ubuntu 7.10 - 2.6.22-14 kernel
ASUS P5GD2-X motherboard

---

### Post by notman on 2008-02-29
I've been having the same issue. Sorry, I don't have any solutions, but I wanted to offer a confirmation of the problem. Restart does the same thing; it never shuts down complete (to get  a system post). I just get the one second flash to bash, then returns to the login screen. 

Again, using Gutsy

---

### Post by philinux on 2008-02-29
[http://ubuntuforums.org/showthread.php?t=653225](http://ubuntuforums.org/showthread.php?t=653225)

This might help.

---

### Post by bjh_bjh864 on 2008-03-04
@notman: My system actually shuts down, it just starts up again, starting with a normal POST

I have tried both

sudo poweroff -f
sudo shutdown -P now

and neither work to fix my problem.

Interesting note: The hibernate feature shuts down my computer just fine and has been working flawlessly. I might have to look into the differences between the hibernate shutdown and a normal shutdown.

This problem really is a pain so if anybody has any ideas please let me know, the only way to power off my computer is to pull the power cord or boot to Windows and shut down from there, or hibernate all the time.

---

