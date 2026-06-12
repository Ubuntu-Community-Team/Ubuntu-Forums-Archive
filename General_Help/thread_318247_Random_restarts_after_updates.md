---
title: "Random restarts after updates?"
date: 2006-12-13
forum: General Help
---

### Post by Cable on 2006-12-13
I installed the edgy kernel updates today, and since then my computer has randomly and suddenly restarted itself twice while I was using it.  I have no idea how to figure out *why* it restarted like this, but if anyone wants to help me figure it out, just ask for whatever you need in terms of posting information on here.

Is anyone else experiencing these restarts?

---

### Post by bodhi.zazen on 2006-12-13
I do not think I can help, but I will caution you.

The only time I had anything similar it was due to a hardware failure.

Now I am not saying you problem is hardware as I do not know, but I would advise you to back up your data just in case ;)

---

### Post by wpshooter on 2006-12-13
> **Cable said:**
> I installed the edgy kernel updates today, and since then my computer has randomly and suddenly restarted itself twice while I was using it.  I have no idea how to figure out *why* it restarted like this, but if anyone wants to help me figure it out, just ask for whatever you need in terms of posting information on here.

Is anyone else experiencing these restarts?

Why don't you go into the GRUB menu at boot and choose to boot to an eariler installed kernel and see if the restarts stop happening.  If they do stop, then you pretty much know that they are being caused by the latest kernel updates.

Good luck.

---

### Post by Cable on 2006-12-14
The updates seemed to be updates to the current kernel, not a new kernel.  I cannot choose a previous kernel as there is still only 1 choice.  Any other ideas?  Any logs or whatever I can post to give clues as to what could have happened?

---

### Post by bodhi.zazen on 2006-12-14
You can downgrade your kernel with synpatic.....

---

### Post by Cable on 2006-12-14
> **bodhi.zazen said:**
> You can downgrade your kernel with synpatic.....

I might just do that if no one is able to help me.  If I do decide to go that route, how would I do it?  I've never had to downgrade anything before.

---

### Post by bodhi.zazen on 2006-12-14
Open synpatic.

Search for kernel

You will see a list of kernels, one of which is installed.

Install a kernel with 1 number lower

Close synaptic and re-boot

On the boot menu you should have a choice, choose your new kernel.

If that fixes your problem, open synaptic and remove the newer kernel.

If not, boot to the newer kernel and use synaptic to remove the old one ....

Good luck, but I would venture a guess it is not the kernel ....
[indent]Of course I could be wrong on that guess as well[/indent]

---

