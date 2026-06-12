---
title: "AMD Phenom bug. To patch or not to patch?"
date: 2008-02-29
forum: General Help
---

### Post by PreviousN on 2008-02-29
I recently purchased an AMD phenom 9500 and just found out there's a bug that cuts off quite a bit of performance. It's called the TLB bug and a kernel patch has been submitted by AMD. 

I'm not one for compiling my own kernel (I usually think it's a waste of my time), but I plan on doing some video encoding on my new rig (as well as run windows xp in virtualbox). I like to game, but usually just stick with open source ones like Urban Terror 4. 

_Do you think its worth it to try to compile my kernel with the bug patch?_ **Is there some sort of how-to on applying the patch?** *Would I benefit that much?*

About the bug:
[https://www.x86-64.org/pipermail/discuss/2007-December/010259.html](https://www.x86-64.org/pipermail/discuss/2007-December/010259.html)

About the patch:
[https://www.x86-64.org/pipermail/discuss/2007-December/010260.html](https://www.x86-64.org/pipermail/discuss/2007-December/010260.html)

---

### Post by astrotech226 on 2008-02-29
I would certainly give it a try.  Applying the patch is the easy part.  Here's the docs I use to compile my kernels on Ubuntu.  I have to add acl support to nfs on my servers so I do this all the time:

[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

As far as patching, after you download the kernel source, download the patch and put it in /usr/src/ and decompress it.  Change directory into the kernel source directory (something like /usr/src/linix-source-2.6.x).

Then, do a dry run on the patch to see if it's going to work.

patch -p1 --dry-run < ../<patchfile>

Your results may vary depending on how they built the patch file.  If everything goes well, remove the "--dry-run" part and let it rip.  Then follow the docs in the URL above to complete the compiling and installing the kernel.

---

### Post by PreviousN on 2008-02-29
They say this:

This patch is a workaround for AMD erratum 298. Due to the very invasive
nature of this patch and the very small number of affected customers
(you know it if you have an affected part), we do not recommend the use
of this patch on a regular Linux system. This patch is NOT intended for
mainline acceptance or inclusion with a Linux distribution!  The patch
has only received minimal functional testing. Every user must evaluate
it prior to production use to make sure it meets the necessary quality
standards. Like all GPL software, this patch comes with absolutely no
warranty.

Think it'll hurt my new hardware? I'd rather deal with performance hit than to see smoke.

---

### Post by Therion on 2008-02-29
I've been following this in the news myself and would suggest you give this patch some due consideration.  Installing the patch has some significant impact on overall performance.  Per Tech Report's benchmark testing:
> **Conclusions:**
So the BIOS-based workaround for the TLB erratum can have quite an effect on performance. How close were the estimates we've heard of a 10% performance drop? Let's summarize our results and consider the percentage differences.

Across every test we ran, the difference between the Phenom 9600 with and without the TLB patch averages out to 19.8%. However, if we rule out the synthetic memory tests and consider only the application tests, that difference drops to 13.9%.

The most troubling results here are the applications where we see large performance drops with the TLB erratum workaround active, including the Firefox web browser and the picCOLOR image analysis tool. If one happens to spend a lot of time running an application whose memory access patterns don't mix well with the TLB patch, the result could prove frustrating. The BIOS-based workaround for the TLB erratum may achieve its intended result—system stability—but it comes at a pretty steep price in terms of performance.
[The Whole Article](http://techreport.com/articles.x/13741/1) on Tech Report.

---

### Post by astrotech226 on 2008-02-29
> **PreviousN said:**
> They say this:
Think it'll hurt my new hardware? I'd rather deal with performance hit than to see smoke.

I don't think there's anything you could do that would damage the equipment.  I think their warning is to tell you to be vary aware of the fact that if you install the patch and put the machine into production, your server might lock up once a day and might lose data.

I'd give it a shot and run it in lab for a few weeks and to do some heavy testing.

The good part about this is that if the patch doesn't work out, simply change a line in your grub file and boot the old kernel.

---

### Post by PreviousN on 2008-02-29
Really appreciate the tips. I think you guys have given me the confidence to try it out. Thanks.

---

### Post by jmontelius on 2008-03-13
Well, this advice might be a bit late but I would say why bother. TheTLB bug will probably not show up unless you're doing extreme multithreading with high memory contention. I'm been running my Phenom for two months now and have not bothered to patch the bios nor the kernel.  It's more likely that I stumble on the power cord and halt then machine than it being struck by the TLB bug :)  (and I am working with high contention multithreading)

---

### Post by raptor3x on 2008-03-24
I'm having trouble applying the patch; when I try to apply it I get the following error:


[PHP]will@will-headless:~$ cd ./linux-source-2.6.22-2.6.22/
will@will-headless:~/linux-source-2.6.22-2.6.22$ ls
arch   COPYING  crypto  Documentation  fs       init  Kbuild  lib          Makefile  net     REPORTING-BUGS  security  tlb_patch
block  CREDITS  debian  drivers        include  ipc   kernel  MAINTAINERS  mm        README  scripts         sound     usr
will@will-headless:~/linux-source-2.6.22-2.6.22$ sudo patch -p1 --dry-run <./tlb_patch
patching file arch/x86_64/kernel/head.S
Hunk #1 succeeded at 91 (offset -4 lines).
patching file arch/x86_64/kernel/setup.c
Hunk #1 succeeded at 609 (offset -8 lines).
patching file arch/x86_64/mm/fault.c
Hunk #2 FAILED at 327.
Hunk #3 succeeded at 355 with fuzz 1 (offset 10 lines).
Hunk #4 succeeded at 364 with fuzz 2 (offset 10 lines).
1 out of 4 hunks FAILED -- saving rejects to file arch/x86_64/mm/fault.c.rej
patching file arch/x86_64/mm/init.c
patching file arch/x86_64/mm/ioremap.c
can't find file to patch at input line 198
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/arch/x86_64/vdso/vdso.lds.S b/arch/x86_64/vdso/vdso.lds.S
|index b9a60e6..4bf9720 100644
|--- a/arch/x86_64/vdso/vdso.lds.S
|+++ b/arch/x86_64/vdso/vdso.lds.S
--------------------------
File to patch:[/PHP]

Any ideas?

---

