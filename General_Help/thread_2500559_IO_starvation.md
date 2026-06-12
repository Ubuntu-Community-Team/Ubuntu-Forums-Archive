---
title: "IO starvation"
date: 2024-09-05
forum: General Help
---

### Post by wheeto86 on 2024-09-05
Hello,

I have a 22.04 machine booting from an SSD, with two "spinning rust" block devices setup with LVM to be a mirror. The LVM mirror contains the .qcow2 files for a couple of VMs which run under KVM.

All works fine, until I try to back up the boot disk to the mirrors which I'm doing by creating a LVM snapshot of the boot device, then DDing this snapshot to a file on the mirrors. During the dd operation, iotop shows that dd is copying across at about 110MB/s which is reasonable, but the VMs whose volumes are on the the same block device that dd is writing to get completely starved of IO and start throwing warnings and errors - see attached example.

Generally the guests become responsive again once the dd operation has finished, but a couple of times they've remained frozen even with no ongoing i/o.

I thought I could use ionice to kick off the dd task with a low i/o priority but as far as I can tell, and even though ionice is still included in the Ubuntu packages, there are no disk schedulers that actually pay attention to the ionice class. This is borne out by my experience where ```
ionice -c 3 dd ...
``` has no effect.

My question are 1) am I correct in thinking that Ubuntu, out of the box, doesn't allow ionice to work 2) what can I do to sort out my I/O prioritizing such that a dd task won't steal all the resource from my "spinning rust" devices?

Many thanks,

---

### Post by TheFu on 2024-09-05
I did a little reading and it seems ionice needs 2 options to actually work, not just 1.  Google found that easily.

Be certain your dd BS isn't too large or too small.  Think of it was leaving some time slices for other requests to be handled.

I've not seen the issue you are reporting, but I use LVM block storage for my VMs, not file-based VM storage.  Also, just in case this is happening, avoid USB-connected storage.  The USB storage drivers don't handle queuing well.

Have you tested the real storage performance using something like **fio**?

And when posting text, please post the text, not images.  Hard to select parts that standout for others.

---

### Post by wheeto86 on 2024-09-06
Thank you very much for your reply. In reverse order:

Sorry about the image, and understand entirely. I had to take a screenshot from virt-manager because the VM was too unresponsive to be able to log in to over SSH, and no extensions to enable clipboard were working.

I've now run some fio tests. Nothing I didn't expect: between 100MB/s and 200MB/s for sequential writes, and it suffers heavily on small random writes. Is there a particular test I could use to examine queueing behavior?

The disks are all attached to an internal SATA controller.

Would you recommend setting smaller block sizes to allow more time for other IO?

I have taken another look at the man and still can't see the second option. The scheduling class (-n) isn't required, or perhaps even valid, for -c3 and I don't need to pass a -p because I'm launching the process via the ionice binary. What have I missed?

Thanks agian,

---

