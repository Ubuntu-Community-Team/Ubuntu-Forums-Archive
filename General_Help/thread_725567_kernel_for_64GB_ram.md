---
title: "kernel for 64GB ram"
date: 2008-03-15
forum: General Help
---

### Post by chazn85 on 2008-03-15
hey i just wanted to know how i can get a kernel to support all my 6gb of ram in 32 bit ubuntu.  I know its possible i have tried 64 bit but its useless for me and to much of a pain.

any help would be appreciated

---

### Post by p_quarles on 2008-03-15
As far as I can tell, Ubuntu does not distribute a bigmem 32-bit kernel. Your options would be to either roll your own, or switch to a distribution that does ship bigmem kernels (such as Debian).

---

### Post by chazn85 on 2008-03-15
i thought you could enable 64 ram support with something like a sudo apt-get cache search and search for some sort of i686 version

---

### Post by p_quarles on 2008-03-15
> **chazn85 said:**
> i thought you could enable 64 ram support with something like a sudo apt-get cache search and search for some sort of i686 version
Well, like I said, the kernel-type you want is called "bigmem." And as far as I know, Ubuntu does not package such a kernel. You should search the repositories yourself, of course, to doublecheck.

---

### Post by chazn85 on 2008-03-15
is there s way to do it via the command line. im a bit of a noob as far as ubuntu is concerned.  more solaris command line for me

---

### Post by p_quarles on 2008-03-15
```
apt-cache search bigmem
```

---

### Post by PurposeOfReason on 2008-03-15
It would be far easier to use 64bit. What problems did you have with it?

---

### Post by chazn85 on 2008-03-15
thanks mate doesnt look to be in the repos.

did try 64 bit but its very buggy.  might try the server kernel or failing that debaiin which does have big mem support

Any suggestions?

---

### Post by chazn85 on 2008-03-15
the problems i had flash (couldnt get it working at all even with the workaround) songbird wouldnt play mp3 (now in 32 bit working flawlessy with gstreamer plugins) firefox 64 terrible IMHO.  

I am more used to debain but have got a new system and used to have 64 bit support with the new kernel type.

---

### Post by p_quarles on 2008-03-15
The server kernel isn't going to support bigmem either. The repositories are exactly the same for the desktop and server editions.

The 64-bit version of Ubuntu is no more buggy than the 32-bit version (I've used both). If you encountered problems, they were likely with the setup rather than with any outstanding bugs. If you'd like to enumerate the problems, people might be able to point you in the right direction.

---

### Post by p_quarles on 2008-03-15
> **chazn85 said:**
> the problems i had flash (couldnt get it working at all even with the workaround) songbird wouldnt play mp3 (now in 32 bit working flawlessy with gstreamer plugins) firefox 64 terrible IMHO.  

I am more used to debain but have got a new system and used to have 64 bit support with the new kernel type.
Oh, okay.

The Flash problem has since been fixed. Songbird is in Alpha, so the fact that it doesn't work isn't considered a bug.

---

### Post by chazn85 on 2008-03-15
yes i found 64 bit very buggy in contrat to 32 bit working straight out of the box so to speak .  spent 3 hours trying to get mp'3 playing in 64 bit via songbird.  got flash to work somewhat in 32 bit firefox under 64 bit.  all in all for my system i think 32bit is better so far,

trying to move away from windows completly which is ridicoulsy buggy, as im sure everyone would atone with.

---

### Post by oldelfy on 2008-06-03
Sorry to revive the slightly old thread.

> **p_quarles said:**
> As far as I can tell, Ubuntu does not distribute a bigmem 32-bit kernel. Your options would be to either roll your own, or switch to a distribution that does ship bigmem kernels (such as Debian).

when you say "roll your own" do you mean recompile with high memory support enabled? I have 32bit dual xeons so 64bit os isn't really an option. Does anyone know a guide for recompiling the kernel for this?

---

### Post by jreinis on 2008-06-10
> **p_quarles said:**
> The server kernel isn't going to support bigmem either. The repositories are exactly the same for the desktop and server editions.

The 64-bit version of Ubuntu is no more buggy than the 32-bit version (I've used both). If you encountered problems, they were likely with the setup rather than with any outstanding bugs. If you'd like to enumerate the problems, people might be able to point you in the right direction.

64 bit Ubuntu as many other lack support from third-parties.

Officials: 

Sun Java:

The 64-bit versions of J2SE 1.4.1 do not include the Java Plug-in and Java Web Start products. 
The 64-bit versions of J2SE 1.4.1 do not have an installer application. These versions are available only as a tar bundle.

For Adobe [Macromedia] Flash I do not say - all internet is full of that.

---

### Post by twright on 2008-06-10
just add the debian repositories to your sources list then search for the bigmem kernel

---

### Post by p_quarles on 2008-06-10
> **jreinis said:**
> 64 bit Ubuntu as many other lack support from third-parties.

Officials: 

Sun Java:

The 64-bit versions of J2SE 1.4.1 do not include the Java Plug-in and Java Web Start products. 
The 64-bit versions of J2SE 1.4.1 do not have an installer application. These versions are available only as a tar bundle.

For Adobe [Macromedia] Flash I do not say - all internet is full of that.
Those are not bugs. A bug is a programming error. Calling an OS "buggy" because an application hasn't been ported to it is insulting to the developers who debugged that OS. 

Not using 64-bit Ubuntu due to the lack of Java or Flash is reasonable (even though there are easy workarounds for those two in particular). Calling 64-bit Ubuntu "buggy" for those reasons is inaccurate.

---

### Post by zakiwi on 2008-06-12
I think that this issue is being badly handled:

The reality is that a bigmem kernel would make a huge difference.  

I've been working on 64bit 7.10 for 6 months (Quad core CPU and 8GB ram) and it's been more or less fine.  Sure there are the occasional problems, but it's been acceptable, **however** I've now been presented with a project where I am being forced (due to application level instability on 64bit that is out of my hands) to a 32bit platform and the thought of going down to 3.5GB RAM is not comforting at all.

Ubuntu is a great platform, but quite frankly, if I'm forced to 32bit I would want to have all my RAM available ... I can't see any reason not to offer a bigmem kernel, and I'm more likely to look at Debian at this stage than sacrifice the RAM available to me.

If there is a good reason why such a kernel can't be provided then I'd love to hear it before reinstalling my machine.

---

