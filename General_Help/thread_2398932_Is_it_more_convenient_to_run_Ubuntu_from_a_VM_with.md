---
title: "Is it more convenient to run Ubuntu from a VM within Win10 ?"
date: 2018-08-19
forum: General Help
---

### Post by drpeppercan on 2018-08-19
I have always ran Ubuntu from a separate drive, but now I am wondering if it could be more convenient to run Ubuntu from a VM within Win10 ?
I have never tried a VM.

Thanks guys!

---

### Post by TheFu on 2018-08-19
It depends on what sort of workloads/tasks you use Windows & Ubuntu for.
Also depends on the hardware, whether virtualization would be a happy experience or not.

There is no single answer that fits for everyone.

---

### Post by drpeppercan on 2018-08-19
Hi TF!

I see. I suppose Ubuntu will run more smoothly when installed the normal way on its own drive, correct?
Being that the case I will no longer use it in a VM then

---

### Post by TheFu on 2018-08-19
> **drpeppercan said:**
> Hi TF!

I see. I suppose Ubuntu will run more smoothly when installed the normal way on its own drive, correct?
Being that the case I will no longer use it in a VM then

It depends on the hardware.  Some things run better inside a VM.  Please don't confuse the GUI most end-users look at with the OS.  The GUI is just another program in Unix systems. Nothing special and pretty trivial to swap out.  There must be 50 different GUIs maintained for Linux today.   10 are fairly popular, so how well the end-user thinks something runs (smoothly?), is very dependent on the GUI, which can mean next to nothing related to the true performance.

So, if you are having less than great GUI interactions **AND** you've followed the instructions for tuning a VM in that link and aren't satisfied, perhaps you need a lighter GUI? Or you might want to rethink using high-end graphics programs in a VM?

Completely up to you.

BTW, my daily use desktop, runs in a virtual machine that I access over the network.  The system hosting that VM has a CPU from 2010 and also runs about 20 other VMs concurrently.

But I don't use Windows as a VM host and I always run light desktops.

---

### Post by drpeppercan on 2018-08-19
Just out of curiousity, what purpose could you have for running 20 VMs? 
I am hoping you could give me ideas for using VMs ;)

---

### Post by TheFu on 2018-08-20
I'm into compartmentalization.  Systems that shouldn't be internet available are on different VMs and subnets from those that should.  I don't believe in using the same VM to merge client data like most SAAS people.  Each company gets VMs for their needs on separate subnets so client A can't access client B's stuff.

A few ideas:
[https://www.rosehosting.com/blog/self-hosted-alternatives/](https://www.rosehosting.com/blog/self-hosted-alternatives/)
[https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)

You can look up "self-hosted" services to find hundreds more. I've been thinking about setting up a social network just for my extended family using retroshare.

---

