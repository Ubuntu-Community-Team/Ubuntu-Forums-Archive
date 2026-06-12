---
title: "Some people said that you can have in ubuntu what backtrack has"
date: 2012-11-01
forum: General Help
---

### Post by doctorcobrado on 2012-11-01
ive just read some tutorials about this and it was called backtrack tools... i dont know if its real but it looks like amazing if you can i can use my ubuntu for penetration testing

---

### Post by localhost8080 on 2012-11-01
I wrote about this a while ago in my blog:

[http://jonathansblog.co.uk/install-backtrack-repo-in-ubuntu](http://jonathansblog.co.uk/install-backtrack-repo-in-ubuntu)

ive not done it for a while, so not sure if it still works, but it was pretty cool.
not everything works as expected though, so now I start from backtrack and add in the ubuntu repositories and install the extra things I want from there

---

### Post by Cheesemill on 2012-11-01
Adding the BackTrack repositories to Ubuntu or vice-versa is not recommended and likely to break your system.

A large number of the tools you get with BackTrack are already available in the standard Ubuntu repositories.

Whenever I need to do some pen-testing I just fire up a BackTrack VM, I find this to be the easiest solution.

---

### Post by localhost8080 on 2012-11-01
> **Cheesemill said:**
> 
Whenever I need to do some pen-testing I just fire up a BackTrack VM, I find this to be the easiest solution.

yeah, I do this too :D

it is ok to mix repos about If you know how to fix things when they break!
but I wouldnt recommend it to most people!

---

### Post by doctorcobrado on 2012-11-02
i dont use virtual machines for backtrack because my mobile broadband and even wifi wont work

---

### Post by Cheesemill on 2012-11-02
That's because VM's don't see your actual hardware.

A BackTrack VM will have a virtual wired ethernet adapter which is linked to the adapter(s) on your host OS.
If you have networking on the host operating system then you ***will*** have networking on the guest VM.

Another option is to use USB passthrough so that your VM does see the physical adapters on your host machine.

Also bear in mind that ***all*** networking is disabled on purpose on any BackTrack installation for stealth reasons, you have to explicitly start networking if you wish to use it.

---

