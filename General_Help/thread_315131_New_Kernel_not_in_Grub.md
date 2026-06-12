---
title: "New Kernel not in Grub"
date: 2006-12-08
forum: General Help
---

### Post by Sandman32 on 2006-12-08
Hi all,

I installed linux-k7 and then restarted my computer expecting to be able to boot into the new kernel.  However when grub popped up for ubuntu it still only had the generic kernel (well and the recovery mode).

So I went ahead and booted in with that.  I then ran sudo update-grub

That also only found the generic kernel.  I checked synaptic package manager, and the k7 kernel is installed...

Any ideas on how to get the k7 kernel to actually appear in grub?

Thanks!

---

### Post by bodhi.zazen on 2006-12-08
Other then adding it manually?

you can try:```
sudo grub
root (hdx,y)
setup (hd0)
```

This will re-install grub to your MBR.

Other then that, is the new kernel listed in /boot ?

---

### Post by azelter on 2006-12-08
I think you'll find all the other kernels are links to the generic one now. There is no such thing as k7 kernel anymore. It's just there for backward compatibility reasons and points to the generic kernel.

---

### Post by Sandman32 on 2006-12-08
Just checked and it is NOT listed in boot.  I don't know what to do about that though...

---

### Post by Sandman32 on 2006-12-08
> **azelter said:**
> I think you'll find all the other kernels are links to the generic one now. There is no such thing as k7 kernel anymore. It's just there for backward compatibility reasons and points to the generic kernel.

Hmm, I didn't know that.  So getting an honest to goodness k7 kernel will actually do nothing that the generic kernel doesn't already do?  Or shall I go in search of it a different way?  It definitely did download and install something though?

Edit:
So I looked in the folder it installed in, and it looks like all it installed was a changelog and a copyright for linux.  So I guess nevermind.  Thanks for your thoughts!  I'm not going to sweat it.

---

