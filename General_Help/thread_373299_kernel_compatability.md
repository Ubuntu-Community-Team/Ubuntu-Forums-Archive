---
title: "kernel compatability"
date: 2007-03-01
forum: General Help
---

### Post by frogotronic on 2007-03-01
Hi,

  If i'm going to recompile my kernel (dapper drake, currently 2.6.15-28-686), which one should I download?  Can I compiled the latest and greatest (i.e. 2.6.20+) or will that not work with dapper?  Is there a guidline for choosing a kernel version?  For example could I compile a kernel version that normally would be used for edgy, or am I asking for problems?

Thanks,
- CH

---

### Post by an.echte.trilingue on 2007-03-01
Probably not a good idea to do this unless you have a specific reason to do this.  A better approach is to recompile the kernel version you are currently using with patches for the specific features you are trying to get.

What feature are you looking for, in particular?

---

### Post by frogotronic on 2007-03-01
Hi,

I'd like to include Suspend2 with the nVIDIA driver (1.0-8776) to get hibernate working.


But...according to this link, I can just compile the kernel without the nVIDIA modules and then re-install?

[http://www.ubuntuforums.org/showpost.php?p=986819&postcount=39](http://www.ubuntuforums.org/showpost.php?p=986819&postcount=39)

But, other guides state that I MUST compile in the nVIDIA drivers.  I'm confused.  Do people compile in the nVIDIA drivers because access to the restricted repos with a custom kernel is no longer possible, or for other reasons?

- CH

---

### Post by an.echte.trilingue on 2007-03-01
I have never gotten suspend2 working on my ATI card, regardless of what I compile into the kernel, but I was under the impression that you need to compile with the drivers.  The best advice I have for you is to try the easier approach, and if that doesn't work, do the more complicated one.

Honestly, it is probably less work to just upgrade to feisty and deal with the pre-release bugs.

---

### Post by frogotronic on 2007-03-01
Does fiesty hibernate and suspend with the nvidia/ati drivers?

---

