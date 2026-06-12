---
title: "Removing latest Kernel upgrade"
date: 2013-04-09
forum: General Help
---

### Post by kjbox on 2013-04-09
I have just upgraded from kernel 3.5.0-26-generic to 3.5.0-27-generic and WindowsXP in my VirtualBox wont open because the kernel driver is wrong. I ran '/etc/init.d/vboxdrv setup' as suggested but got a '"Permission Denied" error.

I have an excel file in there that has a very complex VBA macro that I am in the process of editing and has not been backed up for a few days and I cannot afford to lose the editing that I have done in that time.

I want to remove the kernel upgrade and revert to 3.5.0-26, then back up the excel file before sorting out the vboxdrv issue and then upgrading the kernel again.

I ran:
```

charles@charles-UX31E:~$ sudo apt-get --purge remove linux-image-3.5.0-27-generic
```

and got:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-generic* linux-generic-pae* linux-image-3.5.0-27-generic*
  linux-image-extra-3.5.0-27-generic* linux-image-generic*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 116 MB disk space will be freed.
Do you want to continue [Y/n]?
```

I just want confirmation that this will remove 3.5.0-27 and revert to 3.5.0-26 (which is still installed) before I answer Y 

TIA

---

### Post by sammiev on 2013-04-09
Why not select Advance Options on boot from the grub.

---

### Post by Paqman on 2013-04-09
> **kjbox said:**
> I have just upgraded from kernel 3.5.0-26-generic to 3.5.0-27-generic and WindowsXP in my VirtualBox wont open because the kernel driver is wrong. I ran '/etc/init.d/vboxdrv setup' as suggested but got a '"Permission Denied" error.

Try it again, prepending the command with sudo. You might also want to install the package [dkm]("apt:dkms")s, which should help with making future kernel upgrades go a bit more smoothly.

You don't need to remove the newer kernel, just boot into the older one from Grub.

---

### Post by ppjdee on 2013-04-09
> **sammiev said:**
> Why not select Advance Options on boot from the grub.

Agreed.

---

### Post by Ice On Fire on 2013-04-10
> **ppjdee said:**
> Agreed.

Just for education purposes - can you boot from multiple kernels through the advance menu?

---

### Post by ppjdee on 2013-04-10
No, one or the other.

---

### Post by kjbox on 2013-04-10
> **sammiev said:**
> Why not select Advance Options on boot from the grub.

Because I was having a senior moment!!!!!

---

### Post by mrJaros on 2013-04-12
kjbox, I've just ran your command and yes, it works nice. In my case, after latest upgrade, my pc won't start correctly (black screen after grub menu). I've choose advanced startup options and then my previous kernel and voila! It works like a charm. So I've decided to get rid of this crappy 3.5.0-27-generic kernel and rollback to my nice and warm 3.5.0-26-generic. I love it.

Anyway, thanks for useful command.

---

