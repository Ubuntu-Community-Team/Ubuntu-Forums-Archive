---
title: "Only see 3+ gig on 4 gig installed"
date: 2007-09-01
forum: General Help
---

### Post by CD Baric on 2007-09-01
I have installed Ubunto Studio and Standard desktop on:

AMD Athlon&#8482; 64 X2 Dual-Core 6000+
Asus M2NPV-VM motherboard
4 pcs DDR II 1024MB PC6400 (800)

It is setup to run two large screen digital monitors and is fast like a bunny!

The problem is the large memory setting (4gig) has been disabled in the latest 32bit Ubuntu kernels and it's not something that can be enabled with a module.

Is it possible to download the Ubuntu Linux 2.6.20.16 sourcecode so as to build a new kernel that includes the large memory setting?

Is there a 32bit Ubuntu kernel that has this feature already enabled?

The full 4 gig shows up in my Slackware 12 installation because I built the kernel to include large memory.

Thanks,

CD Baric

---

### Post by Steveway on 2007-09-01
If you know the package name then you should be able to download the source with:
apt-get source <packagename>

---

### Post by tszanon on 2007-09-01
I've seen other post where people said it's normal. You have 4 GB, but since the BIOS uses some of that memory, the system shows you only what's left.
Using system log, you can see the memory map (see attachment). Converting those hexadecimal numbers into decimals, you can see how much memory you have. Let's take mine for example:
0 - 9F800 = 653312 bytes (638K)
100000 - 3FFF0000 = 1072627712 bytes = 0,99 GB

Since I have 1 GB RAM, 0,99 GB + 638K are usable by the system. That seems fine. Check you "usable" ram map and see if it's ok.

---

### Post by CD Baric on 2007-09-01
That's not it.

There is a setting in the Linux kerbel that allows a 32 bit kernel deal with large ammounts of memory - that switch is not enabled in the Ubuntu 32 bit kernel.

I am trying to find out how to correct that.

Thanks anyway.

CD Baric

---

### Post by CD Baric on 2007-09-02
OK - here is what I had to do.

Following a couple different Ubuntu HowTOs helped me build a custom kernel whereupon I made the change to hardwire the kernel for 64 gigs memory. I also changed the CPU to AMD Athlon but I doubt that will make much of a real difference.

I also had to re-install my custom nVidia video driver for my 8600 dual DVI video output. Incidently, running Ubunto Studio on two large screen LCD monitors is awesome - it is unfortunate the Ubuntu Studio project is run by such precious deceitful cretins.

I then ran against a new problem, my Restricted Drivers Manager complained about not having any information about the new kernel. I disabled the function since it didn't help with my nVidia driver anyway.

What would be real great would be for the Ubunto kernel team to just make that small change to the standard and low latency kernels. How about it kernel team?  ; )

While you kernel guys are at it, why not have a look at the 2.6.22 kernels? Some great refinements over .20 - just a thought.

CD Baric

---

### Post by Steveway on 2007-09-02
I'm running Gutsy Gibbon and this is what uname -r gives me:
> steveway@steveway-laptop:~$ uname -r
2.6.22-10-generic

---

### Post by CD Baric on 2007-09-02
"I'm running Gutsy Gibbon and this is what uname -r gives me: 2.6.22-10..."

OK - that is great.

How do you like Gutsy? 

Is it stable enough for you?

What improvements have you noted?

Thanks for your response.

CD Baric

---

### Post by bmorency on 2007-09-03
try to install the -server-bigiron (linux-image-2.6.20-16-server-bigiron) or just the -server version of your kernel. I think they have the built in options for the amount of ram you have.

---

### Post by CD Baric on 2007-09-03
"the -server version of your kernel"

OK - I am running a low latency kernel for Studio. I am pretty sure the requirments for servers is quite different than multimedia - especially the low latency issues.

Thanks for the feedback.

CD Baric

---

### Post by Steveway on 2007-09-03
It surprisingly didn't crash, yet.
For me it is stable but if you are not familar with the command-line then better stay away from it because updates could and propably will crash it.

---

### Post by bmorency on 2007-09-03
> **CD Baric said:**
> "the -server version of your kernel"

OK - I am running a low latency kernel for Studio. I am pretty sure the requirments for servers is quite different than multimedia - especially the low latency issues.

Thanks for the feedback.

CD Baric

if you do not want to try the server kernel than you should try the 64-bit kernel.

---

### Post by CD Baric on 2007-09-03
> **Steveway said:**
> It surprisingly didn't crash, yet.
For me it is stable but if you are not familar with the command-line then better stay away from it because updates could and propably will crash it.

I live for the command line.

CD Baric
Linux user since 1995.

---

### Post by CD Baric on 2007-09-03
> **bmorency said:**
> if you do not want to try the server kernel than you should try the 64-bit kernel.

Tried that but the user wants Flash in his browser and no 64 bit Flash yet.

Also don't know if there is a 64 bit Studio version.

Thanks,

CD Baric

---

