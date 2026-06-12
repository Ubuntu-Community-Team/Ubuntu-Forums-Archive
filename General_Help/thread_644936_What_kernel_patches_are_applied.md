---
title: "What kernel patches are applied?"
date: 2007-12-19
forum: General Help
---

### Post by gallatin_drew on 2007-12-19
How do I determine what patches were applied to an Ubuntu kernel vs a kernel.org kernel of the same version?   For example, I'm seeing what I think is a serious bug in the 2.6.20 Ubuntu kernel dealing with MSI-X interrupt vector updates which I don't see in the vanilla 2.6.20 kernel.  I can obviously diff the vanilla and ubuntu kernel sources, but this would be like looking for a needle in a haystack.  Is there a description of the changes somewhere, or a version control log or something?

Thank you,

Drew

---

### Post by psusi on 2007-12-19
You can check out the Ubuntu kernel git repository and check the logs, and bisect until you find the offending commit.

---

### Post by gallatin_drew on 2007-12-19
Thanks.. that was just the hint I needed.

Drew

---

### Post by gallatin_drew on 2007-12-19
Actually, I'm still confused.   The fiesty kernel version is 2.6.20.x, but it seems to contain at least some patches from 2.6.21, and there is no history in your git tree for them. 

I'm looking at kernel/irq/chip.c which differs from the 2.6.20 sources that I have. In the feisty kernel, default_disable() is just a stub (which is the source of the bug I'm chasing).  I looked at the git tree for fiesty, and it looks like default_disable() has always been a stub.  Eg, there are no changes for the file kernel/irq/chip.c mentioned at: [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-feisty.git;a=history;h=9849ab4f1243cb2e1da70cb2c12b05a0e6284c86;f=kernel/irq/chip.c](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-feisty.git;a=history;h=9849ab4f1243cb2e1da70cb2c12b05a0e6284c86;f=kernel/irq/chip.c)

From what I can see, the default_disable() function appears to have been stubbed out as part of this kernel.org change, which is listed in the changelog of kernel.org's  2.6.21:


commit 76d2160147f43f982dfe881404cfde9fd0a9da21
Author: Ingo Molnar <mingo@elte.hu>
Date:   Fri Feb 16 01:28:24 2007 -0800

    [PATCH] genirq: do not mask interrupts by default
    
    Never mask interrupts immediately upon request.  Disabling interrupts in
    high-performance codepaths is rare, and on the other hand this change could
    recover lost edges (or even other types of lost interrupts) by conservatively
    only masking interrupts after they happen.  (NOTE: with this change the
    highlevel irq-disable code still soft-disables this IRQ line - and if such an
    interrupt happens then the IRQ flow handler keeps the IRQ masked.)
    
    Mark i8529A controllers as 'never loses an edge'.
    
    Signed-off-by: Ingo Molnar <mingo@elte.hu>
    Cc: Thomas Gleixner <tglx@linutronix.de>
    Signed-off-by: Andrew Morton <akpm@linux-foundation.org>
    Signed-off-by: Linus Torvalds <torvalds@linux-foundation.org>


For the curious, the bug I'm chasing is that at least Feisty (and perhaps later Ubuntu kernels) will incorrectly update the affinity of MSI-X interrupt vectors without masking them first due to the above patchset.  This can potentially lead to crashes or data loss as MSI-X messages may be dma'ed to an incorrect location.

Drew

---

### Post by psusi on 2007-12-20
I'm confused... the Ubuntu kernel is based on 2.6.20, and you seem to be saying that the state of that file is unmodified from 2.6.20, but was changed in 2.6.21.  Well if it was changed after the version that the ubuntu kernel is based on, why is it unexpected that the version in the ubuntu repository is the same as 2.6.20?

---

### Post by gallatin_drew on 2007-12-20
> **psusi said:**
> I'm confused... the Ubuntu kernel is based on 2.6.20, and you seem to be saying that the state of that file is unmodified from 2.6.20, but was changed in 2.6.21.  Well if it was changed after the version that the ubuntu kernel is based on, why is it unexpected that the version in the ubuntu repository is the same as 2.6.20?

I'm saying that the supposedly 2.6.20.3 version of ubuntu's kernel has a patch from 2.6.21 applied.
But the git repository does not show any changes (like the application of a backported version of the patch from 2.6.21).  

Here is a diff between the kernel.org 2.6.20.3 and the ubuntu one for the file I'm interested in:
diff -pu linux-2.6.20.3/kernel/irq/chip.c linux-source-2.6.20/kernel/irq/chip.c
--- linux-2.6.20.3/kernel/irq/chip.c    2007-03-13 11:27:08.000000000 -0700
+++ linux-source-2.6.20/kernel/irq/chip.c       2007-04-12 10:16:23.000000000 -0700
@@ -202,10 +202,6 @@ static void default_enable(unsigned int 
  */
 static void default_disable(unsigned int irq)
 {
-       struct irq_desc *desc = irq_desc + irq;
-
-       if (!(desc->status & IRQ_DELAYED_DISABLE))
-               desc->chip->mask(irq);
 }
 
 /*
<.....>

The git repository for feisty shows the file *after* the patch is applied (eg, default_disable() is a stub), not as it appears in the kernel.org 2.6.20.3 kernel.  There is no history to explain how default_disable() became a stub in the ubuntu kernel. In fact, there are no changes to this file at all listed in the git repo.  

Am I just not using the git web interface right?   

It is sort of ironic.  Building ubuntu kernels from source is much easier than building RHEL or SLES kernels since they come pre-patched.  But at least the patches for RHEL and SLES
are obviously packaged, and it is easy to tell how a particular file gets changed.

Drew

---

### Post by psusi on 2007-12-20
Looks to me like the Ubuntu history shows commit f2bb4986 shows that patch being applied.  I suggest checking out the kernel.org and ubuntu.com repositories to a local repo and using the git tools directly to look it over.

---

### Post by gallatin_drew on 2007-12-21
> **psusi said:**
> Looks to me like the Ubuntu history shows commit f2bb4986 shows that patch being applied.  I suggest checking out the kernel.org and ubuntu.com repositories to a local repo and using the git tools directly to look it over.

Thanks for the commit id.  If I plug *that* into the git web interface, I can see the change.  The bizarre thing is that if you use the web interface's history link, it appears to always show no history for any file involved in that commit (or indeed, any file I checked at random).  At least for my purposes, this makes the git web interface close to useless.  At any rate, this is what is confusing me. 

Thanks for supplying the commit id,

Drew

---

### Post by geirha on 2007-12-21
Not sure how useful this information will be for your case, but in general you can get the vanilla source and the patches applied for ubuntu for a package using ```
apt-get source package
``` For example, for the edgy kernel: ```
apt-get source linux-image-2.6.17-12-generic
``` will download the files ```

linux-source-2.6.17_2.6.17.1.orig.tar.gz
linux-source-2.6.17_2.6.17.1-12.42.dsc
linux-source-2.6.17_2.6.17.1-12.42.diff.gz

``` which is the vanilla kernel source, signature file, and a file containing all patches applied, respectively.

And the command ```
aptitude changelog package
``` will display all changes done on that particular package.

---

